---
title: "Variabel & Tipe Data di Pemrograman Dart"
date: 2025-01-03
description: "Kali ini kita  akan membahas bagaimana mendefinisikan suatu variabel dan jenis-jenis tipe data yang ada dalam bahasa pemrograman Dart."
series: dart
series_title: "Variabel & Tipe Data di Pemrograman Dart"
---

{% include series.liquid %}

Bab ini akan membahas bagaimana mendefinisikan suatu variabel dan jenis-jenis tipe data yang ada dalam bahasa pemrograman Dart. Pembaca yang sudah pernah belajar bahasa pemrograman lain seperti Java, Kotlin, atau Swift mungkin akan sedikit familiar dengan tipe data yang ada di Dart. 

Berikut beberapa poin yang akan kita bahas di bab ini:

- Variabel
- Constant
- Number
- String
- Boolean
- _Type Inference_
- _Late Variable_
- _Constant_
- List
- Set
- Map

## Variabel

Dalam suatu program kita akan bekerja dengan banyak jenis data. Terkadang data tersebut berupa angka seperti umur, uang, jarak, terkadang juga berupa teks seperti nama, alamat, dan lain sebagainya. 

Agar bisa mengelola banyak data, kita memerlukan suatu cara untuk menampung data tersebut. Perhatikan kode berikut:

```dart
int age = 17;
```

Pada contoh di atas kita membuat sebuah variabel bernama `age` yang menampung data beruba angka bernilai 17. Karena angka 17 merupakan integer, maka kita perlu menggunakan tipe data `int` yang ditulis sebelum nama variabel yang diinginkan.  

Suatu variabel bisa dipanggil lagi untuk mengambil data yang ia tampung dari tempat yang berbeda, untuk di proses lagi atau dicetak ke layar. 

```dart
int age = 17;

print(age); // mencetak angka 17

// mencetak teks berdasarkan nilai dari variabel age
if (age >= 17) {
    print("adult");
} else {
    print("kids");
}
```

Jika pembaca mencari arti dari _variable_ di dalam kamus, maka akan menmukan terjemahan "dapat berubah-ubah". Dalam pemrograman **variabel** merupakan sesuatu karena nilainya bisa diubah (dengan beberapa pengecualian)

```dart
int age = 17;

print(age); // 17

age = 21;

print(age); // 21
```

Dalam bahasa pemrograman Dart pada umumnya menggunakan _camelCase_ seperti Java dan Kotlin. Meskipun bisa menggunakan *snake_case*, tapi mengikuti standar yang umum dipakai akan lebih baik.

## Number

Angka menjadi jenis data yang paling sering digunakan disebuah aplikasi. Dart memberikan variasi tipe data yang bisa dipakai untuk bekerja dengan angka.

### `num`

Tipe data `num`, merupakan _superclass_ dari tipe data lain yaitu `double` dan `int`. Namun, dalam praktiknya, kita akan jarang sekali menggunakan `num` secara langsung tapi menggunakan `double` atau `int` karena lebih spesifik. 

<div class="note">
<strong><em>CATATAN:</em></strong> Superclass akan dibahas di bab Class & Object.
</div>

Berikut contoh penggunaan num:

```dart
num pi = 3.14;

// atau

num age = 17;
```

Tipe data num memiliki beberapa fungsi yang bisa dimanfaatkan untuk memproses angka di dalam suatu variabel. 

```dart
pi.toString() // mengubah angka menjadi string 3.14 

pi.toStringAsPrecision(2) // mengubah angka  dengan presisi di belakang koma, pada contoh ini akan menghasilkan 3.1

p.ceil() // Pembulatan ke atas (4)

p.floor() // Pebulatan ke bawah (3)
```

Karena `double` dan `int` merupakan _subclass_ dari `num`, maka mereka juga mendapat akses pada fungsi-fungsi di atas. 

Berdasarkan pengalaman penulis, tipe data `num` jarang dipakai secara langsung. Satu contoh kasus dimana `num` terpaksa dipakai adalah saat _backend api_ yang memberikan data secara dinamis berupa `int` tapi terkadang `double`. 

### `int`

Tipe data `int` menyimpan angka berupa bilangan bulat baik positif maupun negatif diantara -2^63 sampai 2^63-1.

Contoh deklarasi variabel int adalah sebagai berikut:

```dart
int age = 17;
```

Seringkali kita akan mendapatkan suatu data angka tapi berupa string. String tersebut bisa kita ubah menjadi `int` dengan memanggil method `parse`. 

```dart
int length = int.parse('413');
```

Meskipun jarang, tapi jika suatu hari membutuhkan variabel yang bisa menampung apa yang `int` bisa, kita bisa menggunakan class `BigInt` untuk angka yang lebih besar.

### `double`

Variabel bertipe `double` bisa menyimpan angka berupa bilangan desimal dengan limit yang kurang lebih sama seperti `int`. 

```dart
double pi = 3.14;
```

Perlu diketahui juga bahwa Flutter bisa memproses sebuah bilangan bulat dan menganggapnya sebagai _double_ secara otomatis. 

```dart
double width = 8;
```

