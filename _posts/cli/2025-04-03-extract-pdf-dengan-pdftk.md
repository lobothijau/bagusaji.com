---
title: "Extract Dokumen PDF dengan pdftk"
date: 2025-04-03
description: "Artikel ini akan membahas tentang cara mengekstrak sebagian halaman file PDF dengan tool CLI bernama pdftk."
tags: cli
series: cli
series_order: 100
series_title: "Ekstrak Dokumen PDF dengan pdftk"
---

{% include series.liquid %}

Let say dari satu dokumen PDF yang besar (500 halaman), ada bagian yang ingin kita ekstrak, contoh kita butuh hanya halaman 103-109 saja supaya ukurannya lebih kecil dan bisa diproses lebih cepat. Bagaimana caranya? 

Salah satu trik yang bisa kita lakukan adalah dengan memanfaatkan tools `pdftk` via *command line*. 

Pertama pasang dulu `pdftk`:

```sh
$ brew install pdftk # untuk mac os
$ sudo apt install pdftk # untuk ubuntu dan sekitarnya
```

Setelah `pdftk` terpasang, lakukan proses ekstrak pdf dengan format:

```sh
$ pdftk file-lama.pdf cat 103:109 output file-baru.pdf
```

Pastikan `file-lama.pdf` ada di `working directory` saat ini. 