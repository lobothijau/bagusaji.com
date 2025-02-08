---
title: "Menggunakan Symbolic Link"
date: 2025-02-07
description: "Artikel ini akan membahas tentang cara menggunakan symbolic link di command line."
tags: cli
series: cli
series_order: 90
series_title: "Menggunakan Symbolic Link"
---

{% include series.liquid %}

Symbolic link dalam kehidupan sehari-hari amat jarang digunakan. Berdasarkan pengalaman pribadi, symbolic link lebih banyak dipakai untuk kebutuhan sistem atau server. Symbolic link bekerja dengan cara membuat file khusus yang berisi pointer ke file atau folder lain. Cara kerjanya mirip dengan shortcut di Windows, meskipun sudah ada jauh lebih dulu sebelum Windows.  

File asli dengan symbolic link nya hampir tidak bisa dibedakan (namun bisa dilihat lewat `ls -al`). Jika kita mengubah isi dari sautu symbolic link, maka file asli yang direferensikan juga akan ikut berubah. Namun, jika kita menghapus symbolic link, maka file asli tidak akan terhapus. Jika file asli dihapus sebelum symbolic link, maka symbolic link akan tetap ada, namun tidak akan menunjuk ke file apapun. 

Konsep symbolic link memang sulit dipahami karena jarang digunakan di sisi user. Namun, bila sering berhubungan dengan server, cepat atau lambat akan lebih paham nantinya. 

Sebagai contoh, mari buat sebuah folder baru sebagai latihan:

```bash
$ mkdir symlink
$ cd symlink
$ mkdir dir1 dir2
```

Lalu salin file random ke folder symlink:

```bash
$ cp /dev/urandom random.txt
```

