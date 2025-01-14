---
title: "MySQL sampai Typesense: Full-Text Search Super Cepat di Laravel"
date: 2025-01-11
description: |
  Pencarian ada di mana-mana. Artikel ini membahas cara mengimplementasi fitur pencarian di Laravel dengan MySQL dan Typesense untuk membuat fitur pencarian yang super bagi pengguna.
tags: laravel, full-text-search, typesense, mysql
---

Pencarian ada di mana-mana, dari mencari SPBU, mencari tutorial di YouTube, atau mencari pesan lama disebuah chat. _in-app search_ memudahkan kita mencari apa yang kita mau.

Kali ini kita akan mengimplementasi fitur pencarian di Laravel. Bila pembaca ingin menambahkan fitur pencarian dan tidak tahu mulai dari mana, atau pembaca ingin meningkatkan fitur pencarian yang sudah ada, inilah artikel yang kalian butuhkan.

Kita akan mulai dari yang sederhana menggunakan query `LIKE` MySQL. Dilanjutkan dengan query yang lebih cepat dengan _full-text index_. Sebagai demo kita akan membuat sebuah component Livewire untuk melakukan _search-as-you-type_.

Dalam eksplorasi, kita akan menemui batas kemampuan MySQL dalam menangani skenario pencarian. Keterbatasan ini akan kita atas dengan menggunakan **Typesense**, sebuah search engine open source yang menawarkan solusi atas kesulitan yang kita hadapi. Kita akan menggunakannya lewat Laravel Scout yang telah menyediakan _driver_ resmi untuk mengawinkan Laravel dengan Typesense.

Siap? Mari kita mulai!

## Menyiapkan Project dengan 2 Juta Baris Data

Bayangkan aplikasi _customer support_ dimana seorang anggaplah _customer service_ perlu mencari akun berdasarkan nama, email atau alamat. Hasil pencarian sangat krusial untuk menjawab email ataupun telepon pelanggan. Sebagai aplikasi contoh, mari buat project baru dan kita beri nama StarSupport:

```bash
$ composer create-project laravel/laravel starsupport

# Atau dengan Laravel Installer:
$ laravel new starsupport
```

Ikuti proses pembuatan project baru yang muncul. Kita tidak akan menggunakan _starter kit_, jadi pilih “No starter kit” bila pilihan tersebut muncul. Selanjutnya pilih MySQL esbagai database dan atur file `env` sesuai dengan detail koneksinya.

Sekarang, mari buat model `Customer` berikut dengan migrasi, factory serta sebuah seeder:

```bash
$ php artisan make:model Customer --migration --factory --seed
```

Perintah di atas akan membuat empat file:

- app/Models/Customer.php
- database/migrations/2024_06_20_135645_create_customers_table.php
- database/factories/CustomerFactory.php
- database/seeders/CustomerSeeder.php

Mari ubah konten keempat file tersebut, dimulai dengan migrasinya:

```php
$table->id();
$table->string('name');
$table->string('email')->unique();
$table->string('account_number')->unique();
$table->string('address');
$table->string('country');
$table->string('phone');
$table->timestamps();
```

Kita perlu sebuah cara untuk mengisi database dengan data palsu, jadi mari kita siapkan sebuah factory:

```php
'name' => fake()->firstName() . ' ' . fake()->lastName(),
'email' => fake()->unique()->safeEmail(),
'account_number' => fake()->unique()->randomNumber(8, true),
'address' => fake()->address(),
'country' => fake()->country(),
'phone' => fake()->phoneNumber(),
```

Sempurna. Berikutnya kita akan gunakan factory tersebut di `CustomerSeeder`. Kita akan membutuhkan data yang sangat banyak untuk menguji fitur pencarian yang akan dibuat, jadi buatlah sebanyak dua juta data dibagi dalam 100rb kelompok data agar proses pembuatannya lebih cepat.

```php
public function run(): void
{
    $total = 2_000_000;
    $chunkSize = 100_000;

    for ($i = 0; $i < $total; $i += $chunkSize) {
        Customer::factory()->count($chunkSize)->create();
    }
}
```

Jangan lupa memanggil seeder tersebut di `DatabaseSeeder`:

```php
public function run(): void
{
    User::factory()->create([
        'name' => 'Test User',
        'email' => 'test@example.com',
    ]);

    $this->call(CustomerSeeder::class);
}
```

