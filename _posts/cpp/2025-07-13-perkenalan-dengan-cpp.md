
---
title: Perkenalan dengan C/C++
date: 2025-07-08
description: "Artikel ini memperkenalkan tentang bahasa pemrograman C dan C++ secara singkat."
tags: cpp
series: cpp
series_title: Belajar Pemrograman C++ Untuk Pemula
index: 1
favorite: true
series_order: 20
---

## Sebelum C++, Ada C

Bahasa C dikembangkan tahun 1972 oleh Dennis Ritchie di laboratorium Bell Telephone sebagai bahsa pemrograman sistem (bahasa untuk menulis sistem operasi). Tujuan utama Ritchie pada waktu itu adalah untuk menghasilkan bahasa yang minimalis yang mudah di kompilasi, memungkinkan akses yang efisien ke memori, menghasilkan kode yang efisien serta *self-contained* (tidak bergantung pada program lain). Untuk sebuah bahasa tingkat tinggi, C didesain agar memberikan kontrol yang luas pada programmer, sementara memungkinkan mereka untuk bisa menulis program yang bisa berjalan di berbagai platform. 

Bahasa C akhirnya menjadi sangat efisien dan fleksibel sehinggai pada tahun 1973, Ritchie dan Ken Thompson menulis ulang sistem operasi Unix dengan menggunakan C. Kebanyakan sistem operasi sebelumnya ditulis dengan assembly. Tidak seperti assembly yang menghasilkan progam yang hanya dapat berjalan di CPU tertentu, C memiliki portabilitas yang sangat baik, memungkinkan Unix untuk dikompilasi ulang untuk berbagai jenis komputer sehingga adopsinya menjadi semakin luas. C dan Unix ditakdirkan untuk bersama, popularitas C menjadi bagian dari popularitas Unix sebagai sebuah sistem operasi. 

Pada tahun 1978, Brian Kernighan dan Dennis Ritchie mempublikasikan sebuah buku berjudul "The C Programming Language". Buku ini yang kemudian dikenal sebagai K&R (inisial dari nama belakang keduanya), memberikan speisfikasi tidak resmi yang menjadi standar *de facto*. Saat portabilitas maksimum menjadi tujuan, programmer akan mengikut rekomendasi-rekomendasi di K&R karena mayoritas *compiler pada wkatu itu mengikuti standar mereka. 

Pada tahun 1983, American National Standards Institute (ANSI) membentuk semua komite yang bertugas menyusun standar resmi bagi bahasa C. Kemudian pada tahun 1989, komite ini menyelesaikan standar mereka yang disebut dengan *C89 standard* atau sering juga disebut sebagai ANSI C. Lalu pada tahun 1990, International Organization for Standardization (ISO) mengadopsi ANSI C (dengan beberapa modifikasi minor). Versi ini kemudian dikenal sebagai C90. Compiler pada akhirnya mengikuti standar ANSI C/C90 dan program yang menargetkan portabilitas maksimum akan ditulis mengikut standar yang baru ini. 

Kemudian pada tahun 1999, komite ISO merilis standar baru C yang secara informal disebut sebagai C99. C99 mengadopsi banyak fitur baru yang masuk ke banyak *compiler* sebagai sebuah *extension* atau kemudian diimplementasikan dalam C++. 

# C++

C++ (dibaca "si plus plus") dikembangkan oleh Bjarne Stroustrup di Bell Labs sebagai perluasan dari bahasa C pada tahun 1979. C++ menambahkan banyak fitur baru ke bahasa C dan sering dianggap sebagai *superset* dari C meskipun tidak sepenuhnya benar (karena C99 memiliki beberapa fitur yang tidak ada di C++). Inovasi yang paling menonjol dari C++ adalah dukungan terhadap pemrograman berorientasi objek. Tentang apa itu "object" dan bagaimana ia berbeda dari metode pemrograman tradisional akan kita bahas di bab terpisah. 

