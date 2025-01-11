---
title: Cara Kerja Arrow Function di PHP 7
date: 2024-11-07
description: "Arrow function merupakan fitur baru yang ditambahkan pada rilis PHP 7.4. Apabila pembaca mengenal bahasa pemrograman JavaScript khususnya setelah ES6, mungkin sudah lebih dahulu familiar dengan fitur ini."
tags: php
---

Arrow function merupakan fitur baru yang ditambahkan pada rilis PHP 7.4. Apabila pembaca mengenal bahasa pemrograman JavaScript khususnya setelah ES6, mungkin sudah lebih dahulu familiar dengan fitur ini.

## Untuk apa arrow function di PHP?

Secara singkat, arrow function berfungsi untuk menyingkat penulisan suatu closure atau istilah lainnya anonymous function di PHP.

Mari kita lihat beberapa contoh:

```
$books->each(function ($b) {
    $b->title = ucwords($b->title);
})
```

Pada contoh di atas kita ingin mengubah judul suatu buku menjadi huruf kapital pada suatu  _collection of books object_  (asumsi ini adalah sebuah collection Laravel). Karena closure di atas hanya terdiri dari satu baris saja, maka bisa kita tulis ulang dengan arrow function menjadi:

```
$books->each(fn ($b) => $b->title = ucwords($b->title));
```


_Keyword_ yang dipakai saat menggunakan arrow function adalah  `fn`  diikuti dengan list parameter, lalu arrow function itu sendiri (simol  `=>`) dan satu baris code yang ingin di eksekusi.

## Bagaimana menggunakan use dengan arrow function?

Mari kita lihat contoh lainnya, yaitu melakukan pencarian disuatu collection:

```
$books->first(function ($book) use ($keyword) {
  return $book->title === $keyword;
});
```

Kode di atas dapat ditulis ulang menjadi:

```
$books->first(fn ($book) => $book->title === $keyword) ;
```

Perintah return dalam arrow function dilakukan secara implicit. Jadi, meskipun kita tidak tuliskan function tersebut akan tetap memberikan return value dengan denagn data yang ada.

Selain itu, arrow function memiliki akses pada scope di atasnya, sehingga kita tidak lagi membutuhkan  `use`  untuk bisa menggunakan  `$keyword`  atau variabel lain diluar arrow function.