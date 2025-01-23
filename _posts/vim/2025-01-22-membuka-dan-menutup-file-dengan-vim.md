---
title: "Membuka dan Menutup File dengan Vim"
date: 2025-01-22
description: Artikel ini membahas beberapa konsep dasar navigasi disebuah file dengan Vim.
tags: vim
series: vim
series_title: Belajar Vim untuk Pemula
---

Mayoritas editor lain seperti VSCode, Sublime Text, dll. ketika dibuka akan langsung memungkinkan pengguna untuk mengetik langsung ke dalam file. Sementara itu Vim memiliki empat mode yaitu normal, insert, command dan visual. Fungsi keempatnya adalah sebagai berikut:

**Normal mode** akan aktif setiap membuka Vim. Mode ini kita bisa menulis semua jenis perintah atau melakukan navigasi dan manipulasi teks. Mayoritas pengguna Vim akan lebih sering berada di mode ini. Pengguna senior akan menyarankan untuk selalu berada di mode normal saat tidak mengetik dengan menakan tombol `Esc`.

**Insert mode** digunakan untuk menuliskan teks dan akan aktif saat kita menekan tombol `i`, `a`, `o`, `I`, `A`, `O`, `s`, `S`, `c`, `C`, `R`, `r`, `v`, `V`, `esc` atau `Ctrl-R` di mode normal (karena saking banyaknya, cukup ingat tombol `i` saja untuk saat ini). Mode ini juga memungkinkan pengguna untuk menjalankan beberapa perintah. Secara default, “– INSERT –” akan ditampilkan di bagian bawah jendela Vim.

**Command mode**, mode ini digunakan untuk menjalankan perintah Vim yang akan diawali dengan `:` seperti `:set number`, `:search` atau `:filter`. Setelah perintah dijalankan, Vim akan kembali ke mode normal.

**Visual mode** digunakan memilih teks (atau istilah lainnya melakukan *seleksi* atau *blok*). Mode ini mirip dengan mode normal, tetapi perintah navigasi akan diterapkan pada area yang telah dipilih. Secara default, “– VISUAL –” akan ditampilkan di bagian bawah jendela.

## Membuka File dari Terminal

Cara termudah untuk membuka file dari terminal adalah dengan menggunakan perintah `vim` diikuti nama file yang ingin dibuka. 

```
vim <nama-file>

vim main.go
vim ./cmd/main.go
```

## Membuka File dari Dalam Vim

Menjalankan perintah `vim` tanpa memberikan nama file akan membuka Vim dalam mode normal tanpa membuka file apapun. Bila ingin membuka file lain, gunakan perintah `:e <nama-file>`. Pastikan untuk berada di mode normal dengan menekan tombol `Esc`.

```
:e main.go
:e ./cmd/main.go
:e /etc/passwd
```

*Relative path* bisa dipakai untuk mereferensikan file dari lokasi direktori terakhir kita membuka Vim. Kita juga bisa menggunakan *absolute path* untuk menentukan filenya. 

## Menutup File

Selain dengan `:q` yang pernah kita bahas di artikel sebelumnya, kita juga bisa menutup file dengan beberapa cara:

- `:wq` untuk menyimpan dan keluar
- `:x` untuk menyimpan dan keluar hanya jika ada perubahan
- `:q!` untuk keluar tanpa menyimpan perubahan

## Menyimpan File

Untuk menyimpan file juga ada beberapa cara. Cara paling dasar adalah dengan menggunakan perintah `:w` yang diambil dari kata **w**rite. Berikut ini beberapa strateginya:

- `:w` untuk menyimpan file
- `:w!` untuk memaksa menyimpan file (berguna ketika file read-only atau perlu override permissions)
- `:w app.py` untuk menyimpan ke file baru yang telah ditentukan (`save as`)
- `:w! app.py` untuk memaksa menyimpan ke file baru bila file sudah ada (*overwrite*)
- `:wq!` untuk menyimpan file dan keluar
