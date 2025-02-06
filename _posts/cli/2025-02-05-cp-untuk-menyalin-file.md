---
title: "Menggunakan cp Untuk Menyalin File"
date: 2025-02-05
description: "Artikel ini akan membahas tentang cara menggunakan perintah cp untuk menyalin file di command line."
tags: cli
series: cli
series_order: 80
series_title: "Menggunakan cp Untuk Menyalin File"
---

{% include series.liquid %}

Perintah `cp` bisa dipakai untuk menyalin file, diambil dari kata _copy_ dalam bahasa Inggris. Cara penulisannya adalah sebagai berikut:

```bash
$ cp nama_file_asal nama_file_tujuan
```

Untuk menyalinnya ke dalam folder lain, maka ikutsertakan path folder tujuan dengan relative maupun absolute path. 

```bash
$ cp my-first-project ~/Sandbox/Go
```

Untuk menyalin beberapa file, kita bisa mengetikkan perintah `cp` diikuti dengan nama file yang ingin disalin, dipisahkan dengan spasi. Kuncinya adalah folder tujuan tertulis terakhir.

```bash
$ cp my-first-project my-second-project ~/Sandbox/Go
```

Perintah `cp` bisa dipakai baik untuk file maupun folder. 

Berikut beberapa opsi yang bisa dipakai bersama dengan perintah `cp`:

- `-a` atau `--archive` : menyalin file dan folder dengan mode dan permission yang sama.
- `-i` atau `--interactive` : perintah `cp` akan menimpa file tanpa konfirmasi, flag ini dipakai untuk meminta konfirmasi sebelum menimpa file yang sudah ada.
- `-r` atau `--recursive` : menyalin folder dan isinya.
- `-u` atau `--update` : menyalin file yang belum ada di folder tujuan atau file yang lebih baru dari file yang sudah ada di folder tujuan.
- `-v` atau `--verbose` : menampilkan pesan informatif saat menyalin file.
