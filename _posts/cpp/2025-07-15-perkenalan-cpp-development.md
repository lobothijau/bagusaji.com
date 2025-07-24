---
title: Perkenalan dengan C/C++ Development
date: 2025-07-15
description: "Kita akan mulai mengenal lingkungan development untuk bahasa pemrograman C++."
tags: cpp
series: cpp
series_title: Perkenalan dengan C/C++ Development
index: 4
favorite: true
series_order: 25
---

{% include series.liquid %}

Sebelum kita bisa menulis dan mengeksekusi program C++, kita perlu memahami bagaimana sebuah program C++ dikembangkan. Berikut diagram yang menggambarkan prosesnya secara sederhana:

![](/assets/images/cpp/Development-min.png)

## Langkah 1: Tentukan masalah yang akan diatasi

Ditahap yang pertama kita perlu menentukan masalah apa yang akan diatasi. Memikirkan ide awal akan apa program yang ingin dibuat bisa menjadi langkah termudah maupun tersulit. Tapi secara konsep, seharusnya menjadi langkah paling mudah. Semua yang kita butuhkan adalah ide yang terdefinisi dengan jelas sehingga siap untuk dipakai di proses berikutnya. 

Berikut beberapa contoh:

- "Saya ingin membuat program yang bisa menerima banyak angka lalu menghitung rata-ratanya."
- "Saya ingin membuat program yang menghasilkan labirin 2D dan memungkinkan pengguna mengeksplornya. Pengguna akan menang bila mencapat ujung labirin."
- "Saya ingin membuat program yang membaca sebuah file berisi harga saham lalu memprediksi apakah saham tersebut naik atau turun."


## Langkah 2: Tentukan bagiamana menyelesaikan masalahnya:

Pada langkah ini, kita menentukan bagaimana kita ingin menyelesaikan masalah yang kita tentukan di langkah 1.  Langkah ini pula yang mengandung *software development* paling banyak. Ada banyak solusi akan suatu masalah, namun hanya beberapa solusi yang cukup baik sementara solusi lain tidak. Seringkali saat programmer mendapat sebuah ide, mereka duduk dan langsung menulis solusi untuk masalah tersebut. Hal ini bisa menghasilkan solusi yang justru jatuh ke kategori yang buruk. 


Solusi yang baik pada umumnya mengandung beberapa hal:

- Jelas (tidak terlalu kompleks atau membingungkan).
- Terdokumentasi (terutama mengenai asumsi atau limitasinya).
- Modular, artinya bagian-bagian program tersebut bisa dipakai ulang atau diganti tampa mempengaruhi bagian lain dari program. 
- Dapat memberikan pesan error yang berguna bagi pengguna saat hal buruk terjadi. 

Saat duduk dan langsung menulis program, kita biasanya akan memikirkan "Saya akan melakukan <sesuatu>", akhirnya solusi yang diimplementasikan adalah yang paling cepat. Hasil dari proses ini bisa berupa program yang kurang baik, sulit diubah atau diperbarui nantinya atau malah punya banyak **bug**. Sebuah bug adalah *error programming* yang membuat program tidak bekerja dengan benar. 