Terakhir, kita ingin membuat semua field di model Customer bisa diisi (fillable). Kita bisa melakukannya dengan menulis semua kolom di `$fillable` atau menulis array kosong untuk field `$guarded`:

```php
protected $guarded = [];
```

Terakhir, mulai proses seeding database-nya:

```bash
php artisan migrate:fresh --seed
```

## Langkah Pertama: Menggunakan Query LIKE

Tujuan kita adalah membuat fitur pencarian berdasarkan nama, email atau alamat. Pengguna bisa menulis kata kunci disebuah input field di frontend, lalu request tersbut dikirim ke backend.

Backend akan menerima request tersebut dan melakukan query `SELECT` menggunakan operator `LIKE`. Sebagai contoh, bila kata kuncinya “john”, maka query-nya akan terlihat sebagai berikut:

```sql
SELECT
    *
FROM
    customers
WHERE
    `name` LIKE '%john%'
    OR `email` LIKE '%john%'
    OR `address` LIKE '%john%';
```

Query tersebut dalam diimplementasi sebagai sebuah scope di model Customer:

```php
public function scopeSearch(Builder $query, string $keyword): Builder
{
    return $query->where('name', 'LIKE', "%{$keyword}%")
        ->orWhere('email', 'LIKE', "%{$keyword}%")
        ->orWhere('address', 'LIKE', "%{$keyword}%");
}
```

..dan menggunakannya dengan cara:

```php
Customer::search('john')->get();
```

Next, mari kita lakukan _benchmark_ atas performa query yang baru saja dibahas. Meskipun ada beberapa cara (misalnya dengan `EXPLAIN ANALYZE` di MySQL atau melakukan log execution time di PHP menggunakan `microtime`), kita akan memanfaatkan Benchmark helper bawaan Laravel.

Jika pembaca tidak familiar, jangan risau karena pemakaiannya sangat mudah. Fitur ini menerima sebuah callback, menjalankannya lalu akan memberikan waktu eksekusinya dalam milidetik. Buka Tinker dengan `php artisan tinker`, lalu jalankan peirntah berikut:

```php
use App\Models\Customer;
use Illuminate\Support\Benchmark;
Benchmark::dd(fn () => Customer::search('john')->get());
```

Pembaca akan mendapatkan hasil kurang lebih sebagai berikut:

```
"3,274.718ms"
```

Benchmark cukup keren kan? Yang tidak keren dari hasil di atas adalah waktu yang lama, butuh lebih dari tiga detik untuk menjalankan pencarian. Durasi tersebut bisa bervariasi tergantung server, tapi pada akhirnya tetap tidak sekencanga yang kita mau.

Mari kita coba lagi. Dengan Benchmark, kita bisa menjalankan suatu query beberapa kali dan mendapat waktu rata-rata. Mari kita coba sepuluh iterasi. Kita bisa menggunakan kata kunci yang sama untuk konsistensi atau mencari dengan kata kunci yang random:

```php
use App\Models\Customer;
use Illuminate\Support\Benchmark;
Benchmark::dd(fn () => Customer::search(Str::random(4))->get(), iterations: 10);
```

Ok, sekarang kita mendapat angka yang lebih representatif:

```
"3,039.130ms"
```

Artinya bila kita melakukan 10 kali pencarian, rata-ratanya adalah 3 detik.

Menunggu tiga detik sampai hasil pencarian muncul itu…. kurang bagus. Menunggu tiga detik lagi saat melakukan pencarian kedua (misalnya, mengubah kata kunci dari john ke johnson) akan menguji kesabaran pengguna.

Jadi, apa yang bisa kita lakukan untuk mengatasinya?

## Pencarian yang Lebih Efisien dengan MySQL Full-Text Index

Sejak versi 5.6 (rilis tahun 2013), MySQL mendukung fitur _full-text index_. Meskipun index unggul dalam pencarian dengan kata kunci yang utuh, mereka tidak optimal untuk melakukan pencarian di dalam konten teks. Mencari kata kunci atau frasa yang spesifik di dalam suatu teks yang lebih besar merupakan keunggulan utama _full-text index_. Teknik ini ideal bagi aplikasi yang konten utamanya adalah teks seperti artikel, deskripsi produk atau konten yang dibuat oleh pengguna (user generated content).