Dalam bahasa pemrograman lain seperit Java dan Kotlin, kode di atas akan menghasilkan _compiler error_ karena `8` bukan sebuah `double`, harus dilengkapi dengan `8.0` atau dengan `8d` atau `8f`.

Sama halnya dengan `int`, double memiliki akses ke fungsi seperti `toString()`, `ceil()`, `floor()` dan `parse()` untuk mengubah string menjadi double. 

```dart
double width = double.parse('3.14');
```

## `String`

Data berupa teks disimpan sebagai sebuah `String`, mirip dengan bahasa pemrograman lain. Dart memungkinkan kita untuk menggunakan tanpa petik satu maupun petik dua. 

```dart
String name = "Bagus Aji";

// atau

String name = 'Bagus Aji';
```

Jika kita ingin menyelipkan variabel di dalam suatu teks, kita bisa menggunakan fitur _string interpolation_ dibandingkan menggunakan _string concatenation_. 

```dart
String name = "Bagus Aji";
String welcomeConcatenation = "Selamat pagi " + name + ". Selamat datang kembali.";
String welcomeInterpolation = "Selamat pagi $name. Selamat datang kembali.";
```

Karena seringnya flutter developer akan bekerja dengan String, kita akan membahasnya secara lebih mendalam di bab tersendiri

## `bool`

Sebuah variabel yang hanya bisa menyimpan dua nilai `true` atau `false` alias _boolean_, dalam pemrograman Dart menggunakan kata kunci `bool`. 

Variabel bertipe data boolean sering dipakai saat membuat kondisi percabangan atau perulangan. 


## List

`List` merupakan tipe data khusus yang berguna untuk menyimpan lebih dari satu data dalam tipe yang sejenis. Dalam bahasa pemrograman lain, _list_ berfungsi mirip dengan sebuah _array_. 

```dart
List<int> integers = [1, 2, 3, 4, 5];
List<double> doubles = [1.1, 1.2, 1.3];
```

List memiliki banyak method yang bisa dipakai untuk menambah, menghapus, mengurutkan atau mengosongkannya. 

Sama seperti bahasa pemrograman pada umumnya, List menggunakan index untuk mengakses elemen di dalamnya dimulai dari 0 sampai dengan jumlah data dikurangi 1. 

```dart
// Menambah item baru diujung
// [1, 2, 3, 4, 5, 9];
integers.add(9); 

// Mengakses indeks ke 2
// 3
integers[2]; 

// Menambah item baru di indeks ke-1
// [1, 7, 2, 3, 4, 5, 9];
integers.insert(1, 7);

// Menghapus elemen berdasarkan nilainya 
// [7, 2, 3, 4, 5, 9];
integers.remove(1);

// Mengurutkan list
integers.sort();

// Mengosongkan list
integers.clear();
```

List akan dibahas secara lebih mendalam di bab tersendiri. 

## Set

Secara sederhana, kita bisa menganggap bahwa `Set` merupakan variasi `List` yang hanya bisa menyimpan satu data yang sama (tidak boleh ada dua data yang sama di dalamnya). Set bisa dideklarasikan dengan menggunakan simbol `{}` berisi nilai-nilai awal:

```dart
Set<String> vegetables = {"Apple", "Durian", "Strawberry"};

vegetables.add("Pineapple");
// {Apple, Durian, Strawberry, Pineapple}

vegetable.add("Apple");
// {Apple, Durian, Strawberry, Pineapple}
// Apple tetap ada 1, tidak ada penambahan. 
```

## Map

Tipe data ini memungkinkan kita untuk memiliki _key-value pair_ atau kita bisa memasangkan suatu data pada tipe data yang lain. Contoh berikut menunjukkan bagimana kita menggunakan nomor punggung pemain sepak bola karena satu pemain hanya akan memiliki satu nomor punggung:

```dart
Map<int, String> players = {
    7: "Rafael Struick",
    12: "Pratama Arhan",
    22: "Ernando Ari S."
};
```

Dalam deklarasi Map, bagian `<int, String>` menentukan apa yang menjadi _key_ (nomor punggung berupa integer) dan apa yang menjadi _value_-nya (nama pemain berupa string). Baik _key_ maupun _value_ bisa menggunakan tipe data apa saja. 

Kita bisa mengakses nama pemain dengan memanfaatkan nomor punggunya (namun tidak sebaliknya). Cara mengakses isi map berdasarkan key adalah sebagai berikut:

```dart
players[12];
```

## Type Safety & Type Inference

Sebagai bahasa pemrograman modern yang canggih, Dart memiliki fitur _type inference_, artinya kita tidak perlu menuliskan tipe data saat mendeklarasikan suatu variabel. Pada umumnya, saat mendeklarasikan tipe data, programmer tidak secara langsung menulis tipe data seperti yang telah kita lakukan pada contoh-contoh sebelumnya. 

Dengan menggunakan keyword `var` seperti contoh di bawah, kita memberitahu Dart untuk "menggunakan tipe data yang paling cocok":

