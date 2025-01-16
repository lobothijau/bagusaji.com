---
title: "Menggunakan rbenv untuk Mengelola Versi Ruby"
date: 2025-01-18
description: |
  Artikel ini membahas cara menggunakan rbenv untuk mengelola versi Ruby di Mac OS X dan Linux.
tags: ruby
---

Sistem operasi seperti Mac OS X atau Linux ada sudah terpasang Ruby secara default. Namun, akan lebih baik jika kita tidak mengganggu Ruby yang sudah ada untuk menggunakannya dalam bekerja. Seperti yang banyak disarankan oleh developer Ruby maupun Rails, kita bisa menggunakan `rbenv` agar bisa bekerja dengan versi Ruby yang kita inginkan.

## Apa itu rbenv?

Bagi pembaca yang belum tahu, [`rbenv`](https://github.com/rbenv/rbenv) adalah sebuah *tool cli* untuk mengelola instalasi versi Ruby. Dengan `rbenv` kita bisa menginstal berbagai versi Ruby dan mengganti versi Ruby yang aktif hanya lewat satu perintah secara instan. Jika pembaca familiar dengan Node.js atau Python, `rbenv` seperti `nvm` atau `pyenv` yang digunakan untuk mengelola versi Node.js dan Python.

## Instalasi rbenv di Mac OS X

1. Jika menggunakan Mac OS X, untuk bisa memasang `rbenv`, kita perlu memasang [Homebrew](https://brew.sh/) terlebih dahulu.

```bash
brew install rbenv
```

2. Jalankan perintah berikut untuk memasang Homebrew:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Jika ditanya untuk memasang Command Line Tools for Xcode, pilih "yes" untuk melanjutkan.

3. Selanjutnya kita bisa mulai memasang `rbenv` dengan perintah berikut:

```bash
brew install rbenv
```

4. Tunggu sampai proses instalasi selesai. Setelah selesai, kita lanjukan proses inisialisasi awal `rbenv` dengan menjalankan perintah berikut:

```bash
rbenv init
```

Setelah proses selesai, tutup terminal lalu buka lagi agar perubahan sebelumnya bisa aktif. 

5. Sekarang setelah rbenv terpasang dan sistem terminal sudah mengenal konfigurasinya, mari kita mulai dengan memasang Ruby versi terbaru. 

```bash
rbenv install 3.3.4
```

Perintah di atas akan mengunduh, mengompilasi, dan menginstal Ruby versi 3.3.4. Versi Ruby tersebut akan disimpan di folder `~/.rbenv/versions/`. Proess pemasangan ini akan memakan waktu beberapa menit tergantung dari kecepatan internet. 

6. Apabila sudah selesai, atur agar Ruby versi 3.3.4 (atau berapapun yang pembaca inginkan) menjadi Ruby yang aktif secara globaldengan perintah berikut:

```bash
rbenv global 3.3.4
```

Perintah di atas akan mengatur Ruby versi 3.3.4 menjadi Ruby yang aktif setiap kali kita membuka terminal.

7. Untuk memastikan bahwa Ruby versi 3.3.4 sudah aktif, kita bisa memeriksa versi Ruby yang aktif dengan perintah berikut:

```bash
ruby -v
```

Pembaca akan melihat output kurang lebih seperti berikut:

```bash
ruby 3.3.4p153 (2024-02-25 revision 73220) [arm64-darwin23]
```

Hasil di atas bisa saja sedikit berbeda tergantung dari versi Ruby yang kita pasang. 

8. Untuk melihat semua versi Ruby yang sudah terpasang, kita bisa menjalankan perintah berikut:

```bash
rbenv versions
```

## Instalasi rbenv di Linux

Pemasangan `rbenv` di Linux tidak begitu sulit. Artikel ini menganggap pembaca menggunakan sistem operasi Ubuntu. Mari kita mulai dengan memperbarui sistem Ubuntu dan memasang `dependencies` yang diperlukan olleh rbenv dan Ruby:

```bash
sudo apt-get update

sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev nodejs npm
```

Selanjutnya kita bisa memasang `rbenv` dengan perintah berikut:

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

<div class="note">
<strong><em>CATATAN:</em></strong> Kita bisa memasang rbenv dengan package resmi dari Debian atau Ubuntu, tapi versi tersebut seringkali tertinggal cukup jauh dengan versi terbaru. Oleh karena itu, untuk pemasangan di Linux, lebih disarankan untuk menggunakan cara di atas.
</div>

Perintah sebelumnya akan mengunduh source code `rbenv` dari GitHub dan menyimpannya di folder home `~/.rbenv`. Selanjutnya kita perlu menginisialisasi `rbenv` dengan perintah berikut:

```bash
~/.rbenv/bin/rbenv init
```

Tutup dan buka kembali terminal agar perubahan sebelumnya bisa aktif.

Dari sini kita bisa melanjutkan pemasangan Ruby versi terbaru dengan emngikuti langkah ke 5 dari tutorial untuk Mac OS X karena perintah-perintahnya sama persis. 

## Penutup

Demikianlah tutorial singkat mengenai pemasangan `rbenv` dan Ruby di Mac OS X dan Linux. Semoga bermanfaat.