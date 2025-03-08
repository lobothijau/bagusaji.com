---
title: "Menjalankan Simulator iOS Lewat Terminal"
date: 2025-03-08
description: "Artikel ini membahas cara menjalankan Simulator iOS lewat terminal command line."
tags: ios,simulator,xcode
---

Mobile developer pasti akan sering butuh menjalankan aplikasinya dengan Simulator. Membuka sebuah Simulator tidak harus lewat Xcode. Kita bisa menjalankannya lewat terminal dengan perintah:

```sh
open -a Simulator.app
```

Biasanya perintah di atas akan mengaktifkan Simulator iPhone SE (3rd Generation). 

Bila ingin mengaktifkan Simulator lain (misalnya iPhone 16 Pro), maka jalankan perintah berikut:

```sh
open -a Simulator && xcrun simctl boot 'iPhone 16 Pro'
```

Darimana mengetahui 'iPhone 16 Pro'? Cara pertama bisa dilihat lewat Xcode seperti pada gambar. 

![](/assets/images/posts/simulator-device-list.png)

Cara yang kedua dengan melihat detail lebih lengkap lewat perintah:

```sh
xcrun simctl list
```

Perintah di atas akan langsung memberikan daftar Simulator yang tersedia beserta UUID. UUID ini bisa dipakai menggantikan nama perangkatnya:

```sh
open -a Simulator && xcrun simctl boot '2532ED8B-2368-43F2-805F-F09A8F66E31D'
```

Kode UUID di atas bisa dilihat dari hasil `xcrun simctl list`. 

![](/assets/images/posts/simulator-ss.png)