---
title: Belajar SQLite untuk Pemula
date: 2024-03-14
description: Kita akan memulai seri belajar SQLite dengan membahas apa itu SQLite dan bagaimana cara membuat database yang baru. 
tags: sqlite
series: sqlite
series_title: Belajar SQLite untuk Pemula
series_order: 10
favorite: true
---

{% include series.liquid %}

SQLite merupakan sistem basis data yang berdiri sendiri, tidak perlu menggunakan server, berukuran sangat kecil, tidak butuh banyak konfigurasi namun memiliki fitur yang lengkap. Karena ukurannya yang sangat kecil dan ringan ini, SQLite menjadi sistem basis data pilihan yang dipakai oleh Android juga iOS.

Pembaca bisa menganggap SQLite sebagai variasi yang lebih ringan dari MySQL, PostgreSQL atau sejenisnya. Tidak seperti mayoritas sistem basis data SQL lain, SQLite tidak butuh server karena data disimipan dalam bentuk file. Hal ini yang membuat SQLite begitu portable, file databasenya bisa disimpan di mana saja dan mudah untuk dipindah-pindahkan.

Dalam sistem operasi seperti Linux atau MacOS, SQLite sudah langsung tersedia. Untuk memeriksanya, eksekusi perintah berikut di terminal:

```bash
sqlite3
```

![](/assets/images/posts/CleanShot-2024-06-09-at-13.02.14@2x.png)

Untuk membuat database SQLite baru dari  _command line_, jalankan perintah berikut:

```bash
$ sqlite3 university.db
SQLite version 3.43.2 2023-10-10 13:08:14
Enter ".help" for usage hints.

```

SQLite sendiri tidak menentukan ekstensi apa yang harus dipakai. Kita bisa menggunakan  `.db`  atau boleh juga menggunakan  `.sqlite3`  supaya file tersebut terlihat sebagai sebuah file database milik SQLite.

Untuk memeriksa database yang sedang dibuka, gunakan perintah:

```bash
sqlite> .databases
main: /Users/baguzzzaji/Sandbox/university.db r/w
```

Sementara itu, untuk keluar dari  _prompt_  SQLite, gunakan perintah:

```sql
.quit
```