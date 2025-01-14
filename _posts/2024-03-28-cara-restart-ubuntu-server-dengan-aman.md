---
title: Cara Restart Ubuntu Server dengan Aman
date: 2024-03-28
description: Artikel ini akan membahas bagaimana cara restart Ubuntu server dengan aman tanpa merusak sistem lewat command line.
tags: ubuntu
---

Restart atau reboot merupakan proses mematikan dan menyalakan sistem operasi secara otomatis. Bisa jadi karena ada update package salah satu aplikasi atau update sistem Ubuntu itu sendiri. Karena Ubuntu server tidak punya tampilan desktop, maka melakukan restart atau reboot dilakukan via command line.

## Bagaimana Cara Restart Ubuntu Server?

Cara restart ubuntu server dengan aman dapat dilakukan dengan cara memanggil perintah berikut ini:

```bash
sudo reboot
```

Atau cara rstart ubuntu server selain dengan  `reboot`  bisa juga dengan menambahkan flag  `-r`  di perintah  `shutdown`.

```bash
sudo shutdown -r now
```

Kita akan diminta password sudo sebelum sistem bisa melakukan restart.

Demikianlah cara restart Ubuntu server menggunakan command line dengan aman tanpa merusak sistem operasi.