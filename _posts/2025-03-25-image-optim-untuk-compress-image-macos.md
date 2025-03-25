---
title: ""
date: 2025-03-25
description: "Artikel ini membahas bagaimana cara menjawab soal tes untuk menjumlahkan isi dari suatu array."
tags: javascript, interview
---

Image merupakan salah satu jenis file yang akan sangat sering diproses disebuah halaman web. Jaman sekarang, kualitas gambar menjadi semakin bagus yang berbanding lurus dengan ukurannya. Semakin besar ukuran file tentu akan berpengaruh terhadap waktu dan kecepatan internet yang dibutuhkan untuk memuatnya. 

Cara terbaik untuk menampilkan image adalah dengan melakukan kompresi data supaya ukurannya lebih kecil tapi tetap memiliki kualitas yang baik. Salah satu truk untuk kompresi gambar yang penulis lakukan terutama di sistem oprasi Mac adalah dengan aplikasi Image Optim. Aplikasi ini bisa kita pasang lewat Homebrew:

```sh
brew install imageoptim
```

Cara kerja Image Optim sangat mudah, kita cukup *drag and drop* file atau folder yang diinginkan ke aplikasi, maka aplikasi tersebut akan secara otomatis melakukan optimasi. 

![](/assets/images/posts/imageoptim.png)

Image Optim sejatinya merupakan GUI untuk berbagai tools cli seperti Zopfli, PNGOUT, OxiPNG, AdvPNG, PNGCrush, JPEGOptim, Jpegtran, Guetzli, Gifsicle, SVGO, svgcleaner dan MozJPEG. Oleh karena itu apapun yang bisa mereka lakukan, bisa juga dilaukan di Image Optim tapi lewat UI. 


