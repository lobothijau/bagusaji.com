---
title: Mengenal Activity Lifecycle di Android
date: 2024-03-16
description: Artikel ini akan membahas tentang apa itu Activity Lifecycle dan cara kerjanya di sebuah aplikasi Android.
tags: android
---

Sebagai sebuah perangkat dengan daya yang terbatas, sistem Android perlu memastikan bahwa penggunaan sumber daya yang terbatas ini dikelola dengan efektif agar sistem operasi beserta aplikasi yang lain dapat berjalan baik. Agar bisa mengelola sumber daya yang tersedia, sistem Android memiliki kontrol penuh atas  _lifecycle_  (siklus hidup) sebuah aplikasi serta komponen-komponen yang membangunnya termasuk di dalamnya, Activity.

Penting bagi seorang developer untuk memahami  _lifecycle_  Activity dan Application agar bisa mengelola data internal aplikasi dengan baik.

## Status Aplikasi Android

Sebuah aplikasi Android saat dijalankan oleh user akan diproses sebagai sebuah  **Process**. Dalam sistem Android, status dari sebuah process dapat berupa:

-   Foreground Process
-   Visible Process
-   Service Process
-   Background Process
-   Empty Process

Sistem Android akan memberikan prioritas sesuai dengan urutan di atas.

### Foreground Process

Foreground process adalah istilah yang diberikan pada aplikasi yang saat ini sedang berjalan dan tampil di hadapan user. Dengan  _split screen_, hanya memungkinkan ada dua aplikasi yang bisa terlihat berjalan bersamaan (meskipun hanya akan ada satu yang aktif). Karena secara visual terlihat langsung oleh user dan kemungkinan user sedang berinteraksi dengan aplikasi ini,  _foreground process_  mendapatkan prioritas tertinggi.

### Visible Process

Visible process merupakan aplikasi yang terlihat namun user sedang tidak berinteraksi dengan aplikasi tersebut. Contohnya adalah saat menjalankan mode  _split screen_. Contoh lain, misalnya ada Activity yang sedang berjalan, tapi sedang menampilkan sebuah dialog. Activity yang sedang menampilkan dialog ini tidak aktif, tapi masih mendapat status sebagai visible Activity.

### Service Process

Android dapat memiliki suatu Service, sebuah konsep untuk menjalankan kode yang tidak memiliki UI. Service yang sudah dimulai dan sedang berlangsung akan mendapatkan status ini.

### Background Process

Bagi aplikasi yang sedang aktif tapi tidak terlihat bagi user dan tidak memiliki Service yang sedang berjalan akan mendapat status sebagai  _background process_. Setiap process yang berada di status ini memiliki resiko dibersihkan dari memory saat sistem perlu memprioritaskan process lain. Android memiliki mekanisme untuk menutup process di background yang paling jarang dipakai terlebih dahulu.

### Empty Process

Process yang masih aktif di memory tapi tidak memiliki activity, service atau komponen lain yang aktif disebut sebagai empty process. Process ini tetap berada di memory agar bisa tetap siap untuk mengelola komponen lain yang akan dijalankan (anggap sebagai sebuah  _cache_  di memory).

## Activity Lifecycle

Pembahasan lifecycle dari sebuah Activity akan membutuhkan bab tersendiri, tapi di artikel ini kita akan bahas konsep utamanya saja.

Saat sebuah aplikasi dibuka, Activity pertama yang dimiliki oleh aplikasi tersebut akan di-pushed sebagai item pertama di dalam  **activity back stack**. Aplikasi yang berada paling atas disebut sebagai  _active_  atau  _running_  Activity. Saat akan menampilkan Activity yang baru, maka Activity tersebut akan ditempatkan di atas Activity yang pertama. Apabila user menutup  _active_  Activity, misalnya dengan tombol “Back”, maka yang akan ditampilkan adalah Activity yang berada di bawahnya. Dalam istilah pemrograman, activity back stack ini menggunakan konsep Last-In-First-Out (LIFO).

Ilustrasi back stack suatu aplikasi dapat dilihat pada gambar berikut:

![Sumber: Android Developer](/assets/images/posts/DraggedImage-2.png)

Sumber: Android Developer

### Status Activity

Ada beberapa status yang dapat mendeskripsikan aktivitas dari suatu Activity, yaitu:

-   **Active/Running**: Activity yang berada paling atas di dalam stack, yang tampilannya sedang terlihat dan user sedang aktif menggunakannya. Activity ini hampir tidak akan ditutup paksa saat kekurangan memori.
-   **Paused**: Activity yang tampil tapi user tidak sedang menggunakannya (contoh saat ada dialog yang muncul). Activity yang berada dalam status  _paused_  akan tetap ada di memory karena umumnya akan segera dikembalikan pada status active kembali.
-   **Stopped**: Activity yang sudah tidak terlihat berada dalam status  _stopped_, contohnya saat user mengklik tombol “Home” atau membuka aplikasi lain. Activity ini akan terus menyimpan informasi di dalamnya, namun beresiko untuk ditutup saat sistem kekurangan memori.
-   **Killed**: Activity dengan status  _stopped_, akan ditutup oleh sistem untuk membersihkan memori sehingga bisa dipakai aplikasi lain. Bila Activity tersebut dibuka lagi, maka akan kembali dimulai dari awal (aktivitas user akan menghilang kecuali di simpan ke database).

## Configuration Changes

Saat user mengubah rotasi layar dari portrait ke landscape atau mengubah pengaturan font, Activity akan di tutup dan dibuat ulang oleh sistem. Saat sistem mentutup dan memuat ulang sebuah Activity karena perubahan pengaturan ini disebut dengan  _configuration changes_. Karena mengubah pengaturan font tidak akan aktif sampai user memuat ulang aplikasi, maka sistem Android yang akan memaksa proses configuration changes ini terjadi supaya perubahan tersebut bisa langsung diaplikasikan tanpa menutup aplikasi secara manual.

Karena sistem Android yang memaksa proses pemuatan ulang Activity ini, ada kemungkinan user akan kehilangan sebagian data. Contohnya, saat scrolling apps,  _configuration change_  terjadi, kita kembali ke posisi awal, padahal scrolling sudah jauh ke bawah. Bagi sebagian user, behavior ini cukup menjengkelkan karena sudah jauh-jauh scrolling, malah kembali lagi ke awal. Bagaimana cara mengatasi  _configuration change_  akan kita bahas di artikel-artikel mendatang.