Saat membuat full-text index, MySQL akan memecah teks menjadi kata per kata lalu membangun index untuk kata-kata tersebut, mirip seperti indeks yang sering ada di belakang suatu buku. Pendekatan ini memungkinkan MySQL untuk dapat mencari data yang mengandung kata kunci spesifik tanpa harus membaca keseluruhan tabel. Bahkan, MySQL mampu mengurutkan hasil berdasarkan relevansi untuk memastikan kita mendapat hasil yang lebih cocok.

Kita dapat membuat full-text index pada kolom `CHAR`, `VARCHAR`, atau `TEXT`. Kita bahkan dapat membuat satu index untuk beberapa kolom sekaligus. Karena kita akan mencari data dalam tiga kolom, maka akan lebih baik bila membuat satu index yang menggabungkan ketiganya.

Mari buat sebauh migrasi baru dengan `php artisan make:migration` untuk menambahkan full-text index ke tabel customers:

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::table('customers', function (Blueprint $table) {
            $table->fullText(['name', 'email', 'address']);
        });
    }

    public function down(): void
    {
        Schema::table('customers', function (Blueprint $table) {
            $table->dropFullText(['name', 'email', 'address']);
        });
    }
};
```

Jalankan dengan `php artisan migrate`. Jika pembaca melihat struktur tabel, maka sekarang akan ada sebuah index baru bertipe `FULLTEXT` dengan nama `customers_name_email_address_fulltext`.

Untuk memanfaatkan full-text search di pencarian, kita harus memperbarui search scope untuk mengganti `where` dengan `whereFullText`.

```php
public function scopeSearch(Builder $query, string $keyword): Builder
{
    return $query->whereFullText(['name', 'email', 'address'], $keyword);
}
```

Mari kita coba dengan menajalankan perintah berikut di Tinker:

```php
Customer::search('john')->get();
```

Lebih cepat kan? Perintah tersebut akan mengubah query SQL-nya menjadi:

```sql
SELECT * FROM `customers`
WHERE MATCH (`name`, `email`, `address`)
AGAINST ('tom' IN NATURAL LANGUAGE MODE);
```

Mari kita ukur _impact_ dari implementasi _full-text index_ dengan menjalankan benchmark yang sebelumnya kita lakukan:

```php
use App\Models\Customer;
use Illuminate\Support\Benchmark;
Benchmark::dd(fn () => Customer::search(Str::random(4))->get(), iterations: 10);
```

Hasilnya adalah…..

```
"3.148ms"
```

Wow! Hanya 3 milidetik dari yang sebelumnya 3 detik lebih. Artinya pencarian kita menjadi 1000 kali lebih cepat.

Kebetulan saja? Mungkin!

Benchmark akan membantu memastikannya, dari 10x pencarian akan kita lakuakn 1000x.

```
Benchmark::dd(fn () => Customer::search(Str::random(4))->get(), iterations: 1000);
```

Angkanya mungkin bisa berbeda-beda, tapi dari hasil yang penulis dapatkan `2.974ms`. Berapa nilai yang pembaca dapat? Penulis pastikan akan jauh lebih rendah dari teknik sebelumnya. Pencapaian ini perlu dirayakan, tapi mari kita periksa beberapa hal.

Kita jalankan sebuah eksperimen. Ambil tiga customer lalu ubah namanya. Dua data harus bernama Tom dan sisanya bernama Tommy. Contoh:

```sql
UPDATE `customers` SET `name` = 'Tom Brown' WHERE `id` = 99;
UPDATE `customers` SET `name` = 'Tom Martinez' WHERE `id` = 134;
UPDATE `customers` SET `name` = 'Tommy Jones' WHERE `id` = 328;
```

Sekarang mari kita coba:

```php
Customer::search('tom')->get();
```

Dan…. tidak ada hasil. Aneh bukan? Bila kita mencari “john” kita mendapat hasil tapi nihil bila kata kuncinya “tom” padahal ada beberapa customer bernama Tom di tabel database kita. Jangan kaget, kejadian ini sebetulnya bukan bug, karena minimal panjang karakter untuk melakukan pencarian di MySQL adalah 4. Angka ini bisa disesuaikan dengan mengubah konfigurasi MySQL biasanya di `/etc/mysql/my.cnf`. Tambahkan baris berikut:

```
[mysqld]
ft_min_word_len=3
```

Simpan lalu restart server MySQL. Setelah melakukan perubahan ini, kita perlu menghapus dan membuat ulang full-text index sebelumnya yang bisa dilakukan dengan rollback dan migrasi kembali.

```bash
php artisan migrate:rollback && php artisan migrate
```

Sekarang kita coba lagi:

```php
Customer::search('tom')->get();
```

Kali ini kita seharusnya akan mendapat beberapa data bernama Tom, tapi ternyata kata kunci “tom” tidak memberikan data si Tommy.

```php
> App\Models\Customer::search('tom')->get()->pluck('id')->contains(328);
= false
```

Kenapa? Karena fitur full-text search MySQL tidak secara otomatis mengikutsertakan suffix maupun prefix. Ia hanya akan mencari sesuai kata kunci. Mencari kata “boo” tidak akan secara otomatis mendapatkan hasil “book” atau “boost”. Terkadang memang itulah yang diperlukan, hasil yang persis sesuai dengan kata kunci. Namun, pada kasus yang kita hadapi sekarang pencarian parsial juga akan lebih ideal.

Untuk mencapai tujuan tersebut kita akan menggunakan **boolean mode**. Dengan mode ini, kita dapat menggunakan beberapa karakter khusus baik di depan maupun di belakang sebuah string. Contoh, operator `*` artinya keyword `tom*` akan mencari semua kata berawalan “tom”.

```sql
SELECT * FROM `customers`
WHERE MATCH(`name`, `email`, `address`)
AGAINST ('tom*' IN boolean mode);
```

Kita bisa memperbarui scope agar menggunakan query di atas dengan menambahkan bintang diakhir keyword dan menggunakna boolean mode:

```php
public function scopeSearch(Builder $query, string $keyword): Builder
{
    return $query->whereFullText(
        ['name', 'email', 'address'],
        "$keyword*",
        ['mode' => 'boolean'],
    );
}
```

Sekarang kita bisa mencari Tommy:

```php
> App\Models\Customer::search('tom')->get()->pluck('id')->contains(328);
= true
```

Sip! Fungsi pencarian yang kita buat sudah bisa mencari kata kunci parsial. Namun, perubahan yang sudah dilakukan hanya akan memberikan hasil yang diawali oleh kata kunci tertentu (misalnya **Tom**my”) dan tidak akan memberikan hasil yang diakhiri oleh kata kunci (misalnya “A**tom**“). Topik ini akan kita bahas nanti.

Terakhir, kita perlu ingat untuk memberikan batas hasil pencarian. Memanggil `get` dapat menghasilkan ribuan data. Oleh karena itu kita bisa tentukan misalnya hanya mengambil 20 data teratas:

```php
Customer::search($this->keyword)->take(20)->get();
```

Oke, sekarang kita bisa melanjutkan di bagian frontend.

## Membangun Livewire Search Component

Meskipun mengembangkan frontend pencarian bukan fokus dari artike lini, melihat hasil pencarian secara visual akan memberikan gambaran yang lebih bagus.

Mari kita mulai dengan memasang Livewire lewat Composer:

```bash
composer require livewire/livewire
```

Langkah di atas bisa dilewatkan bila project sudah menggunakan Livewire (contohnya jika sudah memasang Laravel Breeze dengan opsi Livewire with Alpine). Berikutnya, buat search component dengan perintah:

```bash
php artisan make:livewire customer-search
```

Perintah di atas akan menghasilkan dua file yaitu:

- app/Livewire/CustomerSearch.php
- resources/views/livewire/customer-search.blade.php

Kita akan membutuhkan properti `$keyword` untuk menyimpan kata kunci pencarian dengan `$customers` tempat menyimpan hasil pencarin tersebut. Kita bisa membuatnya sebagai properti public di class Livewire agar bisa diakses dari view.

Selnjutnya, kita perlu membuat sebuah fungsi `search()`. Hasil akhir component tersebut akan adalah sebagai berikut:

```php
<?php

