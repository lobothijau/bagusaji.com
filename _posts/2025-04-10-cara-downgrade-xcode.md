---
title: "Cara Downgrade Xcode dari Versi 16.3 ke 16.2"
date: 2025-04-10
description: "Artikel ini membahas bagaimana cara downgrade versi Xcode di macOS dari versi 16.3 ke 16.2."
tags: xcode,macos,ios,react-native
---

Kadang versi baru tidak selamanya membawa hal baik. Banyak hal buruk yang bisa ikut hanya di rilis baru, contohnya beberapa saat lalu saat Xcode 16.3 rilis. Project React Native yang sebelumnya bisa di build, tiba-tiba jadi banyak error terkait RCT-Folly. 


![](/assets/images/posts/downgrade-xcode-1.png)

Sebuah post di [SitHub Issue React Native mengonfirmasi masalah yang hanya muncul di beberapa React Native dan di versi Xcode terbaru](https://github.com/facebook/react-native/issues/50411). Solusinya ada dua, upgrade versi React Native ke rilis terbaru atau downgrade Xcode. Penulis memilih opsi yang kedua karena opsi pertama butuh extra effort. 

## Bagaimana cara downgrade Xcode? 

Cara downgrade Xcode tidak sulit. 

Pertama, hapus atau rename Xcode yang baru (16.3) yang ada di folder `/Applications`. Bisa lewat Finder maupun *command line*. 

```
sudo rm -rf /Applications/Xcode.app
```

atau di rename jika tidak mau dihapus.

```
sudo mv /Applications/Xcode.app /Applications/Xcode-16.3.app
```

Kedua, download versi Xcode yang dibutuhkan dari https://developer.apple.com/download/all/. 

![](/assets/images/posts/downgrade-xcode-2.png)

- Pastikan sign in with Apple ID
- Cari "Xcode 16.2"
- Download file `.xip` 

Ketiga, kita pasang Xcode yang sudah di download. 

- Klik dua kali di file `.xip` untuk mendapatkan file `Xcode.app`. 
- Pindahkan ke folder `/Applications`. 

```
sudo mv ~/Downloads/Xcode.app /Applications/
```

Terakhir, aktifkan Xcode 16.2 sebagai versi Xcode yang aktif.

- Gunakan `sudo xcode-select -s /Applications/Xcode.app` untuk mengaktifkan Xcode yang baru. 
- Periksa versi yang aktif dengan perintah `xcodebuild -version`.

```
$xcodebuild -version
Xcode 16.2
Build version 16C5032a
```

