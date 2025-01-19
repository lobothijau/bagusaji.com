---
title: Cara Menjalankan Simulator iOS di Mac Lewat Terminal
date: 2025-01-19 11:00:00 +0700
description: Artikel ini akan membahas tentang cara menjalankan Simulator iOS di Mac lewat terminal.
tags: ios
---

Sebagai mobile developer, kita akan sering membutuhkan simulator untuk menjalankan aplikasi saat development. Untuk memastikan program nantinya bisa berjalan lancar di perangkat iOS, simulator menjadi salah satu alat yang penting apalagi bila tidak memiliki perangkat asli. 

Untuk bisa menggunakan Simulator, pastikan XCode sudah terpasang dengan benar. Selanjutnya, akses menu XCode -> Open Developer Tool -> Simulator untuk menjalankan Simulator terakhir yang dibuka. 

## Cara Menjalankan Simulator iOS Lewat Terminal

Untuk menjalankan Simulator iOS lewat terminal, kita bisa menggunakan perintah berikut:

```bash
open -a Simulator
```

Perintah di atas akan membuka Simulator iOS terbaru dan yang terakhir dibuka di Mac. 

Untuk melihat semua Simulator yang sudah terpasang di Mac, kita bisa menggunakan perintah berikut:

```bash
xcrun simctl list

# Output
== Devices ==
-- iOS 17.2 --
    iPhone SE (3rd generation) (F775F87A-1FCA-4662-AE01-BB0C0BCEC5CC) (Shutdown) 
    iPhone 15 (413F845D-5FCF-46A5-8B50-7C510793A58B) (Shutdown) 
    iPhone 15 Plus (AC821250-5474-471C-938F-7ECB625F01FC) (Shutdown) 
    iPhone 15 Pro (CEE8223F-DA38-429D-B646-DDF883933EE8) (Shutdown) 
    iPhone 15 Pro Max (E6B99EA2-E27D-4F10-ACC2-A19C96191FA6) (Shutdown) 
    iPad Air (5th generation) (216791BE-392D-4F19-9004-BD1E0BB77DF7) (Shutdown) 
    iPad (10th generation) (384C6360-4E99-4D54-BF08-741BB99486AA) (Shutdown) 
    iPad mini (6th generation) (37C00AC4-6323-418D-814B-F647A6DF0BFE) (Shutdown) 
    iPad Pro (11-inch) (4th generation) (CF514886-1F38-4DAA-90E0-96E4AE2BAA8A) (Shutdown) 
    iPad Pro (12.9-inch) (6th generation) (44E9507A-85F3-4833-9BCB-F6CF7DCA1CD1) (Shutdown) 
== Device Pairs ==
```

Perintah di atas akan menampilkan semua Simulator yang sudah terpasang di Mac. Untuk memilih Simulator yang ingin kita gunakan, kita bisa menggunakan perintah berikut:

```bash
xcrun simctl boot <device-id>
```

## Cara Menghapus Simulator Lama

Untuk menghapus Simulator yang sudah tidak digunakan, kita bisa menggunakan perintah berikut:

```bash
xcrun simctl delete unavailable

# atau untuk menghapus Simulator tertentu
xcrun simctl delete <device-id>
```

## Cara Menghapus Isi Simulator

Untuk menghapus isi Simulator, kita bisa menggunakan perintah berikut:

```bash
xcrun simctl erase <device-id>
```

Perintah di atas akan menghapus isi Simulator seperti melakukan *factory reset* alias reset ke pengaturan pabrik. 

