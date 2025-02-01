---
layout: post
title: "Melihat Tipe File dengan Perintah `file` di Linux"
description: "Artikel ini membahas cara melihat tipe file dengan perintah `file` di Linux."
date: 2025-01-28 08:00:00 +0700
tags: cli
series: cli
series_title: "Melihat Tipe File dengan Perintah `file` di Linux"
series_order: 55
---

{% include toc %}

Suatu sistem komputer akan memiliki banyak data dengan tipe yang berbeda-beda. Akan sangat membantu bila kita bisa mengetahui tipe data dari suatu file. Perintah `file` bisa kita gunakan untuk tujuan tersebut. 

```
$ file bagus.webp   
bagus.webp: RIFF (little-endian) data, Web/P image, VP8 encoding, 1080x1080, Scaling: [none]x[none], YUV color, decoders should clamp
```

Saat digunakan, perintah `file` akan menampilkan informasi dasar dari sautu file seperti contoh. 

Meskipun dari extension-nya kita bisa melihat bahwa itu adalah file webp, tapi bisa saja extension tersebut salah atau tidak sesuai dengan tipe data yang sebenarnya. 