namespace App\Livewire;

use Livewire\Component;
use App\Models\Customer;
use Illuminate\Support\Collection;

class CustomerSearch extends Component
{
    public string $keyword = '';

    public Collection $customers;

    public function search()
    {
        $this->customers = strlen($this->keyword) > 2
            ? Customer::search($this->keyword)->take(20)->get()
            : collect([]);
    }

    public function render()
    {
        return view('livewire.customer-search');
    }
}
```

Sempurn~ Mari kita lanjutkan ke view. Apa yang kita butuhkan? Hanya dua hal:

- Sebuah `<input>` tempat pengguna memasukkan kata kunci.
- Sebuah `<ul>` untuk menampilkan daftar hasil pencarian. Elemen ini hanya ditampilkan bila pencarian memberikan hasil, apabila kosong maka tampilkan pesan “No maches found”.

Template view Livewire tersebut dapat terlihat sebagai berikut:

```html
<div class="customer-search">
    <input
        wire:model="keyword"
        wire:keyup.debounce="search"
        autofocus
        placeholder="Search" />
    @if ($keyword)
        <ul>
            @forelse ($customers as $customer)
                <li>
                    <div>{{ $customer['name'] }}</div>
                    <div>{{ $customer['email'] }}</div>
                    <div>{{ $customer['address'] }}</div>
                </li>
            @empty
                <li>
                    No matches found
                </li>
            @endforelse
        </ul>
    @endif
