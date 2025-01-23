---
title: Tutorial Insert Data ke SQLite
date: 2024-03-22
description: Artikel ini akan membahas bagaimana cara melakukan operasi  `INSERT`  untuk menambahkan data baru ke sebuah tabel di SQLite.
tags: sqlite
series: sqlite
series_title: Belajar SQLite untuk Pemula
series_order: 30
---

{% include series.liquid %}

Artikel ini akan membahas bagaimana cara melakukan operasi  `INSERT`  untuk menambahkan data baru ke sebuah tabel di SQLite. Perintah ini bisa dipakai untuk menambah satu baris data, beberapa baris serta memberikan  _default value_  ke sebuah tabel.

Untuk menambahkan satu baris data baru, struktur perintah SQL adalah sebagai berikut:

```sql
INSERT INTO nama_tabel (kolom1,kolom2 ,..)
VALUES (data1,data2,...);
```

-   Tentukan nama tabelnya, contoh  `students`
-   Tentukan nama-nama kolomnya, contoh  `name`,  `age`
-   Tentukan nilai untuk masing-masing kolom, contoh  `Bagus`,  `28`

perhatikan untuk nama kolom dan nilai-nilainya akan dipisahkan oleh koma dan harus sesuai urutan agar datanya masuk di kolom yang benar.

Pada contoh berikut kita akan menggunakan tabel  `students`  yang sebelumnya  [sudah pernah kita buat](https://www.baguzzzaji.com/cara-membuat-dan-menghapus-tabel-di-sqlite/). Untuk pengingat, berikut struktur tabelnya.

![](/assets/images/posts/Screenshot-2024-06-14-at-11.35.01.png)

Untuk menambahkan satu baris data pada tabel di atas, perintahnya adalah:

```sql
INSERT INTO students (name, age, grade)
VALUES ("Bagus", 17, 4.0)
```

Sementara itu untuk menambahkan banyak data sekaligus, perintahnya adalah:

```sql
INSERT INTO nama_tabel (kolom1,kolom2 ,..)
VALUES 
   (data1,data2,...),
   (data3,data4,...),
    ...
   (data100,data100,...);
```

Perhatikan bahwa setiap baris data yang diapit oleh tanda kurung, diakhiri dengan koma sebagai pemisah dengan baris berikutnya.

Berikut contoh insert data untuk tabel di atas:

```sql
INSERT INTO students (name, age, grade)
VALUES 
	("Budi", 17, 3.1),
	("Ayu", 18, 3.3),
	("Bambang", 17, 2.95)
```

Dan hasil dari 2 perintah di atas adalah sebagai berikut:

![](/assets/images/posts/Screenshot-2024-06-14-at-11.51.46.png)
