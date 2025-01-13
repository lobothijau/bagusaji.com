---
title: Mengubah Package Name Aplikasi Flutter
date: 2025-01-09
description: |
  Artikel ini membahas cara mengubah package name di aplikasi Flutter secara manual setelah aplikasi sudah dibuat.
tags: flutter
---

Package name merupakan identitas suatu aplikasi yang bersifat  _unique_  yang akan melekat sebagai identitas setiap aplikasi di platform Android maupun iOS. Agar aplikasi kita bisa diupload ke Play Store maupun App Store, aplikasi tersebut wajib memiliki package name yang berbeda dengan aplikasi lain. Aplikasi yang package name nya sama dengan aplikasi lain akan membuatnya tidak bisa di-install.

Bila aplikasi belum dibuat, kita bisa dengan mudah mengatur package name ataupun _bundle identifier_ saat membuat project Flutter. Caranya melakukannya adalah dengan menggunakan flag  `--org`:

```
flutter create --org com.bagusaji.aplikasi nama_folder
```

## Android

Untuk Android, buka file  `build.gradle`  di module  `app`, lalu ubah nilai dari  `applicationId`.

```
defaultConfig {
    applicationId "com.bagusaji.aplikasi"
    minSdkVersion 21
    targetSdkVersion 34
    versionCode 1
    versionName "1.0"
}
```

Aplikasi kita akan mendapatkan package name sesuai dengan yang tertulis di atas saat terpasang, namun untuk source code Android nya masih menggunakan package name bawaan (misalnya com.example.bagusaji).

## iOS

Untuk iOS, buka file Info.plist, di dalam folder  `ios/Runner`. Selanjutnya cari dan ubah nilai berikut:

```
<key>CFBundleIdentifier</key>
<string>com.bagusaji.aplikasi</string>
```

## Menggunakan Package Rename

Cara cepat lainnya yang bisa kita gunakan adalah dengan menggunakan package  [rename](https://pub.dev/packages/rename). Kita cukup memanggil package tersebut dari terminal dan akan secara otomatis melakukan perubahan disetiap tempat.

Pasang package tersebut dengan perintah:

```
pub global activate rename
```

Jalankan perintah berikut di dalam project Flutter, untuk mengubah package name:

```
pub global run rename --bundleId com.bagusaji.aplikasi --targets ios,android 
```