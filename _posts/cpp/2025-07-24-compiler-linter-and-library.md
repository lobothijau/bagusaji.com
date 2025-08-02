---
title: Belajar Pemrograman C++ Untuk Pemula
date: 2025-08-02
description: "Artikel ini membahas tentang proses kompilasi, linking dan penggunaan library dalam bahasa pemrograman C++."
tags: cpp
series: cpp
series_title: Belajar Pemrograman C++ Untuk Pemula
index: 5
favorite: true
series_order: 30
---

{% include series.liquid %}

Melanjutkan diskusi dari diagram pada pembahasan sebelumnya, kita akan bahas langkah 4-7. 

![](/assets/images/cpp/Development-min.png)


## Langkah 4: Kompilasi

Untuk mengubah *source code* C++ menjadi sebuah program kita gunakan **C++ compiler**. Sebuah compiler akan membaca setiap source code (.cpp) secara berurutan lalu melakukan dua hal:

Pertama, compiler akan memeriksa bila kode C++ yang ditulis mengikuti aturan-aturan yang sudah ditentukan. Jika tidak, maka compiler akan memberikan sebuah error (dan informasi nomor barisnya) untuk memberitahu dimana masalahnya. Proses kompilasi akan dihentikan sampai error diperbaiki. 

Kedua, compiler akan menerjemahkan kode C++ menjadi instruksi bahasa mesin. Instruksi ini kemudian disimpan dalam sebuah file yang disebut sebagai **object file**. Object file berisi data lain yang diperlukan atau yang berguna bagi langkah-langkah berikutnya (termasuk data yang dibutuhkan oleh linker di step 5 dan untuk debugging di step 7). 

Object file biasanya memiliki nama file.o atau file.obj, dimana file akan mengikuti nama kode sumber file `.cpp`. 

Sebagai contoh bila program memiliki 3 file `.cpp`, maka compiler akan membuat tiga object file:

![](/assets/images/cpp/CompileSource-min.png)


Compiler C++ tersedia untuk banyak sistem operasi. Kita akan bahas bagaimana memasang compiler sebentar lagi.

## Langkah 5: Linking

Setelah proses kompilasi selesai dengan sukses, ada proses lain yang dijalankan oleh sebuah program yang disebut dengan **linker**. Tugas linker adalah mengelompokkan semua **object file** untuk menghasilkan outpul file yang diinginkan (misalnya file *executeable* yang bisa kita jalankan). Prosesnya tadi disebut dengan *linking*. Apabila ada proses *linking* yang gagal, maka **linker** akan memberikan pesan error yang memberitahukan masalahnya lalu menghentikan proses yang dilakukan. 

Linker pertama-tama akan membaca setiap *object file* yang dibuat oleh compiler untuk memastikan semuanya valid. 

Lalu, linker akan memastikan semua *dependencies* yang dibutuhkan juga bisa diakses dengan benar. Contoh, bila kita membuat sesuatu di salah satu file .cpp, lalu menggunakannya difile .cpp yang lain, linker akan mengelompokkan keduanya. Apabila linker tidak bisa mencari setiap kebutuhan tersebut, maka kita akan dapatkan *linker error*. 

Ketiga, linker biasanya akan akan mengelompokkan *library files*, koleksi dari *precompiled code* yang dipaketkan agar bisa dipakai ulang oleh program lain. 

Terkahir, linker akan menghasilkan output file yang diinginkan. Biasanya file ini merupakan file *executeable* dan bisa dijalankan (tapi bisa juga sebuah file library yang bisa dipakai program lain tergantung bagaimana kita mengatur suatu project).

![](/assets/images/cpp/LinkingObjects-min.png)

## Standard Library

C++ memiliki sesuatu yang dinamakan **C++ Standard Library** (sering disebut saja dengan "the standard library") yang merupakan fitur-fitur yang siap dipakai di program yang kita buat. Salah satu standard libary yang paling sering dipakai adalah Input/Output atau sering juga disebut dengan "iostream" dan berisi beragam fungsi untuk menampilkan teks di monitor atau menerima input dari keyboard. 

Hampir setiap program C++ pasti akan memanfaatkan standard library sehingga sangat umum untuk di linked ke program yang kita buat. Mayoritas linker C++ diatur untuk terhubung dengan standard library secara otomatis sehingga hal ini secara umum tidak perlu kita pikirkan.

## Library Pihak Ketiga

**Third party libraries** alias library pihak ketiga adalah library yang dibuat orang lalu didistribusikan sebagai produk independen (yang bukan bagian dari C++ standard library). Contoh, bila kita ingin membuat program yang memainkan suara, maka C++ standard library tidak akan memiliki fungsi tersebut. Meskipun kita bisa menulis sendiri program untuk membaca file suara, memastikan file tersebut valid, atau bagaimana memainkan data suara tersebut ke speaker, semuanya adalah pekerjaan yang akan memakan banyak waktu! Oleh karena itu, seringkali kita akan mencari jika sudah pernah ada library yang memenuhi kebutuhan tersebut sebelum menulis semuanya sendiri. 

## Building

Karena ada beberapa langkah, istilah *building* sering dipakai untuk menggambarkan keseluruhan proses mengubah file *source code* menjadi *executable* yang bisa dijalankan. File-file *executable* yang dihasilkan dari proses *building* biasa disebut sebagai **build**.

Untuk project yang kompleks, program *build automation* (seperti `make` atau `build2`) sering dipakai untuk mengotomasi proses *building* dan menjalankan *automated test*. Meskipun program seperti itu *powerful* dan *fleksibel*, karena bukan bagian dari inti dari bahasa pemrograman C++, juga tidak wajib dipakai, kita tidak akan membahasnya di seri tutorial ini. 

## Langkah 6 & 7: Testing dan Debugging

Inilah bagian paling seru! Sekarang kita sudah bisa menjalankan file *executable* dan melihat apa yang bisa ia lakukan!

Setelah program bisa dijalankan, maka bisa kita uji. Pengujian atau *testing* merupakan proses memastikan bahwa program yang dibuat berjalan seperti seharusnya. Pengujian sederhana biasanya terdiri dari memasukkan kombinasi masukan untuk melihat apakah program tersebut bisa berjalan dengan normal dengan berbagai kasus. 

Bila program tidak berjalan dengan seharusnya, maka kita harus melakukan proses **debugging**, yaitu proses mencari dan memperbaiki error dalam pemrograman. 

Kita akan diskusikan tentang *testing* dan *debugging* secara lebih detail di pembahasan mendatang. 

## Integrated development environments (IDEs)

Langkah 3, 4, 5, dan 7 semua membutuhkan progarm yang harus dipasang (*editor, compiler, linker, debugger*). Meskipun kita bisa memasang setiap program secara terpisah, ada satu paket program khusus yang dikenal dengan nama **integrated development environment (IDE)** yang sudah memiliki kesemua program tersebut. Kita akan diskusikan tentang IDE, cara memasangkan di pembahasan sesudah ini. 