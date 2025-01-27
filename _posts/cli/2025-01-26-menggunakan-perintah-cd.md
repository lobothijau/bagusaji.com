---
title: "Menggunakan Perintah cd"
date: 2025-01-26
description: "Perintah cd digunakan untuk pindah ke direktori lain dan wajib kita kuasai untuk melakukan navigasi di dalam command line."
tags: cli
series: cli
series_title: "Menggunakan Perintah cd"
series_order: 40
---

{% include series.liquid %}

Untuk pindah dari satu direktori ke direktori lain, kita bisa menggunakan perintah `cd` alias *change directory*. Untuk menggunakannya, kita cukup mengetikkan perintah `cd` diikuti dengan path direktori yang ingin kita tuju. Penulis path bisa dilakukan dalam dua cara, yakni dengan *absolute path* dan *relative path*.

## Menggunakan Absolute Path

Absolute path adalah path yang dimulai dari root directory diikuti dengan direktori yang ingin kita tuju satu per satu hingga mencapai direktori tujuan. Contoh, untuk pindah ke direktori `Videos` di home directory, kita bisa menggunakan perintah `cd /home/bagusaji/Videos`. 

Diawali oleh `/` yang menandakan root directory, diikuti dengan direktori `home` yang ada di dalam root directory, diikuti oleh direktori `bagusaji` yang herada di dalam direktori `home`, dan terakhir adalah direktori `Videos` yang berada di dalam direktori `bagusaji`.

## Menggunakan Relative Path

Absolute path akan memiliki selalu sama darimanapun kita mengaksesnya karena kita sudah tentukan secara eksplisit, bahwa lokasinya ada di dalam root directory, diikuti oleh subdirektori lainnya. 

Relative path adalah path yang dimulai dari direktori saat ini. Path ini akan berbeda-beda tergantung dari direktori mana kita berada. Contoh, jika kita berada di direktori `Documents`, dan ingin pindah ke direktori `Videos`, kita bisa menggunakan perintah `cd Videos`. 

Bila *current working directory* berada di dalam subdirektori `js` pada contoh struktur di bawah, dan kita ingin pindah ke direktori `video`, kita bisa menggunakan perintah `cd ../video`.

```
.
└── assets
    ├── css
    ├── fonts
    ├── img
    ├── js
    ├── video
    └── webfonts
```

Simbol `..` menandakan direktori di atas direktori saat ini. Jadi, `cd ..` akan membawa kita ke direktori assets, lalu agar langsung masuk ke direktori `video`, kita bisa melengkapi perintahnya `cd ../video`. Atau bisa juga dilakukan dua kali:

```bash
$ cd ..
$ cd video
```

