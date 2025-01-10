---
title: "Perulangan di Pemrograman Dart"
date: 2025-01-05
description: "Perulangan dipakai untuk mengeksekusi suatu kode yang perlu dijalankan berulang kali hanya lewat satu kali penulisan."
series: dart
series_title: "Perulangan di Pemrograman Dart"
---

{% include series.liquid %}


Pada pembahasan bab-bab esbelumnya kita telah belajar tentang bagaimana mendeklarasikan suatu variabel, bagaimana menentukan tipe data dari suatu variabel, serta bagaimana membuat program yang kita buat bisa memutuskan sesuatu berdasarkan suatu nilai. Program-program tersebut ditulis dalam program main yang dieksekusi baris demi baris sampai dengan selesai. Bab ini akan membahas tentang bagaimana suatu program bisa mengulang-ulang suatu proses sesuai dengan apa yang kita inginkan. Perulangan sering dipakai saat melakukan pencarian, melakukan pengurutan data, atau proses otomatisasi yang harus dilakukan berulang kali. 

## Perulangan For

Perulangan `for`  merupakan salah satu konsep yang ada hampir disemua bahasa pemrograman. Aturan penulisan perulangan `for` di pemrograman Dart mirip seperti pada bahasa pemrograman turunan C lainnya. 

```dart
for (var i = 0; i < 5; i++) {
    print(i);
}
```

Bila pembaca pernah belajar bahasa pemrograman lain sebelumnya, pasti familiar dengan blok `for` di atas. Jika ini pertama kalinya, jangan risau, mari kita bahas satu demi satu.

Sebelum proses perulangan berlangsung, kita akan memulainya dengan menentukan sebuah variabel yang menentukan kapan dan berapa kali proses perulangan terjadi. Deklarasi `var i = 0` pada contoh di atas bisa dinamakan apa saja, `i` di sini diambil dari kata _index_. Variabel tersebut diberikan sebuah nilai awal, biasanya angka `0`, tapi juga bisa diatur sesuai kebutuhan. Jangan lupa perhatikan titik komanya. 

Setelah menentukan nilai awal, tahap berikutnya adalah memberikan kondisi kapan perulangan ini terus berjalan. Selama kondisi bernilai `true`, maka perulangan akan terus berjalan sampai ia hasilnya menjadi `false`. Pada contoh ini, program akan terus berjalan selama variabel `i` nilainya di bawah lima, ketika variabel `i` nilainya menjadi 5, perulangan akan berhenti. 

Tahap berikutnya adalah melakukan _increment_ atau _decrement_ yaitu proses untuk mengubah nilai variabel ini. Bila variabel i nilainya tidak berubah, maka perulangan kita beresiko untuk tidak pernah berhenti atau istilah kerennya _looping forever_/_invite loop_. 

Kode `i++` pada contoh sama artinya dengan `i = i + `, artinya kita ingin menambahkan angka satu ke variabel `i`. Bila sekarang `i` bernilai `3`, maka `i++` akan membuat variabel `i` bernilai `4`. Proses _increment_ baru akan terjadi ketika semua kode pada blok `for` telah tereksekusi, artinya setelah kode `print(i)` dijalankan, nilai `i` tersebut baru di _increment_-kan. 

Bila contoh program di atas dibalik untuk menuliskan angka 4 sampai dengan 0 dengan _decrement_ maka hasilnya adalah:

```dart
for (var i = 4; i >= 0; i--) {
    print(i);
}
```

## Perulangan While

Perulangan dengan `while` memiliki struktur yang sedikit berbeda dengan `for`. Contoh penulisan blok `while` adalah sebagai berikut:

```dart
while(true) {
    // kode program yang lain
}
```

Perulangan while akan memeriksa kondisi yang diberikan di dalam tanda kurung. Selaam bernilai `true` maka program akan jalan terus. Apabila contoh pada perulangan `for` ditulis ulang dengan `while, maka hasilnya akan menjadi:

```dart
var i = 0; 

while (i < 5) {
    print(i);
    i++;
}
```

Pertama kita deklarasikan dulu variabel `i` untuk mengontrol perulangan sehingga tidak terjadi _infinite loop_. Selanjutnya, `while` akan memeriksa kondisi apabila variabel `i` nilainya di bawah `i` maka lakukan perintah `print`, lalu _increment_ variabel `i`. Ketika i sudah bernilai 4, maka program akan berhenti. 

## Perulangan Do While

Perulangan dengan `do while` memiliki sedikit perbedaan dengan `while`. Perbedaannya, kondisi perulangan diperiksa diakhir blok bukan di awal. Oleh karena itu, ketika menggunakan `do while`, blok perulangan pasti akan dijalankan dulu minimal satu kali. 

Contoh program perulangan sebelumnya bila ditulis dengan `do while` akan menjadi:

```dart
var i = 0;
do {
    print(i);
    i++;
} while (i < 5);
```

Program di atas akan menghasilkan keluaran yang sama, hanya saja struktur penulisannya yang berbeda. 

## Break, Keluar dari Loop

Sebuah yang memiliki perulangan tidak harus selalu menunggu perulangan itu untuk selesai. Dalam kasus tertentu kita perlu untuk keluar dari proses perulangan meskipun belum mencapai kondisi dimana seharusnya perulangan itu berhenti. 

```dart
  var i = 1;

  while (i < 10000) {
    print(i);

    if (i == 999) {
      break;
    }

    i++;
  }
```

Pada contoh kode di atas, terdapat dua kondisi untuk berhenti melakukan perulangan. Kondisi yang pertama saat variabel `i` bernilai `10000` dan kondisi yang kedua saat variabel i bernilai `999`. 

Saat nilai i bernilai `999`, meskipun belum memenuhi kondisi yang seharusnya, tapi kode `break` akan menyebabkan perulangan untuk behenti. 

## Continue, Lanjut ke Perulangan Berikutnya

Terkadang ada keperluan dimana kita tidak perlu menghentikan proses perulangan, mungkin kita cukup melewati proses perulangan tertentu. Perhatikan contoh berikut:

```dart
for (var i = 0; i < 100; i++) {
  if (i % 10 == 0) {
    continue;
  }
  print(i);
}
```

Program di atas akan mencetak setiap angka dari 0 sampai 999, tapi setiap angka kelipatan 10 akan dilewati. Perintah `continue` akan langsung memanggil proses _increment_ (`i++`), lalu kembali ke awal program.

