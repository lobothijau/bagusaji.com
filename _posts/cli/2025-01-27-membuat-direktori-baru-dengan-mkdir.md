---
title: "Membuat Direktori Baru dengan mkdir"
date: 2025-01-27
description: "Artikel ini akan membahas beberapa cara membuat direktori baru dengan perintah mkdir dengan command line."
tags: cli
series: cli
series_order: 30
series_title: "Membuat Direktori Baru dengan mkdir"
---

Untuk membuat direktori baru atau folder baru lewat command line dapat kita lakukan dengan perintah `mkdir`. Cara penulisannya adalah sebagai berikut:

```bash
$ mkdir nama_direktori
```

Contoh, untuk membuat direktori baru dengan nama `Downloads`, kita bisa mengetikkan perintah `mkdir Downloads`. 

Kita juga bisa membuat beberapa direktori baru dengan satu perintah. Caranya adalah dengan mengetikkan perintah `mkdir` diikuti dengan nama direktori yang ingin kita buat, dipisahkan dengan spasi. 

```bash
$ mkdir Downloads Documents
```

Perintah di atas akan membuat dua direktori baru, yakni `Downloads` dan `Documents`.

Untuk membuat direktori baru di dalam direktori lain, kita perlu menuliskan path lengkapnya baik dengan absolute path maupun relative path. Contoh, untuk membuat direktori baru dengan nama `Downloads` di dalam direktori `Documents`, kita bisa mengetikkan perintah:

```bash
$ mkdir Documents/Downloads
```

Perlu diketahui bahwa untuk membuat subdirektori, direktori utamanya harus sudah ada. Jika tidak ada, maka perintah di atas akan menghasilkan error. Apabila dalam kasus di atas direktori `Documents` tidak ada, maka kita bisa memanfaatkan flag `-p` untuk membuatnya. 

```bash
# Direktori Documents belum ada, maka akan kita buat keduanya sekaligus
$ mkdir -p Documents/Downloads
```