</div>
```

Perintah `wire:model="keyword"` menghubungkan nilali yang ditulis dengan properti `$keyword` di component kita, memastikan isi `$keyword` akan selalu sama dengan apa yang ditulis pengguna.

Kita menggunakan `wire:keyup="search"` agar setiap kali pengguna menekan suatu tombol kita ingin memulai pencarian. Untuk mencegah server menerima spam request setiap kali user mengetikkan sesuatu, maka kita tambahkan pengaturan `wire:keyup.debounce="search"`. Kode tersebut akan memberitahu Livewire untuk menunggu, biasanya 250ms setelah user mengetikkan sesuatu sebelum mengirimkan request pencarian. Hasilnya bila user mengetikkan “john” dengan cepat, kita hanya akan mengirim satu request saja, bukan empat.

Semua sudah siap, sekarang kita tinggal menambahkan `<livewire:customer-search />` ke view Blade. Sebagai contoh kita tambahkan saja di dalam `welcome.blade.php`:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Customers</title>
        @vite(['resources/css/app.css', 'resources/js/app.js'])
    </head>
    <body>
        <livewire:customer-search />
    </body>
</html>
```

Mari kita jalankan `php artisan serve` dan buka di browser. Tuliskan kata kunci yang diinginkan, misalnya “ross”:

![](/assets/images/posts/fulltext-search-ross.png)

Kita akan mendapat hasil customer dengan nama, email atau alamat yang sesuai dengan kata kunci. Mari kita coba lagi dengan kata kunci lain “rossie”:

![](/assets/images/posts/fulltext-search-rossie.png)

Hasil yang didapatkan pembaca mungkin akan berbeda karena isi database sesuai dengan apa yang disi oleh Faker. Tapi yang penting kita mendapat hasil yang sesuai dengan apa yang dimau.

## Menambahkan Keyword Highlight

Akan lebih cantik bila kita bisa memberikan highlight kata kunci pada detail customer dengan tag `<mark>`. Contoh, bila kata kuncinya “john”:

```html
<li>
    <div><mark>John</mark> Doe</div>
    <div><mark>john</mark>@gmail.com</div>
    <div>123 Main St., FL</div>
</li>
```

Ada banyak cara untuk mencapainya. Cara yang cukup sederhana ialah dengan menggunakan properti `computed` milik Livewire. Tambahkan kode berikut di dalam kelas Livewire kita:

```php
use Livewire\Attributes\Computed;
```

Lalu tambahkan method berikut:

```php
#[Computed]
public function highlightedCustomers()
{
    $fields = ['name', 'email', 'address'];
    $highlight = fn ($value) => preg_replace("/({$this->keyword})/i",'<mark>$1</mark>',$value);

    return $this->customers
        ->map(fn ($customer) => array_map($highlight, $customer->only($fields)));
}
```

Sekarang di view kita ganti `$customers` dengan `$this->highlightedCustomers`.

```php
@forelse ($this->highlightedCustomers as $customer)
    <li>
        <div>{!! $customer['name'] !!}</div>
        <div>{!! $customer['email'] !!}</div>
        <div>{!! $customer['address'] !!}</div>
    </li>
@empty
    <li>
        No matches found
    </li>
@endforelse
```

