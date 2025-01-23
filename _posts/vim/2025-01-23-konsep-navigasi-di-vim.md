---
title: "Konsep Navigasi di Vim"
date: 2025-01-22 
description: Artikel ini membahas beberapa konsep dasar navigasi disebuah file dengan Vim.
tags: vim
series: vim
series_title: Belajar Vim untuk Pemula
series_order: 30
---

{% include series.liquid %}

Bekerja dengan suatu teks tidak selamanya hanya menulis saja. Kita juga akan sering melakukan navigasi diantara baris, kolom, kata maupun kalimat. Navigasi merupakan salah satu konsep yang penting di Vim dan bisa dicapai dengan beberapa cara. 

Artikel kali ini membahas beberapa konsep dasar navigasi disebuah file dengan Vim.

## *Basic Movement*

Dihampir semua text editor, kita menggunakan tombol panah untuk bergerak diantara baris, kolom, kata maupun kalimat. Vim, memiliki caranya sendiri. 

Meskipun tombol panah masih bisa digunakan, pengguna Vim akan memanfaatkan tombol `hjkl` untuk melakukan navigasi. 

- `h` untuk bergerak ke kiri
- `j` untuk bergerak ke bawah
- `k` untuk bergerak ke atas
- `l` untuk bergerak ke kanan

Mengapa `hjkl`? Ternyata ada sejarahnya. Saat Vi dibuat (editor yang menjadi inspirasi Vim), komputer yang dipakai adalah ADM-3A. 

![](/assets/images/vim/adm3a.jpg)

Komputer ini memilki keyboard yang terintegrasi sehingga lebih pendek dan tidak memiliki tombol panah. Tombol panah disatukan dengan hjkl untuk mensiasati ukuran keyboard yang lebih pendek. 

![](/assets/images/vim/adm3ahjkl.jpg)

Selengkapnya kunjungi [blog catonmat](https://catonmat.net/why-vim-uses-hjkl-as-arrow-keys).

Pembaca pasti tidak terbiasa dengan `hjkl` diawal belajar pasti dan itu hal yang normal. Perlahan-lahan dengan semakin seringnya menggunakan Vim, pengguna akan semakin terbiasa dengan `hjkl` sebagai pengganti tombol panah. 

Kelebihan utama menggunakan `hjkl` adalah jari-jari kita tetap berada di tengah keyboard. Bila pembaca pernah mempelajari konsep mengetik 10 jari, jari telunjuk akan diam di tombol F dan J. Jika menggunakan tombol panah navigasi menjadi kurang efisien karena harus mengangkat jari dari tengah keyboard. Sementara itu, bila menggunakan `hjkl`, jari-jari kita tetap *ready* untuk mengetik. 

## *Word Movement*

*Basic movement* memungkinkan kita untuk bergerak diantara baris, kolom, kata maupun kalimat namun karakter per karakter.. Sementara itu *word movement* akan memungkinkan kita untuk bergerak diantara kata. Berikut beberapa contoh:

- `w` atau `W` untuk bergerak ke karakter pertama di kata berikutnya (_next **w**ord_)
- `b` atau `B` untuk bergerak ke kata sebelumnya (_**b**efore word_)
- `e` atau `E` untuk bergerak ke karakter terakhir di kata berikutnya (_**e**nd of word_)

Word atau kata dalam kosakata Vim merupakan kumpulan karakter tanpa spasi. 

```
Mari belajar "Vim" bersama-sama!
```

Meskipun aslinya berjumlah empat kata, tapi menurut Vim ada sembilan kata. Karakter khusus tetap dianggap sebagai sebuah kata/*word*. Dengan begitu, ketika melakukan navigasi suatu *source code* yang mengandung karakter `(){}.$` gunakan `w`, sementara itu bila bekerja dengan teks yang bukan source code, gunakan `W` untuk mengabaikan karakter khusus tersebut.

## *Scrolling*

Bila bertemu dengan file besar dengan ratusan atau ribuan baris, kita bisa menggunakan scrolling untuk memudahkan navigasi. Melakukan scrolling disuatu file bisa dilakukan dengan beberapa cara, yaitu:

1. `Ctrl + b` untuk scroll ke atas (dari `beginning` atau `backward`)
2. `Ctrl + f` untuk scroll ke bawah (dari `forward`)
3. `Ctrl + d` untuk scroll ke bawah setengah halaman (dari `down`)
4. `Ctrl + u` untuk scroll ke atas setengah halaman (dari `up`)

## Lainnya

Navigasi dasar yang perlu pembaca ketahui agar bisa menggunakan Vim sesederhana mungkin adalah sebagai berikut:     

- `gg` untuk bergerak ke baris pertama
- `G` untuk bergerak ke baris terakhir
- `0` untuk bergerak ke karakter pertama di suatu kalimat
- `^` untuk bergerak ke karakter pertama di suatu kalimat (spasi di depannya diabaikan)
- `$` untuk bergerak ke karakter terakhir di suatu kalimat
- `{` untuk bergerak ke awal kalimat sebelumnya
- `}` untuk bergerak ke awal kalimat berikutnya
- `(` untuk bergerak ke awal kalimat sebelumnya
- `)` untuk bergerak ke awal kalimat berikutnya
- `%` untuk bergerak ke diantara dua tanda kurung `()` atau `{}` atau `[]`

Umum bagi suatu source code untuk memiliki spasi kosong di awal suatu baris untuk indentasi, oleh karena itu untuk programming akan lebih sering menggunakan `^`. 