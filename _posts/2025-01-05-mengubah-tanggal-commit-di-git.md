---
title: Mengubah Tanggal Commit di Git
date: 2025-01-05
description: "Tanggal commit di Git ternyata bisa diubah. Artikel ini membahas bagaimana cara mengubah tanggal commit di Git."
tags: git
---

Tahukah pembaca bahwa tanggal commit di Git ternyata bisa diubah? Selama 10 tahun menggunakan Git, baru hari ini saya mengetahui bahwa tanggal commit di Git ternyata bisa diubah. Bagaimana cara mengubah tanggal commit di Git?

Mengubah tanggal commit di Git bisa dilakukan dengan menggunakan perintah:

```sh
git commit --amend --date="now"
```

Perintah di atas akan memperbarui tanggal commit dengan tanggal saat ini. Jika pembaca ingin mengubah tanggal commit dengan tanggal tertentu, pembaca bisa mengganti `now` dengan tanggal yang diinginkan.

```sh
git commit --amend --date="Wed Mar 25 10:05:44 2025 +0700"
```

Perintah di atas akan memperbarui tanggal commit dengan tanggal 25 Maret 2025. Komponen pertama adalah hari, komponen kedua adalah bulan, komponen ketiga adalah tanggal, komponen keempat awaktu dalam format HH:mm:ss, dan komponen terakhir adalah zona waktu. 


