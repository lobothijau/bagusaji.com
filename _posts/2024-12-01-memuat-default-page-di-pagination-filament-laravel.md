---
title: Memuat Halaman Default di Pagination Filament Laravel
date: 2024-12-01
description: |
  Artikel ini membahas cara memuat halaman default di pagination Filament Laravel.
tags: laravel, filament
---

Beberapa waktu yang lalu penulis mendapat sebuah kasus di project Laravel dengan Filament. Salah satu Resource yang ada, perlu menampilkan halaman tertentu saat pertama kali dibuka.  _Let’s say_  hari ini ada di minggu ke 38, maka Resource tersebut saat pertama kali dibuka harus lompat ke halaman 38.

![Lompat ke halaman 38](/assets/images/posts/filament-default-page.png)

Untuk mencapai tujuan tersebut, kita harus menambahkan beberapa kode di kelas  **ListRecords**  (bila Resource bernama Bucket, maka class tersebut akan bernama  **ListBuckets**). Teknik ini belum teruji di Resource yang dibuat dengan  _flag_  `--simple`  saat di  _generate_.

Langkah pertama, tambahkan method  `mount()`  di kelas tersebut. Method ini merupakan method  _lifecycle_  yang akan dipanggil setiap halaman tabel di load pertama kali. Penulis tidak yakin apakah method ini diturunkan dari parent class-nya saja atau didapat dari livewire.

```
class ListBuckets extends ListRecords
{
    public function mount(): void
    {

    }
}

```

Setiap ListRecords ternyata memiliki method  `setPage`  yang dipakai untuk mengubah halaman yang sedang diakses. Oleh karena itu, kita tinggal memanggil method ini untuk mengubah default halaman yang ingin dibuka setiap mengakses halaman Resource tertentu.

```

    public function mount(): void
    {
        $this->authorizeAccess();
        $this->loadDefaultActiveTab();

        // Mengambil minggu sekarang
        $dateNow = date('Y-m-d');
        $weekNumber = date("W", strtotime($dateNow));

        $this->setPage($weekNumber); // Mengubah halaman
    }
```

Pada contoh kode di atas, bagian yang paling penting untuk mengubah halaman adalah baris yang terakhir.