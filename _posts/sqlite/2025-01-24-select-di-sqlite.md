---
title: SELECT di SQLite
date: 2025-01-24
description: Artikel ini akan membahas tentang perintah SELECT di SQLite dan bagaimana cara menggunakannya
tags: sqlite
series: sqlite
series_title: Belajar SQLite untuk Pemula
series_order: 50
---


Perintah `SELECT` merupakan perintah yang paling sering digunakan di SQLite karena perintah ini dipakai untuk mengambil data dari database. Artikel ini akan membahas beberapa cara untuk menggunakan perintah `SELECT` di SQLite.

## Mengambil Semua Data

Untuk mengambil semua data dari sebuah tabel, kita bisa menggunakan perintah `SELECT` dengan memasukkan nama tabel yang ingin kita ambil data.

```sql
SELECT * FROM students;
```

Mengikuti data yang pernah kita insert sebelumnya, hasil dari perintah di atas adalah sebagai berikut:

![](/assets/images/sqlite/select.png)

Simbol `*` artinya akan mengambil semua kolom dari tabel yang kita tentukan yaitu `id`, `name`, `age`, dan `grade`. Simbol ini sering juga disebut sebagai wildcard dan akan sering dipakai dibanyak perintah SQL juga di pemrograman lain dengan konsep yang mirip, `*` berarti semua. 

## Mengambil Beberapa Kolom

Kita juga bisa mengambil beberapa kolom dari tabel yang kita tentukan. Caranya adalah dengan menuliskan nama kolom yang ingin kita ambil, dipisahkan oleh koma.

```sql
SELECT id, age FROM students;
```

![](/assets/images/sqlite/select-column.png)

## Penutup

Sebagian developer akan menyarankan untuk tidak menggunakan *wildcard* dan menentukan secara eksplisit kolom yang ingin kita ambil. Dengan begitu, data yang dikembalikan dari database akan sesuai dengan kebutuhan, tanpa mengekspos data yang tidak perlu.