---
title: "Konversi File .nrg ke .iso di Mac OS X"
date: 2025-01-19
description: "Artikel ini membahas bagaimana cara mengubah file .nrg menjadi .iso di Mac OS X yang juga bisa di aplikasikan di Linux."
tags: [game, macos]
---

Beberapa waktu yang lalu, saya ingin kembali memainkan game legendaris sudah sudah lama tidak saya mainkan, yaitu Pro Evolution Soccer 6 (PES 6). Dokumen yang saya dapatkan adalah file .nrg yang merupakan file ISO yang dikompres dalam format Nero. File ini tidak bisa terbaca oleh Parallels Desktop (aplikasi virtualisasi Windows). Agar file ini bisa dibuka oleh virtual CD/DVD ROM, saya perlu mengkonversi file .nrg ke .iso.

Mengubah file .nrg menjadi iso di Mac OS X dapat dilakukan dengan menggunakan tool bernama `nrg2iso`. Selain untuk Mac OS X, tool ini juga tersedia untuk Linux. Cara memasangnya sangat mudah, yaitu dengan menggunakan `Homebrew`.

```bash
brew install nrg2iso
```

Bila menggunakan Ubuntu, maka perintah yang digunakan adalah:

```bash
sudo apt-get install nrg2iso
```

Setelah itu, kita bisa langsung menggunakan tool tersebut untuk mengubah file .nrg menjadi .iso.

```bash
nrg2iso file.nrg file.iso
```

Prosesnya sangat cepat, untuk file berukurang 600-700MB, hanya membutuhkan waktu beberapa detik. 