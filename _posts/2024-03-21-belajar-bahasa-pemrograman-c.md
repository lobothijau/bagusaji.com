---
title: Belajar Bahasa Pemrograman C
date: 2024-03-21
description: Artikel ini akan membahas tentang dasar-dasar bahasa pemrograman C dan menyiapkan development environment-nya.
tags: c
---

Bahasa pemrograman C merupakan bahasa pemrograman  _general-purpose_  yang dibuat oleh Dennis Ritchie pada akhir 1960-1970an. Bahasa ini sering dipakai dalam pengembangan sistem operasi dan  _embedded system_. C juga sering dipakai sebagai pengganti bahasa pemrograman Assembly karena sintaksnya lebih mudah dan cukup efisien.

## Compiler

Bahasa C adalah  _compiled language_, artinya  _source code_  yang sudah ditulis perlu di proses untuk menjadi sebuah  _object file_  yang kemudian diproses kembali agar menjadi sebuah  _executeable_  atau  _library_. Ada beberapa compiler yang dewasa ini populer dipakai:

-   gcc
-   Clang
-   Visual C/C
-   MinGW

## Install GCC di Linux

Jika menggunakan Linux, cara termudah adalah dengan menggunakan gcc. Pada umumnya setiap distribusi Linux sudah memiliki gcc, namun jika tidak, maka jalankan perintah berikut:

```
sudo apt install build-essential

```

Perintah di atas akan memasang  _gcc toolchain_  yang dapat dipakai untuk melakukan  _compile_,  _debug_  juga menjalankan apilkasi C yang kita buat.

Untuk mencobanya, buat sebuah file kosong dengan nama  `app.c`  lalu tulis kode berikut:

```
#include <stdio.h>
int main(void)
{
      printf("Hello World!\n");
}

```

Untuk melakukan proses kompilasi dengan gcc, jalankan perintah berikut di terminal:

```
gcc app.c
```

Perintah tersebut akan membuat sebuah file dengan nama  `a.out`  di folder yang sama. Jalankan program tersebut di terminal dengan perintah:

```
./a.out
```

## Install Clang di Linux

Alternatif lain selain gcc di Linux adalah clang. Pasang Clang di sistem Linux dengan perintah:

```
sudo apt install clang
```

Untuk memproses file  `app.c`  yang sebelumnya sudah kita buat, jalankan perintah berikut:

```
clang app.c
```

Sama seperti ketika menggunakan gcc, Clang juga akan membuat sebuah file bernama  `a.out`  yang bisa dieksekusi. Untuk melihat hasilnya, jalankan perintah berikut di terminal:

```
./a.out
```

Kita bisa melakukan kompilasi dan menggunakan nama selain  `a.out`  dengan menambahkan flag  `-o`:

```
gcc app.c -o myapp
```

Untuk menjalankan aplikasi C yang sudah dikompilasi, jalankan:

```
./myapp
```

### Menggunakan MinGW di Windows

JIka menggunakan Windows, MinGW (Minimalist GNU for Windows) merupakan opsi yang paling banyak dipakai. Namun, karena tidak menggunakan Windows, penulis tidak dapat menuliskan tahapan-tahapannya. Kunjungi  [halaman resmi MinGW](https://www.mingw-w64.org/)  untuk mengunduh dan memasang  _installer_-nya.

Tahapan kompilasinya sama dengan perintah-perintah di Linux.

Di tahap belajar, pilihan  _compiler_  tidak begitu penting, lebih baik fokus pada belajar pemrograman C saja. Gunakan compiler apapun selama ia bisa memproses file yang kita buat.

Di artikel berikutnya kita akan mulai mengenal sintaks dasar pemrograman C.