```dart
// variabel age mendapatkan tipe data int
var age = 17;

// variabel pi mendapatkan tipe data double
var pi = 3.14;

// variabel isAdult mendapatkan tipe ada bool
var isAdult = true;

// variabel arr mendapatkan tipe data List<int>
var arr = [1, 2, 3];

// variabel name mendapatkan tipe data String
var name = "Bagus Aji";

// variabel players mendapatkan tipe data Map<int, String>
var players = {
    7: "Rafael Struick",
    12: "Pratama Arhan",
    22: "Ernando Ari S."
};
```

Dart akan tahu bahwa angka `10` adalah sebuah integer, angka `3.14` adalah sebuah double, dan lain sebagainya. Jadi meskipun tidak secara eksplisit tipe datanya ditulis tapi Dart bisa memahami nya saat deklarasi variabel dengan `var`. 

Meskipun kita tidak menuliskan tipenya saat mendeklarasikan variabel, bukan berarti kita bisa bebas menggunakan tipe data yang lain sesudahnya variabel tersebut dideklarasikan.

```dart
var age = 17;
age = 17.5; 
```

Dart sudah mengasumsikan tipe data int untuk variabel `age`. Saat variabel age akan diubah dengan nilai yang bukan berupa integer misalnya double, maka akan muncul pesan error:

```
Error: A value of type 'double' can't be assigned to a variable of type 'int'.
```

Dart merupakan bahasa pemrograman yang _type-safe_, artinya sekali dideklarasikan, maka tidak bisa diubah lagi seperti pada contoh di atas. Fitur _type safety_ ini akan membantu kita menghindari error yang terjadi akibat data yang tidak seharusnya sehingga bisa menyebabkan aplikasi mengalami _crash_.

Fitur _type safety_ ini bisa dihindari dengan menggunakan tipe data khusus bernama `dynamic`. Semua tipe data yangn ada di dart pada dasarnya merupakan `dynamic` sehingga data yang ditampung bisa diubah dengan tipe data yang lain.  

```dart
dynamic age = 17;
age = 17.5;

print(age);
// 17.5

age = "seventeen";
print(age);
// seventeen
```

Meskipun bisa, penggunaan tipe data `dynamic` tidak direkomendasikan tanpa alasan khusus. Memakai tipe ini akan menyulitkan proses bug fixing yang terkait dengan tipe data kaerna tipe data dynamic bisa berubah-ubah. 

Pembaca perlu berhati-hati saat menggunakan _type inference_ di tipe data _collection_ misalnya List. 

```dart
var lst = [];

print(lst.runtimeType); // List<dynamic>
```

## Constant & Final

Dart bisa memiliki dua jenis variabel yang setelah diisi satu kali, tidak bisa diubah lagi sesudahnya. Dua jenis variabel ini dibuat dengan `const` dan `final`. 

### `const`

Variabel yang datanya bisa diubah seperti pada contoh-contoh sebelumnya disebut sebagai _mutable data_. Sementara itu, ada beberapa kasus di mana kita memerlukan variabel yang datanya tidak bisa diubah. Variabel yang datanya tidak bisa diubah lagi ini disebut juga dengan _immutable data_. 

Untuk membuat sebuah variabel konstan, gunakan `const`:

```dart
const pi = 3.14;
```

Dalam matematika, pi sudah memiliki ketetapan dimana nilainya akan selalu `3.14`, bila nilai pi diubah maka hasil perhitungannya tentu akan ikut berubah juga. Untuk mencegah agar variabel pi tidak diubah disuatu tempat, deklarasikan sebagai sebuah variabel konstan. Sama seperti `var`, saat kita menggunakan `const`, Dart juga akan cukup pintar untuk menentukan tipe data nya lewat _type inference_.

```dart
const pi = 3.14;
pi = 3;
```

Kode di atas tidak akan bisa di _compile_ dan menghasilkan pesan error:

```dart
Error: Can't assign to the const variable 'pi'.
```

### `final`

Secara konsep `final` sama dengan `const`, hanya saja saat menggunakan const, nilainya harus sudah ditentukan sebelum aplikasi di _compile_. Apabila kita menginginkan sebuah `const` tapi belum ada nilainya saat aplikasi di _compile_, itulah saat kita membutuhkan yang namanya _runtime constant_. 

Cara mudah membedakan kapan menggunakan `const` dan `final` adalah dengan melihat nilainya. 

```dart
const age = 17;
const name = "Bagus";
const pi = 3.14;
```

Pada contoh di atas kita sudah tahu saat mendeklarasikan variabel, apa nilai yang akan dituliskan setelah `=`. Apabila data tersebut tidak bisa dituliskan secara langsung dan perlu menunggu suatu proses lain setelah aplikasi dijalankan seperti data yang datang dari suatu api atau query database, maka saat itulah kita menggunakan `final`.

```dart
final now = DateTime.now();
print(now);
// 2024-06-23 13:52:50.722594 
```

Method `DateTime.now()` adalah fungsi yang akan memberikan jam dan tanggal saat program diakses. Karena nilainya baru akan didapat bila program sudah jalan, maka variabel now yang kita miliki tidak bisa dideklarasikan dengan `const` sehingga harus menggunakan `final`. 