C++ distandarkan pada tahun 1998 oleh komite ISO. Ini artinya komite ISO menyetujui sebuah dokumen yang memberikan deskripsi formal tengang bahasa pemrograman C+=. Tujuan dari sebuah standarisasi tersebut ialah untuk membantu memastikan bahwa kode C++ bekerja secara konsisten di *compiler* maupun *platform* manapun. 

Sebuah pembaruan terhadap standar C++ dirilis pada tahun 2003 (atau secara tidak resmi bernama C++03). 

Lima pembaruan besar dirilis sejak 2003 yaitu C++11, C++14, C++17, C++20 dan C++23, masing-masing membawa fungsi-fungsi tambahan. C++11 sendiri mebawa begitu banyak kemampuan baru sehingga dianggap sebagai dasar baru bagi bahasa ini. Pembaruan berikutnya untuk bahasa ini diharapkan akan datang setiap tiga tahun sekali.
 
Karena nama resmi biasanya sangat kompleks (nama resmi C++20 yang lengkap adalah ISO/IEC 14882:2020), maka penamaan standar biasanya mengikuti penamaan tidak resmi yaitu mengikuti dua angka terakhir dari tahun publikasi (atau target publikasi). Misalnya, C++ mengacu pada standar yang dipublikasikan tahun 2020. 

## Filosofi C dan C++

Filosofi desain yang mendasari C dan C++ dapat dirangkum sebagai "percayakan pada programmer" -- ini bisa menjadi hal yang luar biasa sekaligus berbahaya. C++ didesain untuk memberikan programmer kebebasan tertinggi untuk melakukan apa yang mereka inginkan. Namun, ini juga berarti bahasa ini sering kali tidak akan mencegah mereka melakukan hal-hal yang tidak masuk akal, karena ia akan menganggap programmer melakukannya untuk suatu alasan tertentu. Ada cukup banyak jebakan yang mungkin dihadapi programmer pemula jika tidak waspada. Ini adalah salah satu alasan utama mengapa mengetahui apa yang tidak boleh dilakukan di C/C++ hampir sama pentingnya dengan mengetahui apa yang harus dilakukan. 

## Keunggulan C++ 

C++ unggul dalam situasi dimana performa tinggi dan kontrol penuh akan memori dibutuhkan. Berikut beberapa jenis aplikasi akan mendapatkan keuntungan lebih dari C++:

- Video games
- Real-time systems (misalnya untuk transportasi, *manufacture*, dll.)
- High-performance financial applications (misalnya untuk *high frequency trading*)
- Graphical applications dan simulasi
- Aplikasi Productivity / office
- Embedded software
- Audio dan video processing
- Artificial intelligence dan neural networks

C++ juga memiliki library pihak ketiga yang besar dan berkualitas sehingga bisa mempercepat waktu development secara signifikan.

## Bukankan C++ Sudah Mati?

Jelas tidak. Survei menunjukkan secara konsisten bahwa C++ merupakan bahasa nomor dua atau tiga dari *compiled language* didunia (dibelakang Java dan terkadang C#), atau peringkat kelima atau keenam secara umum (diluar HTML, SQL dan shell scripting). 

C++ adalah salah satu bahasa paling populer untuk mulai belajar pemrograman berkat sumber belajar yang melimpah dan komunitas yang besar dan banyaknya kampus yang mengajarkannya. 

Dengan bahasa yang terus diperbarui setiap tiga tahun, banyak library pihak ketiga yang dihasilkan menjadi sangat besar dan dominasi di industri video game membuat C++ akan terus berjaya. 

## Apakah Harus Tahu C Sebelum Belajar C++?

Tidak! Kita boleh mulai belajar langsung dengan C++, seri tutorial ini akan mengajarkan semua yang pembaca perlu tahu (dan hal yang perlu dihindari) selama proses belajar. 

Jika sudah menguasai C++, akan lebih mudah untuk belajar standar C bila memang diperlukan. Dewasa ini, C mayoritas dipakai untuk kasus yang sangat jarang, kode yang berjalan di *embedded device*, saat ebrinteraksi dengan bahasa lain yang hanya bisa dilakukan lewat bahasa C, dll. Secara umum, C++ akan lebih direkomendasikan. 

