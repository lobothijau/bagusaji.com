---
title: "Upgrade Versi MacOS di Github Actions"
date: 2025-04-22
description: "Artikel ini membahas bagaimana cara downgrade versi Xcode di macOS dari versi 16.3 ke 16.2."
tags: xcode,macos,ios,react-native
---

Kemarin saat mengirimkan sebuah PR, penulis mendapatkan error seperti ini:

![](/images/posts/macosrunner1.png)

Pada intinya mesin runner belum bisa support Swift 6, hanya Swift 4.0, 4.2 dan 5.0. Solusinya adalah dengan mengupgrade Xcode ke versi 16 supaya mendukung Swift 6. Tapi bagaimana caranya jika sistemnya itu runner github? 

Ternyata kita cukup menggunakan runner macos-15 atau yang lebih baru (sebelumnya macos-latest alias macos-14) di konfigurasi CI Github. 

```
jobs:
  build-ios:
    runs-on: macos-15
    
    steps:
      - uses: actions/checkout@v4
      - uses: kuhnroyal/flutter-fvm-config-action/config@v3
        id: fvm-config-action
      - uses: subosito/flutter-action@v2
        with:
          flutter-version: ${{ steps.fvm-config-action.outputs.FLUTTER_VERSION }}
          channel: ${{ steps.fvm-config-action.outputs.FLUTTER_CHANNEL }}
          cache: true
      
      # Add flutter doctor command here
      - name: Check Flutter configuration
        run: flutter doctor -v
```

Selain mengupgrade versi runner, penulis juga menambahkan konfigurasi untuk menajalankan perintah flutter doctor setiap kali action di jalankan. Jadi, dimasa depan ketika ada masalah kita akan selalubisa memeriksa kondisi sistem saat itu. 