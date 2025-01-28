---
title: "Sekilas Tentang Relative Path"
date: 2025-01-28
description: "Artikel ini akan membahas relative path dalam sistem Linux/Unix."
tags: cli
series: cli
series_title: "Sekilas Tentang Relative Path"
series_order: 60
---

{% include series.liquid %}

Beberapa artikel yang lalu, kita sempat membahas tentang relative path saat membahas perintah `cd`. Artikel ini akan membahas relative path sedikit lagi. Perhatikan aboslute path berikut:

```bash
$ cd /home/bagusaji/Sanbox/Go/my-first-project
```

Penulisan absolute path memaksa kita untuk menulis secara eksplisit. Bila saat ini kita berada di direktori `Go/my-second-project`, menggunakan absolute path akan memakan lebih banyak waktu karena perlu menulis path yang lebih panjang. Bandingkan dengan relative path berikut:

```bash
$ pwd
/home/bagusaji/Sanbox/Go/my-second-project
$ cd ../my-first-project
```

Perintah `cd` dengan relative path di atas akan memberikan hasil yang sama dengan absolute path sebelumnya. 

## . dan ..

Relative path dalam sistem Linux/Unix memiliki dua simbol khusus, yakni `.` dan `..`. 

Simbol `.` menyatakan direktori saat ini. Sebagai contoh, jika kita berada di direktori `my-first-project`, dan mengetikkan `cd .`, maka kita akan tetap berada di direktori `my-first-project`.

Sementara itu, simbol `..` menyatakan direktori di atas direktori saat ini (atau parent directory). Sebagai contoh, jika kita berada di direktori `my-first-project`, dan mengetikkan `cd ..`, maka kita akan pindah ke direktori induk dari `my-first-project`, yakni direktori `Go` berdasarkan contoh struktur direktori di atas.

Sebetulnya tidak ada cara yang benar atau salah karena menggunakan relative path atau absolute path tetap menghasilkan cara yang sama. Namun, agar lebih efisien selalu gunakan path dengan penulisan lebih singkat. 