Kita gunakan `{!! !!} untuk mencetak tag`mark`. Teknik ini cukup untuk aplikasi contoh seperti tutorial ini, tapi di production berhati-hati akan XSS attack.

![](/assets/images/posts/fulltext-search-mark.png)

Dengan [sedikit css](https://github.com/nicodevs/demo-search/blob/main/resources/css/app.css), komponen search kita terlihat seperti ini:

![](/assets/images/posts/fulltext-search-css.png)

## Batasan Full-Text Search di MySQL

### Tidak boleh typo

Mari kita cari customer bernama John!

![](/assets/images/posts/fulltext-search-no-match.png)

Kok tidak ada? Nah, karena ada typo di kata kuncinya, “jhon” yang seharusnya “john”, MySQL tidak memberikan hasil yang diharapkan.

### Tidak bisa mencari suffix dan infix

Pada contoh sebelumnya kita sudah menggunakan boolean mode sehingga dapat mencari data yang dimulai oleh kata kunci tapi tidak dengan yang diakhiri atau kata kunci yang berada di tengah suatu kata.

### Belum mampu mengimplementasi “weighted result”

Mari coba customer bernama “markus”:

![](/assets/images/posts/fulltext-search-markus.png)

Seperti yang pembaca lihat, dua hasil pertama merupakan hasil dengan data alamat yang sesuai, sementara dua hasil di bawahnya dengan data nama yang sesuai. Bagiamana bila kita ingin memprioritaskan nama diikuti email dan terakhir alamat? Strategi untuk menentukan nilai-nilai yang berbeda untuk tiap kolom disebut dengan _weighted result_. Kita bisa melakukannya di MySQL, tapi query yang dibutuhkan akan semakin kompleks (lihat contohnya [di sini](https://github.com/nicodevs/demo-search/blob/main/examples.md))

### Sulit Melakukan Pengecualian

Di backend kita mengatur agar pencarian dilakukan di tiga kolom yaitu name, email dan address. Bagaimana bila user hanya ingin mencari berdasarkan satu kolom saja? Untuk saat ini hal tersebut belum bisa dilakukan karena pengecualian akan membutuhkan logic yang lebih kompleks lagi dengan kombinasi indeks (nama dan email saja atau nama saja atau nama dan alamat saja) tapi dapat menaikkan ukuran database.

Kesimpulannya, fitur full-text search di MySQL sudah sangat bagus, tapi masih ada kekurangannya. Berikutnya akan kita lihat bagiamana melakukan pencarian dengan _experience_ yang lebih baik dengan Typesense.

## Typesense: Open Source Search Engine Super Cepat

[Typesense](https://typesense.org/) menawarkan solusi search engine yang powerful sebagai alterantif yang gratis dari layanan seperti Algolia. Library ini [open-source](https://github.com/typesense/typesense) dan mudah disiapkan di server sendiri. Beberpa fitur yang dimilikinya:

- Toleransi typo yang bisa di atur: Mampu mencari data meskipun dengan kata kunci yang salah ketik.
- Mendukung prefix, suffix dan infix: Mencari kata yang diawali, diakhiri atau mengandung kata kunci.
- Mengatur prioritas hasil berdasarkan ranking dan relevansi: Hasil pencarian dapat diprioritaskan berdasarkan frekuensi kata kunci, field yang mengandung kata kunci atau dapat dengan mengatur sendiri prioritas yang diinginkan.
- Parameter yang fleksibel: Index data menggunakan gabungan beberapa kolom (seperti name, email dan address). Dengan demikian bisa menargetkan pencarian secara spesifik hanya di field tertentu (misalnya hanya mencari di kolom name).

![](/assets/images/posts/fulltext-search-typesense-1024x502.png)

Fitur-fitur diatas telah mengatasi keterbatasan yang kita temui dengan MySQL. Meskipun begitu, Typesense masih punya banyak fitur lain seperti:

- Geo-Search untuk mencari lokasi berdasarkan radius.
- Image search untuk mencari gambar yang spesifik (misalnya “all images containing dogs”).
- AI-powered conversational search, bisa menjawab pertanyaan berdasarkan data yang kita miliki (misalnya ada pertanyaan “Can you suggest an action movie?”).

Siap? Mari kita mulai dengan memasang dan mengintegrasikan Typesense ke project yang kita miliki hanya dengan tiga langkah.

## Langkah 1: Install Typesense dan Laravel Scout

Pembaca bisa baca cara [memasang Typsense](https://typesense.org/docs/guide/install-typesense.html) di dokumentasi mereka.

Bila menggunakan Takeout, Docker container manager milik Tighten, Typesense bisa dipasang dengan menjalankan `takeout enable typesense`. PIlih volume name Docker, atur API key dan bisa melewati langkah di bawah.

Bila menggunakan server sendiri, ikuti langkah di bawah untuk memasang Typsense di Linux yang kemungkinan besar menjadi sistem operasi di server.

```
curl -O https://dl.typesense.org/releases/26.0/typesense-server-26.0-amd64.deb
sudo apt install ./typesense-server-26.0-amd64.deb
```

Setelah terpasang, Typesense membuat sebuah API key yang perlu kita salin. Jalankan:

```
cat /etc/typesense/typesense-server.ini
```

Lalu salin API key yang ada di dalamnya. Contoh:

```
api-key = BIO2PGT4B3xpauGBpkIX4p8jAHltKBlxEY5VD3EKFtTZP6jq
```

## Langkah 2: Install Package dan Perbarui Config

Tambahkan kedua baris berikut di dalam file `.env` Laravel, pastikan API key sesuai dengan yang di salin:

```
SCOUT_DRIVER=typesense
TYPESENSE_API_KEY=BIO2PGT4B3xpauGBpkIX4p8jAHltKBlxEY5VD3EKFtTZP6jq
```

Lalu, gunakan composer untuk memasang Typesene PHP SDK dan Laravel Scout, librar yang menambahkan fitur pencarian ke model Eloquent.

```
composer require typesense/typesense-php laravel/scout
```

Berikutnya jalankan perintah artisan:

```
php artisan vendor:publish --provider="Laravel\Scout\ScoutServiceProvider"
```

Perintah di atas akan menambahkan file `scout.php` di folder `config`. Fuka file tersebut di editor dan tambahkan `use App\Models\Customer;` di bagian atas. Lalu scroll kebawah sampai menmeukan “Typesense Configuration”. Hapus kode yang dikokmentari di `model-settings` lalu ganti dengan pengaturan berikut:

```
'model-settings' => [
    Customer::class => [
        'collection-schema' => [
            'fields' => [
                ['name' => 'id', 'type' => 'string'],
                ['name' => 'name', 'type' => 'string'],
                ['name' => 'email', 'type' => 'string'],
                ['name' => 'address', 'type' => 'string'],
            ],
        ],
        'search-parameters' => [
            'query_by' => 'name,email,address',
        ],
    ],
],
```

Pada konfigurasi di atas kita mengatur:

- Daftar field yang ingin di index di dalam `collection-schema`. Pastikan untuk menambahkan id sebagai string karenag Typesense menggunakan string ID.
- Menentukan parameter awal untuk `search-parameter`yang menandakan kita ingin melakukan query berdasarkan name, email dan address. Urutannya sangat penting karena Typesene akan memprioritaskan hasil yang sesuai dengan field pertama, lalu kedua dan seterusnya.

## Langkah 3: Update Model

Buk model Customer lalu:

- Tambahkan `Searchable` trait.
- Hapus search scope karena sudah tidak dipakai.
- Tambahkan method `toSearchableArray`. Method ini harus me-return associative array dengan indexable fields. Ingat bahwa primary key ID harus di cast sebagai sebuah string.

```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Laravel\Scout\Searchable;

