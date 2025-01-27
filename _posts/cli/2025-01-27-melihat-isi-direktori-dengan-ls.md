---
title: Melihat Isi Direktori Dengan ls
date: 2025-01-27
description: Artikel ini akan membahas tentang cara melihat isi direktori dengan perintah ls di command line. 
tags: cli
series: cli
series_order: 50
series_title: "Melihat Isi Direktori Dengan ls"
---

{% include series.liquid %}

Untuk melihat isi dari suatu direktori, kita bisa menggunakan perintah `ls`. Perintah ini akan menampilkan semua file dan direktori yang ada di dalam direktori saat ini.

```bash
$ ls
Applications               Pictures
Applications (Parallels)   PlayOnMac's virtual drives
Calibre Library            Postman
Desktop                    Projects
Documents                  Public
Downloads                  Sandbox
Dropbox                    Screen Studio Projects
Library                    Tools
Movies                     Videos
Music                      fvm
Parallels                  go
```

Setiap perintah `ls` tentu akan berbeda-beda tergantung dari direktori mana kita berada.

## Melihat Hidden Files

Dalam sistem Linux/Unix, hidden files adalah file yang diawali dengan titik (.). File ini tidak tampil di perintah `ls` kecuali kita menambahkan flag `-a` atau `--all`.

```bash
$ ls -a
```

## Melihat Detail File

Untuk melihat detail file, kita bisa menggunakan flag `-l` atau `--long`.

```bash
$ ls -l
total 0
drwx------@   4 baguzzzaji  staff   128 Oct 18 14:07 Applications
drwxr-xr-x@   4 baguzzzaji  staff   128 Jan 19 15:41 Applications (Parallels)
drwxr-xr-x@  57 baguzzzaji  staff  1824 Sep  8 12:05 Calibre Library
drwx------+  12 baguzzzaji  staff   384 Jan 26 20:49 Desktop
drwx------@  21 baguzzzaji  staff   672 Jan 19 13:34 Documents
drwx------@  88 baguzzzaji  staff  2816 Jan 27 09:02 Downloads
```

Flag `-l` akan menampilkan informasi detail file:

- `drwx------@` adalah permission atau hak akses dari suatu file/direktori. Huruf `d` menandakan direktori, bila tidak ada `d` artinya file. 
- `4` adalah jumlah file didalamnya. 
- `baguzzzaji` adalah pemilik file.
- `staff` adalah grup pemilik file.
- `128` adalah ukuran file dalam byte.
- `Oct 18 14:07` adalah tanggal dan waktu file terakhir diubah.

## Melihat Ukuran File

Untuk melihat ukuran suatu file atau direktori, kita bisa menggunakan flag `-h` atau `--human-readable`.

```bash
$ ls -lh
total 1973360
drwxr-xr-x    7 baguzzzaji  staff   224B Jan 24 21:33 .
drwxr-x---+ 109 baguzzzaji  staff   3.4K Jan 27 09:38 ..
-rw-r--r--@   1 baguzzzaji  staff   6.0K Nov 16 22:09 .DS_Store
-rw-r--r--@   1 baguzzzaji  staff   376M Jan 24 21:42 A.mp4
-rw-r--r--@   1 baguzzzaji  staff   211M May 28  2024 B.mp4
-rw-r--r--@   1 baguzzzaji  staff   184M May 28  2024 C.mp4
-rw-r--r--@   1 baguzzzaji  staff   192M May 28  2024 D.mp4
```
