---
title: Cara Convert Video File TS ke MP4 dengan Command line
date: 2025-08-01
description: Artikel ini membahas trik convert video file ts ke mp4 lewat command line
tags: cli
series: cli
series_order: 110
series_title: "Ekstrak Dokumen PDF dengan pdftk"
---

{% include series.liquid %}

Beberapa waktu yang lalu, saya mendapatkan sebuah file dengan beberapa file video berjenis `.ts`. Meskipun seharusnya VLC bisa memutarnya, tapi entah kenapa VLC yang ada di MacBook ini benar-benar tidak bisa memutarnya. 

Solusi lain ialah dengan menggunakan alternatif video player yang lain seperti Elmedia, *buuut* subtitlenya ternyata tidak punya shadow sehingga sulit sekali dibaca kalau background video-nya terang. 

Maka, solusi terkahir adalah dengan mengubah file `.ts` tadi menjadi file `.mp4`. Cara convert video file `.ts` ke `.mp4` lewat command line ternyata tidak sulit. Syaratnya kita hanya perlu memiliki ffmpeg terpasang. 

```
for f in *.ts; do ffmpeg -i "$f" -c copy "${f%.ts}.mp4"; done
```

Perintah di atas bila dijalankan di dalam suatu folder, akan membaca semua file, lalu secara otomatis membuat file `.mp4` dengan nama file yang sama dari sebuah file `.ts`. Prosesnya pun ternyata sangat cepat, bahkan tidak sampai 5 menit untuk video hampir berukuran 1GB. 

