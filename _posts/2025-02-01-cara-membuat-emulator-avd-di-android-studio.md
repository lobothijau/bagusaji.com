---
layout: post
title: "Cara Membuat Android Virtual Device (AVD) alias Emulator di Android Studio"
date: 2025-02-01 08:00:00 +0700
tags: android, emulator, avd, android studio
---

Untuk menguji sebuah aplikasi Android yang sedang dibuat, kita perlu menjalankannya ke perangkat fisik atau menggunakan emulator. Emulator dalam terminologi Android disebut dengan Android Virtual Device (AVD). Artikel ini akan membahas cara membuat perangkat virtual yang bisa kita gunakan untuk menguji aplikasi Android.

## Apa itu Android Virtual Device (AVD)?

Android Virtual Device (AVD) adalah perangkat virtual yang dibuat di Android Studio. Meskipun nama resminya AVD, tapi kita akan sebut emulator saja karena inilah nama yang lebih populer. Emulator Android memiliki konfigurasi yang cukup lengkap seperti resolusi layar, ukuran memori, dan lainnya. 

Emulator akan membutuhkan memori yang cukup besar, oleh karena itu pastikan komputer kita memiliki RAM yang cukup. Bila dibutuhkan kita juga bisa membuat lebih dari satu emulator dengan konfigurasi yang berbeda.

Emulator dibuat dan dikelola lewat Android Virtual Device Manager. Ia bisa dipakai lewat Android Studio atau dari command line. 

## Membuat Emulator Baru

Untuk membuat emulator baru, kita perlu membuka Android Virtual Device Manager yang berada di sebelah kanan atas Android Studio.

![](/assets/images/posts/avd-manager-button.png)

Dari device manager, kita bisa melihat emulator yang pernah dibuat atau perangkat fisik yang terhubung ke komputer. Untuk membuat emulator baru, klik tombol `Create Virtual Device`.

![](/assets/images/posts/avd-manager-add-new.png)

Selanjutnya akan muncul jendela baru untuk meminta kita memilih model perangkat yang akan dibuat. Disini, sesuaikan pilihan dengan kebutuhan. Bila memang butuh perangkat tablet, maka pilih tablet. Hanya saja, sebagai contoh saya akan pilih Pixel 4. 

![](/assets/images/posts/avd-pixel4.png)

### Perangkat denagn Logo Play Store

Sebelum kita melanjutkan, pemabaca mungkin menyadari ada perangkat yang memiliki logo Play Store ada yang tidak. Perangkat yang memiliki logo Play Store adalah perangkat yang sudah memiliki layanan Google Services diantaranya Play Store dan Google Maps. 

Biasanya penulis akan memilih perangkat yang memiliki logo Play Store bila tidak ada kebutuhan khusus untuk sistem yang tidak memiliki layanan Google Services. 

Untuk melanjutkan proses pembuatan emulator, klik tombol `Next`.

Pada tahap selanjutnya, kita diminta memilih *system  image* atau sistem operasi untuk perangkat yang akan dibuat. Disini kita bisa memilih sistem operasi terbaru yang sudah rilis secara resmi (Android Studio juga menyediakan sistem operasi yang masih dalam tahap pengembangan). 

Tapi, pembaca juga bisa kembali menyesuaikan sistem operasi yang akan dibuat. Contoh, ada bug yang hanya muncul di Android 7, maka buatlah emulator dengan sysmte image Nougat. Bila tidak ada di tab **Recommended**, maka buka tab **Other Images** dan cari image yang diinginkan. 

Pada contoh ini, saya akan memilih Android Tiramisu. 

![](/assets/images/posts/avd-images.png)

Terakhir adalah verifikasi konfigurasi emulator. Penulis di sini biasanya hanya  menghilangkan tanda centang pada *Enable device frame* agar emulator yang dijalankan hanya berbentuk kotak (layar) saja. Klik tombol `Finish` untuk membuat emulator.

![](/assets/images/posts/avd-verify.png)


## Menjalankan Emulator

Untuk menguji apakah emulator yang kita siapkan sudah berjalan dengan baik, kita bisa menjalankannya dengan cara klik tombol `Run` yang berada di sebelah kanan emulator di jendela AVD Manager.

![](/assets/images/posts/avd-run.png)

Selain lewat tombol run di AVD Manager, kita juga bisa memilih emulator default lalu dengan tombol `Run` aplikasi yang berada di tengah atas Android Studio.

![](/assets/images/posts/avd-default.png)

Emulator yang sudah dijalankan akan terlihat seperti gambar di bawah. 

![](/assets/images/posts/avd-emulator.png)


## Menjalankan Aplikasi di Beberapa Emulator Sekaligus

Sebelumnya sempat penulis singgung bahwa kita bisa membuka emulator sekaligus menjalankan aplikasi lewat tombol yang ad adi atas tengah layar. 

![](/assets/images/posts/avd-run-app.png)

Cara di atas akan menjalankan aplikasi hanya di satu emulator yang terpilih saja. Bila sewaktu-waktu kita butuh menjalankan aplikasi di beberapa emulator, kita bisa memilih **Select Multiple Devices** yang berada di bagian bawah. 

![](/assets/images/posts/avd-default.png)

Beri tanda centang untuk setiap emulator yang ingin menjalankan aplikasi tersebut. 

![](/assets/images/posts/avd-select-multiple.png)

