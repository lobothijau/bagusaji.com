---
title: "Menggunakan mv Untuk Memindah File dan Rename"
date: 2025-02-06
description: "Artikel ini akan membahas tentang cara menggunakan perintah mv untuk memindah file dan rename file di command line."
tags: cli
series: cli
series_order: 90
series_title: "Menggunakan mv Untuk Memindah File dan Rename"
---

{% include series.liquid %}

Perintah `mv` bisa dipakai untuk memindah file dan rename file, tergantung cara pemakaiannya. Cara menggunakan `mv` kurang lebih sama dengan `cp`:

```bash
$ mv nama_file_asal nama_file_tujuan
```

Atau bila ingin memindah beberapa file, kita tuliskan semua nama file nya sebelum folder tujuan, mirip seperti `cp`. Folder tujuan harus sudah ada sebelumnya.

```bash
$ mv my-first-project my-second-project ~/Sandbox/Go
```

Opsi yang bisa dipakai bersama dengan perintah `mv` kurang lebih sama dengan `cp`.