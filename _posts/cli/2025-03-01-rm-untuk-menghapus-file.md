---
title: "Menggunakan rm Untuk Menghapus File"
date: 2025-03-01
description: "Artikel ini akan membahas tentang cara menggunakan perintah rm untuk menghapus file di command line."
tags: cli
series: cli
series_order: 100
series_title: "Menggunakan rm Untuk Menghapus File"
---

{% include series.liquid %}

Perintah `rm` bisa dipakai untuk menghapus file maupun direktori. Cara penulisannya adalah sebagai berikut:

```bash
$ rm nama_file_atau_direktori
```

Atau bila ingin menghapus beberapa file, kita tuliskan semua nama file nya, mirip seperti `cp` dan `mv`.

```bash
$ rm file1 file2 file3
```

Berikut adalah beberapa opsi yang bisa dipakai bersama dengan perintah `rm`:

- `-f`: Menghapus file tanpa meminta konfirmasi (`--force`).
- `-r`: Menghapus direktori dan semua isinya (`--recursive`).
- `-i`: Memberikan konfirmasi sebelum menghapus (`--interactive`).

Berdasarkan keterangan di atas, untuk menghapus direktori dan semua isinya, kita bisa menggunakan opsi `-r` dan `-f` sekaligus.

```bash
$ rm -rf direktori
```

## Berhati-hati dengan perintah `rm`

Sistem operasi seperti Linux tidak memiliki fitur `undelete`. Bila pernah menggunakan Windows, pembaca akan dekat dengan Recycle Bin. Sementara bila menggunakan macOS, pembaca akan dekat dengan Trash Bin. Bila kita menghapus file menggunakan aplikasi gui seperti `Nautilus` di GNOME, biasanya file akan masuk ke Trash Bin terlebih dahulu. Tapi tidak bila menggunakan perintah `rm` di terminal.