> Istilah bug pertama kali dilakukan Thomas Edison tahun 1870an! Namun, istilah tersebut dipopulerkan pada tahun 1940 saat engineer menemukan seekor ngengat yang tersangkut di perangkat keras komputer generasi pertama saat itu yang menyebabkan konsleting. Baik buku dimana error tersebut dicatat dan ngengat yang tersangkut kini menjadi bagian dari Smithsonian Museum of American History. Lihat keduanya [di sini](https://americanhistory.si.edu/collections/nmah_334663).

Banyak penelitian mengungkapkan bahwa dalam suatu sistem software yang kompleks, hanya 10-40% waktu yang dihabiskan programmer untuk menulis program. 60-90% waktu dipakai untuk *maintenance* yang dapat terdiri atas **debugging** (memperbaiki bug), melakukan perubahan (misalnya agar bisa berjalan di OS yang baru), peningkatan kualitas (perubahan kecil untuk *usability* atau *capability*-nya, atau *internal improvement* (agar lebih andal dan mudah di *maintain*)).

Akibatnya, penting agar mengalokasikan waktu lebih di awal (sebelum mulai koding) untuk memikirkan solusi terbaik dalam mengatasi suatu masalah, asumsi-asumsi dan rencana ke depan dalam rangka menghemat banyak waktu dan menghindari kesulitan di masa depan. 

Kita akan berbicara lebih banyak tentang bagaimana mengatasi suatu permasalahan di pelajaran lain. 

## Langkah 3: Menulis Progam

Untuk menulis sebuah program, kita membutuhkan dua hal: pertama adalah pengetahuan dari sebuah bahasa pemrograman, itulah tujuan utama tutorial ini! Kedua, kita perlu sebuah *text editor* untuk menulis dan menyimpan program C++ kita. Instruksi C++ yang kita tulis ke sebuah *text editor* disebut sebagai *source code* (atau sering disingkat *code*). Kita bisa menulis program dengan *text editor* apa saja misalnya seperti notepad milik Windows atau dengan vi atau pico yang ada di Unix. 

Sebuah program yang ditulis dengan *text editor* biasa mungkin akan terlihat seperti ini:


```
#include <iostream>

int main()
{
    std::cout << "Here is some text.";
    return 0;
}
```

Namun, penulis sangat menyarankan pembaca untuk menggunakan editor yang memang didesain untuk programming (disebut *code editor*). Jangan risau jika belum punya. Kita akan bahas bagaimana cara memasang sebuah *code editor* nanti. 

Editor yang didesain untuk koding memiliki beberapa fitur yang membuat pemrograman jadi lebih mudah dilakukan, diantaranya:

- Line numbering. Penomoran baris sangat berguna karena saat terjadi error, *compiler* bisa membantu memberitahu di baris berapa hal tersebut terjadi. Tanpa editor yang menampilkan nomor baris, mencari baris tertentu akan jadi sangat merepotkan. 
- Syntax highlighting & coloring. Syntax highlighting membantu merubah warna dari berbagai bagian dari program kita agar lebih mudah mengelompokannya. 
- Font khusus dengan lebar yang sama (sering disebut sebagai `monospace font`). Font lain yang bukan untuk pemrograman terkadang sulit untuk membedakan mana angka 0 mana huruf O atau perbedaan antara angka 1 dengan l (huruf kecil dari L) atai huruf I (huruf kapital i). Font pemrgoraman yang baik akan memastiakn simbol-simbol ini berbeda secara visual supaya tidak terjadi kesalahan saat penggunaannya. Semua code editor biasanya akan memilih font ini secara otomatis, tapi text editor biasa bisa saja tidak memilikinya. 


Berikut contoh source code dengan syntax highlighting dan monospace font (line numbering tidak muncul karena di blog ini tidak diaktifkan). 


```cpp
#include <iostream>

int main()
{
    std::cout << "Here is some text.";
    return 0;
}
```

Note how much easier this is to understand than the non-highlighted version. The source code we show in this tutorial will have both line numbering and syntax highlighting to make that code easier to follow.

Perhatikan bagaimana sekarang akan lebih mudah membaca kode dengan format khusus dibandingkan teks biasa. 

> Lihat [Coding Font](https://www.codingfont.com/) and [Programming Fonts](https://www.programmingfonts.org/) untuk mencari font pemrograman yang bagus.

Banyak program C++ sederhana hanya terdiri dari satu file, tapi program C++ yang lebih kompleks bisa memiliki ratusan bahkan ribuan file.

Setiap source code yang dibuat perlu disimpan sehingga membutuhkan sebuah nama file. Program C++ tidak memiliki aturan khusus untuk penamaan file. Akan tetapi, standar yang paling umum digunakan untuk menulis program C++ adalah dengan menyimpannya ke dalam file `main.cpp`. Nama file `main` mempermudah orang menebak isi dari file tersebut, sementara akhiran `.cpp` menandakan bahwa isi file tersebut adalah kode program C++. 

Terkadang kita juga bisa menemukan file yang dinamakan sesuai nama programnya (misal `calculator.cpp`, atau `poker.cpp`). Kita juga bisa menemukan akhiran lain yang dipakai seperti `.cc` atau `.cxx`.

Setelah menulis program, langkah selanjutnya adalah mengubah source code menjadi sesuatu yang bisa dijalankan dan melihat bila program tersebut bisa dieksekusi dengan benar. Kita akan diskusikan di pelajaran selanjutnya. 

