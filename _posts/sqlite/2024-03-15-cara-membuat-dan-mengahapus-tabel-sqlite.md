---
title: Cara Membuat dan Menghapus Tabel di SQLite
date: 2024-03-15
description: Artikel ini akan membahas tentang cara membuat dan menghapus tabel di SQLite.
tags: sqlite
series: sqlite
series_title: Belajar SQLite untuk Pemula
series_order: 20
---

{% include series.liquid %}

Mirip seperti di MySQL, perintah untuk membuat tabel di SQLite adalah  `CREATE TABLE`.

```sql
CREATE TABLE students(
	id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL,
	name TEXT NOT NULL,
	age INTEGER NOT NULL,
	grade REAL
);
```

Daftar tipe data yang bisa digunakan dapat dibaca  [di artikel berikut](https://www.baguzzzaji.com/?p=47).

Mari kita buat satu tabel lagi agar ada dua tabel di database ini.

```sql
CREATE TABLE departments(
	id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, 
	name TEXT NOT NULL
);

```

Selanjutnya kita periksa tabel-tabel yang sudah dibuat:

```sql
sqlite> .tables
departments  students   
sqlite> 
```

Menghapus tabel di SQLite dilakukan dengan perintah  `DROP`. Contoh penggunaannya adalah sebagai berikut:

```sql
sqlite > DROP TABLE departments;
sqlite > .tables
students
```