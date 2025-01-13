---
title: "Tutorial Export dan Import (Dump) Database MySQL"
date: 2024-08-01
description: |
  Sebagai seorang fullstack developer, bekerja dengan database menjadi salah satu makanan sehari-hari. Apalagi ketika website sudah di upload ke server, seringkali kita perlu meng-export database dari server untuk di import ke database lokal atau sebaliknya.
tags: mysql, database
---

Sebagai seorang fullstack developer, bekerja dengan database menjadi salah satu makanan sehari-hari. Apalagi ketika website sudah di upload ke server, seringkali kita perlu meng-export database dari server untuk di import ke database lokal atau sebaliknya.

Artikel ini akan membahas bagaimana cara meng export data dengan database dump di MySQL atau MariaDB.

## Export Database MySQL

Untuk melakukan export data dari database SQL kita bisa memanfaatkan perintah  `mysqldump`. Perintah ini akan meminta nama database dan kredensial server MySQL yang aktif.

Berikut contoh perintahnya:

```
mysqldump -u username -p nama_db > dump.sql
```

-   username pada perintah di atas adalah username yang bisa mengakses database
-   nama_db adalah nama database yang akan di export
-   dump.sql adalah nama file yang akan kita dapatkan

Perintah di atas tidak akan memberikan keluaran apapun, tapi kita akan mendapatkan sebuah file bernama  `dump.sql`  di folder yang saat ini sedang aktif.

![](/assets/images/posts/Screenshot-2024-07-25-at-12.23.55-1024x725.png)

Berikut contoh konten dari file dump SQL yang akan kita dapatkan.

![](/assets/images/posts/Screenshot-2024-07-25-at-12.25.21-1024x819.png)

## Import Database MySQL

Langkah berikutnya setelah meng-export database dan mendapat file dump, kita akan meng-import file tersebut. Untuk melakukan import kita harus pastikan bahwa sudah ada database dengan nama yang sama.

Untuk membuat database MySQL baru, buka prompt MySQL:

```
mysql -u root -p
```

Berikutnya buat sebuah database dengan perintah CREATE DATABASE. Pastikan nama database nya sama:

```
mysql > CREATE DATABASE kelascatur;
```

Keluar dari prompt MySQL dengan menekan  `CTRL+D`. Selanjutnya import file dump tersebut dengan perintah:

```
mysql -u root -p kelascatur < dump.sql
```

Bila berhasil maka perintah di atas tidak akan memberikan hasil apa-apa, namun bila error baru akan muncul pesan error-nya.