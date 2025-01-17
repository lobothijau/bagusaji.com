---
title: "Belajar Menggunakan Command Line Interface"
date: 2025-01-01
description: "Menjadi seorang programmer akan membuat kita lebih dekat dengan *command line*. Seri belajar menggunakan command line interface ini akan membantu mengenalkan pembaca dengan berbagai perintah cli."
series: cli
series_title: "Persiapan Belajar Menggunakan CLI"
favorite: true
---

{% include series.liquid %}

Menjadi seorang programmer akan membuat kita lebih dekat dengan *command line*. Ya, ada banyak tools yang bisa kita gunakan tanpa harus bersentuhan dengan *command line*, tapi menguasainya akan membuat pekerjaan kita lebih cepat dan efisien.

Sebelum *graphical user interface* (GUI) diciptakan, *command line* adalah satu-satunya cara untuk berinteraksi dengan komputer. Dengan *command line* kita tidak hanya bisa menulis program, tapi juga melakukan kompilasi, menginstall software, melakukan navigasi diantara file-file yang ada di komputer, dan lain sebagainya. Kita tetap bisa bekerja sebagai seorang programmer tanpa harus bisa menggunakan *command line*, tapi menjadi seorang programmer yang mengausai *command line* akan memberikan nilai lebih bagi kita.

Seri artikel ini akan membahas tentang *command line* dalam konteks Unix/Linux sehingga bisa dipakai untuk sistem operasi seperti Ubuntu atau Mac OS X. 

## Apa Itu Shell?

Ketika kita bekerja dengan *command line* kita sebetulnya akan berinteraksi dengan yang namanya *shell*. *Shell* adalah program yang menjadi jembatan antara kita dengan sistem operasi. *Shell* akan menerima perintah dari keyboard dan mengeksekusi perintah tersebut. Mayoritas *shell* yang ada di Unix/Linux adalah *bash* (Bourne Again SHell), tapi selain bash ada juga *zsh* (Z Shell) atau *fish* (Friendly Interactive Shell). Mac OS X sendiri sudah menggunakan zsh. 

Untuk terhubung dengan shell dari desktop, kita akan membutuhkan aplikasi khusus yang umumnya dikenal sebagai *terminal*. *Terminal* bisa datang dengan berbagai jenis aplikasi, di Ubuntu kita bisa menggunakan Gnome Terminal, di Kubuntu atau distribusi lain yang menggunakan KDE namanya Konsole, di Mac OS X namanya Terminal atau ada juga yang menggunakan iTerm 2. Kita bisa menggunakan aplikasi terminal apapun bahkan yang tidak tertulis di sini karena fungsi utama semua aplikasi tersebut sama, yaitu memberikan kita akses ke *shell*. 

Buka aplikasi terminal yang ingin pembaca gunakan, lalu perhatikan:

```bash
[bagus@bagusaji.com ~]$
```

Contoh di atas adalah apa yang dikenal sebagai *shell prompt* yang akan muncul ketika aplikasi terminal siap menerima perintah dari keyboard. Shell prompt bisa muncul dengan struktur yang berbeda-beda tergantung sistem operasi yang dipakai atau konfigurasi dari masing-masing shell. Tapi, satu hal yang biasanya akan selalu ditampilkan adalah simbol `$`. Setiap kali mengikuti tutorial yang membahas penggunaan *command line*, simbol ini menandakan perintah yang perlu ditulis ke terminal. 

<div class="note">
Apabila simbol terakhir yang ditampilkan bukan <code>$</code> tapi <code>#</code>, artinya kita sedang aktif sebagai seorang <em>superuser</em>. Superuser adalah user dengan hak akses tertinggi (disebut juga dengan <em>root</em>) yang bisa melakukan banyak hal termasuk merusak sistem itu sendiri. Berhati-hatilah saat menjalankan perintah dengan hak akses ini. 
</div>

## Mencoba Perintah Sederhana

Mari kita coba beberapa perintah sederhana yang bisa kita lakukan lewat terminal. 

Untuk melihat tanggal dan waktu saat ini, kita bisa gunakan perintah `date`. 

```bash
$ date
Fri Jan 17 11:55:03 WIB 2025
```

Untuk melihat direktori yang sedang aktif sekarang, gunakan perintah `pwd` atau *print working directory*. 

```bash
$ pwd
/Users/baguzzzaji
```

## Penutup

Pada artikel berikutnya, kita akan membahas tentang beberapa perintah lagi yang bisa dipakai untuk bekerja dengan command line. 
