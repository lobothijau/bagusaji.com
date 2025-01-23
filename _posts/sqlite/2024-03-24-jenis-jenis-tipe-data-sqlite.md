---
title: Jenis-jenis Tipe Data di SQLite
date: 2024-03-24
description: Artikel ini akan membahas tentang jenis-jenis tipe data yang dapat digunakan di sistem database SQLite.
tags: sqlite
series: sqlite
series_title: Belajar SQLite untuk Pemula
series_order: 40
---

{% include series.liquid %}

Sistem database lain seperti MySQL dan PostgreSQL menggunakan  _static typing_, artinya suatu kolom yang telah memiliki tipe data tertentu, tidak bisa menyimpan tipe data lain. Pada contoh di bawah, kolom  `quantity`  hanya bisa menyimpa bilangan bulat saja.

```sql
CREATE TABLE orders (
   ...
   quantity INT NOT NULL,
   ...
);
```

Sementara itu, SQLite menggunakan  _dynamic type system_, artinya tipe data suatu kolom ditentukan oleh apa data yang tersimpan, bukan oleh tipe data yang dideklarasikan saat tabel dibuat. Ini artinya, meskipun sebuah kolom memiliki tipe data integer, kita masih bisa menambahkan tipe data seperti teks tanpa ada masalah.

Ada lima tipe data dasar yang disediakan SQLite, kelimanya disebut sebagai  _storage classes_.

1.  NULL: artinya kosong atau tidak ada
2.  INTEGER: merupakan bilangan bulat (baik positif atau negatif).
3.  REAL: adalah bilangan desimal.
4.  TEXT: dipakai untuk menyimpan data teks tanpa batas maksimal panjangnya.
5.  BLOB: adalah singaktan dari  _binary large object_  yang bisa menyimpan berbagai macam data.

Untuk menentukan tipe data dari suatu  _value_, SQLite akan mengikuti aturan berikut:

-   Jika data tersebut tidak diapit tanda petik, tidak
-   Jika data diapit oleh petik satu atau dua, maka dianggap TEXT.
-   Jika data tidak diapit oleh tanda petik, tidak memiliki simbol desimal dan tidak ada tanda pangkat, maka dianggap INTEGER.
-   Jika data tidak diapit oleh tanda petik, memiliki simbol desimal atau pangkat,
-   JIka data bernilai NULL tanpa tanda petik, dianggap NULL.
-   Jika data diawali oleh `X’…’, maka dianggap BLOB

SQLite tidak memiliki tipe data untuk date atau datetime, tapi kita bisa menggunakna TEXT, INT atau REAL untuk menyimpannya.

```sql
CREATE TABLE tipedata (
    id INTEGER PRIMARY KEY,
    data
);
```

Perhatikan pada kolom data kita tidak mendefinisikan tipe datanya apa. Lakukan insert data-data berikut:

```sql
INSERT INTO
  tipedata (data)
VALUES
  (1),
  (100),
  (3.14),
  ('A'),
  ('Belajar'),
  (NULL),
  (x'0000');
```

Selanjutnya kita periksa tipe data masing-masing baris dengan  _typeof_.

```sql
SELECT
  id,
  data,
  typeof (data)
FROM
  tipedata;
```

Maka hasilnya akan terlihat seperti berikut:

```sql
id  data     typeof (data)
--  -------  -------------
1   1        integer      
2   100      integer      
3   3.14     real         
4   A        text         
5   Belajar  text         
6            null         
7            blob
```

Bila suatu kolom bisa menyimpan data secara dinamis, lalu pertanyaan berikutnya, bagaimana cara SQLite melakukan  _sorting_? Secara garis besar, SQLite akan mengikuti aturan-aturan berikut:

-   NULL akan mendapat nilai terendah diantara data lain.
-   Berikutnya yang nilainya lebih tinggi adalah INTEGER dan REAL.
-   Nilai yang lebih tinggi berikutnya adalah TEXT.
-   Nilai tertinggi adalah BLOB.

```sql
SELECT
  id,
  data,
  typeof (data)
FROM
  tipedata
ORDER BY
  data;
```

Perintah di atas akan menghasilkan:

```
id  data     typeof (data)
--  -------  -------------
6            null         
1   1        integer      
3   3.14     real         
2   100      integer      
4   A        text         
5   Belajar  text         
7            blob    
```