class Customer extends Model
{
    use HasFactory;
    use Searchable;

    protected $guarded = [];

    public function toSearchableArray()
    {
        return ['id' => (string) $this->id] + $this->toArray();
    }
}
```

## Langkah 4: Menambahkan Customer ke Index Typesense

Karena kita sudah memiliki data yang ingin dicari, kita perlu menambahkan data tersebut ke index milik Typesense. Kita bisa melakukannya dengan mudah lewat perintah import dari Laravel Scout:

```
php artisan scout:import "App\Models\Customer"
```

Kita akan melihat progress-nya di terminal:

```
Imported [App\Models\Customer] models up to ID: 500
Imported [App\Models\Customer] models up to ID: 1000
Imported [App\Models\Customer] models up to ID: 1500
```

Proses akan terus berjalan sampai semua data di import.

Setelah proses import yang pertama, Typesense secara otomatis akan membuat index baru atau memperbarui data Customer ketika memanggil method `create()` atau `save(0)`.

Perlu diketahui ada beberapa method yang tidak memanggil event Typesense misalnya [mass update](https://laravel.com/docs/11.x/eloquent#mass-updates), sehingga index tidak diperbarui secara otomatis. Dalam kasus seperti itu, kita perlu melakukan index secara manual.

## Mencoba Typsense

Setelah semua selesai! Mari kita lakukan pencarian di model Customer menggunakan method `search` dari Laravel Scout.

```
Customer::search('john')->take(20)->get();
```

Kode yang dipakai masih sama dengan sebelumnya sehingga component Livewire yang kita miliki tidak membutuhkan update apapun. Mari lihat hasilnya di browser:

![](/assets/images/posts/fulltext-search-typo-tolerance.png)

Kita bisa menemukan John meskipun melakukan typo “jhon”.

Mari coba lagi dengan keyword “son”:

![](/assets/images/posts/fulltext-search-prefix-suffix.png)

Kita mendapatkan hasil yang mengandung kata son di awal, akhir maupun di tengah alias prefix suffix dan infix support.

Mari coba dua kata kunci:

![](/assets/images/posts/fulltext-search-weigthed-results.png)

Perhatian bagaimana hasil diurutkan berdasarkan relevansi menggunakan urutan kolom yang kita tuliskan di `query_by` sebelumnya: name, email dan address. Pada contoh ini, mencari “Jesse Hills” akan mencari yang namanya sama terlebih dahulu diikuti alamat yang sama persis, baru diikuti oleh nama atau alamat yang mengandung salah satu kata kunci.

Selain itu kita bisa menimpa parameter awal dengan method `options`. Contohnya kita bisa mengatur hasil pencarian hanya dari field `name`:

```
Customer::search($this->keyword)->options(['query_by' => 'name'])->take(20)->get();
```

Atau memungkinkan pengguna untuk memilih kolom mana yang ingin dicari:

```
<input type="checkbox" value="name" wire:model="fields">
<input type="checkbox" value="email" wire:model="fields">
<input type="checkbox" value="address" wire:model="fields">
```

Sehingga hasil pencarian bisa lebih dinamis berdasarkan pilihan checkbox `options(['query_by' => $this->fields])`.

## Kecepatan Nomor Satu

Semua kebutuhan yang kita cari sudah teratasi, sekarang komponen pencarian kita sudah berfungsi dengan lengkap berkat Typesense.

Jangan lupa untuk diakhiri dengan melakukan benchmark. Typesense menawarkan semua fitur yang keren, tapi apakah hasilnya cepat?

```
Benchmark::dd(fn () => Customer::search(Str::random(4))->get(), iterations: 1000);
```

Hasilnya adalah:

```
"5.192ms"
```

Bukan hanya cepat, tapi super cepat! Dengan arata rata pencarian 5 milidetik dalam 1000x iterasi, Typesense membuktikan bahwa ia mampu menawarkan fitur yang lengkap dan kencang.

## Kesimpulan

Dengan mengintegrasikan Typsense kita dapat meningkatkan hasil pencarian tanpa mengorbankan performa. Solusi open-source ini menawarkan fleksibilitas dan kecepatan yang dibutuhkan aplikasi web modern sehingga menjadi pilihan terbaik bagi project Laravel.

Tapi apa yang kita pelajari hanya sedikit dari apa yang mampu dilakukan oleh Typesense. Kami sarankan untuk mencoba fitur lain yang lebih canggih seperti geosearch dan AI-powered conversational search. Memberikan fitur pencarian yang canggih mampu membedakan aplikasi biasa dengan aplikasi yang luar biasa.

Bila Typesense tidak sesuai dengan kebutuhan, coba gunakan database enigne Laravel Scout. Opsi ini memanfaatkan MySQL full-text index sehingga menawarkan solusi lain.

Diterjemahkan dari [Tighten](https://tighten.com/insights/blazing-fast-full-text-search-in-laravel-from-mysql-to-typesense/?utm_source=newsletter&utm_medium=email&utm_campaign=freekdev-newsletter-178) oleh [Nico Devs](https://tighten.com/authors/nico-devs/).
