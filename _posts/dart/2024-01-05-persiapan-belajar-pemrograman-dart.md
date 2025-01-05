---
title: "Persiapan Belajar Pemrograman Dart"
date: 2025-01-05
description: "Artikel ini membahas persiapan yang dibutuhkan untuk belajar pemrograman Dart 3.x terutama untuk menyiapkan _development environment_ yang dibutuhkan agar bisa mengikuti pembahasan pada bab-bab selanjutnya."
series: dart
series_title: "Persiapan Belajar Dart"
---

{% include series.liquid %}

Sebelum bisa menulis satu baris kode Dart, kita perlu menyiapkan perangkat lunak yang dibutuhkan. Bab ini ditulis untuk membantu pembaca menyiapkan _development environment_ yang dibutuhkan agar bisa mengikuti pembahasan pada bab-bab selanjutnya. 

## Apa Saja yang Dibutuhkan?

- Komputer atau laptop dengan spesifikasi yang cukup.
- Editor
- Flutter SDK
- Smartphone atau bisa juga menggunakan iOS Simulator dan Android emulator bila tidak memiliki perangkat smartphone. 

## Editor

Ada beberapa opsi yang bisa dipakai untuk menulis program Dart/Flutter diantaranya:

**DartPad** adalah aplikasi web yang bisa dibuka lewat browser. Web ini dikembangkan langsung oleh tim Google. Cocok untuk sekedar memeriksa potongan kode Dart, namun kurang baik untuk dipakai untuk menulis program yang lebih kompleks. Akses lewat [dartpad.com](https://dartpad.dev/). 

![](/assets/images/persiapan-belajar-pemrograman-dart/dartpad.png)

**Visual Studio Code** adalah teks editor yang cukup populer untuk menulis program dalam bahasa pemrograman apapun. Berkat _extension_ [Dart Language Support](https://dartcode.org/) menulis program Dart di editor ini menjadi lebih mudah. 

![](/assets/images/persiapan-belajar-pemrograman-dart/vscode.png)

**IntelliJ IDEA** merupakan _integrated development environment_ (IDE) yang mendukung pengembangan aplikasi Dart dengan tambahan plugin. IntelliJ merupakan basis yang dipakai oleh Android Studio, sehingga kemampuannya tidak perlu diragukan. 

![](/assets/images/persiapan-belajar-pemrograman-dart/intellij.png)

**Android Studio** merupakan editor yang dikembangkan khusus oleh Google untuk pengembangan aplikasi native Android dengan Kotlin atau Java. Namun, dengan tambahan plugin, kita bisa menggunakan Android Studio untuk pengembangan aplikasi Flutter. 

![](/assets/images/persiapan-belajar-pemrograman-dart/androidstudio.png)

**Xcode** merupakan editor _official_ dari Apple untuk pengembangan aplikasi iOS dengan Swift atau Objective C. Kita tidak bisa menggunakan Xcode untuk menuliskan program Flutter, tapi bila ingin agar program Flutter kita bisa diakses dari perangkat Apple, maka kita tetap membutuhkan Xcode. 

Untuk melewati pembahasan pada bagian pertama buku ini (Dart), penulis menyarankan penggunaa penggunaan Visual Studio Code. Selain lebih ringan, contoh-contoh program yang relatif ringkas pada bagian pertama ini akan lebih cepat dan mudah di tulis dengan VS Code.

Sementara itu, untuk pembahasan pada bagian kedua buku ini (Flutter) penulis akan menggunakan Android Studio. Pembaca tetap bisa mengikutinya dengan menggunakan VS Code, namun seluruh tangkapan layar dan contoh pada bagian kedua akan mengasumsikan penggunaan Android Studio. 

## Memasang Visual Studio Code

Visual Studio Code merupakan editor _cross-platform_, artinya ia tersedia untuk berbagai sistem operasi baik itu Windows, Linux maupun MacOS. VS Code tersedia secara gratis tanpa _embel-embel_ apapun, tidak ada batasan fitur, tidak ada batasan waktu, dan tidak ada _popup_ yang akan meminta pembelian lisensi pro. 

VS Code bisa diunduh langsung di laman [code.visualstudio.com/](https://code.visualstudio.com/). Cara memasangnya sangat mudah, cukup ikuti proses pemasangan yang standar dilakukan sama seperti aplikasi-aplikasi lain. 

Penulis yakin, pembaca akan mampu memasang Visual Studio Code secara mandiri meskipun tanpa panduan langkah demi langkah. 

## Memasang Android Studio

Flutter secara resmi mendukung tidak editor yaitu Android Studio, Visual Studio Code dan Emacs. Contoh tangkapan layar pada bagian kedua buku ini (Flutter) secara khusus menggunakan Android Studio, namun semua contoh kode tersebut tetap bisa dijalankan di Visual Studio Code tanpa perubahan apapun. 

Kunjungi laman resmi developer.android.com/studio untuk mengunduh Android Studio versi terbaru. Ketika tulisan ini dibuat, versi terakhirnya adalah **Android Studio Koala | 2024.1.1**.

![](/assets/images/persiapan-belajar-pemrograman-dart/androidstudiowebsite.png)

Panduan pemasangan Android Studio bagi Windows, MacOS, maupun Linux tersedia dalam bentuk teks maupun video tutorial di halaman [Install Android Studio](https://developer.android.com/studio/install) sehingga tidak akan penulis tulis ulang di sini. 

Setelah Android Studio terpasang, selanjutnya pasang **plugin Flutter** yang sekaligus akan menambahkan **plugin Dart** secara otomatis. Akses menu **Plugin** pada bagian sebelah kiri, klik tab **Marketplace**, lalu cari dengan kata kunci **Flutter*. 

![](/assets/images/persiapan-belajar-pemrograman-dart/androidstudioflutterplugin.png)

Klik tombol **Install** yang berwarna hijau, tunggu proses selesai lalu klik tombol **Restart IDE** yang muncul. 

Bila muncul menu baru **New Flutter Project** di jendela awal Android Studio, artinya proses pemasangan Android Studio dan *plugin Flutter* telah selesai. 

![](/assets/images/persiapan-belajar-pemrograman-dart/androidstudionewflutter.png)

## Menyiapkan Flutter SDK

Laman resmi [flutter.dev](https://flutter.dev) menawarkan file yang kita butuhkan untuk menyiapkan Flutter SDK dan memberikan langkah demi langkah yang sangat lengkap dan mudah untuk diikuti. Untuk membuat buku ini tetap ringkas, penulis tidak memberikan langkah pemasangan Flutter SDK secara lengkap, namun bila pembaca menemui kesulitan saat mengikuti panduan yang diberikan oleh **flutter.dev**, silahkan hubungi penulis untuk melakukan konsultasi tatap muka secara online atau bertanya lewat grup tanya-jawab yang telah disediakan. 

![](/assets/images/persiapan-belajar-pemrograman-dart/fluttersdk.png)

Pembaca perlu catat bahwa Flutter memiliki beberapa _release channel_ untuk distribusi versi SDK yang berbeda. Pada umumnya yang paling banyak dipakai secara luas adalah channel **beta** dan **stable**. Fitur-fitur baru yang masih dalam tahap pengujian sebelum dirilis secara resmi akan hadir lebih dulu di _channel beta_. Apabila fitur tersebut sudah teruji, barulah versi Flutter yang baru tersebut ditambahkan ke _channel stable_. 

Gunakan selalu versi **stable** untuk pengembangan aplikasi pada umumnya untuk menghindari hal-hal yang tidak diinginkan. Bila memang ada kebutuhan untuk menguji fitur baru yang belum hadir di versi **stable**, barulah gunakan versi **beta**. 

Setelah langkah-langkah di atas selesai dilewati, kita akan bisa mengakses perintah `flutter` dari _command-line_. Untuk mengetahui apakah komputer kita sudah siap untuk dipakai bertempur dengan Flutter, jalankan perintah berikut:

```sh
flutter doctor
```

![](/assets/images/persiapan-belajar-pemrograman-dart/flutterdoctor.png)

Pemasangan Flutter SDK sudah termasuk dengan Dart SDK sehingga kita tidak membutuhkan step khusus untuk menyiapkannya dan bisa langsung berkutat dengan pembahasan di bagian pertama. 

Bagi pengguna Windows, harap ketahui bahwa bagian Xcode akan selalu merah karena Apple tidak merilis Xcode diluar sistem MacOS. Meskipun tidak bisa menguji atau merilis aplikasi untuk sistem Apple (iOS dan macOS), selama bagian _Android toolchain_ mendapat centang hijau, kita tetap dapat mengembangkan aplikasi Flutter untuk perangkat Android. 
