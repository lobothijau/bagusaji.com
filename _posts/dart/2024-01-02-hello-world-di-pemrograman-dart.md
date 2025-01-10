---
title: "Hello World di Pemrograman Dart"
date: 2025-01-02
description: "Artikel ini membahas cara menjalankan program Dart sederhana dan membuat project Dart baru."
series: dart
series_title: "Hello World di Pemrograman Dart"
---

{% include series.liquid %}

Apabila diperhatikan,mayoritas lowongan pekerjaan terkait mobile development dikuasai oleh Flutter, diikuti oleh native (Kotlin/Swift) serta diikuti React Native. Melihat tren tersebut, kunci untuk memulai karir di dunia pemrograman mobile dewasa ini bisa dimulai dengan belajar pemrograman Dart. 

Seri **Belajar Pemrograman Dart 3.x** ini akan membahas tentang pemrograman Dart 3.x sebagai sebuah langkah awal bagi pembaca yang ingin memulai karir di dunia pemrograman mobile dengan Flutter. Kita akan fokus membahas konsep-konsep yang banyak dipakai oleh program-program Flutter. 

Bagi yang sudah familiar dengan bahasa pemrograman berorientasi objek atau bahasa pemrograman lain seperti Java, Kotlin, Swift, atau JavaScript, maka mempelajari Dart akan menjadi lebih mudah. Meskipun Dart memiliki keunggulan fiturnya sendiri, namun mayoritas aturan-aturan di dalamnya mirip dengan bahasa lain. Apabila Dart adalah bahasa pemrograman pertama pembaca, jangan berkecil hati. Konsep-konsep yang akan dibahas pada bagian pertama buku ini akan membantu memberikan dasar yang cukup untuk bisa mengikuti pelajaran pada bagian yang kedua. 

Dart tergolong bahasa pemrograman baru. Bahasa ini diperkenalkan pada tahun 2011 dengan rilis versi stabil yang pertama (1.0) pada tahun 2013. Pada awal perkembangannya, Dart bukan ditujukan untuk pengembangan aplikasi mobile tapi sebagai tandingan JavaScript untuk pemrograman web. Sayangnya, Dart gagal mencapai tujuan utama dan sempat terpilih sebagai bahasa pemrograman terburuk untuk dipelajari karena tidak ada tempat untuk Dart. 

Semua berubah saat Flutter datang. Flutter bukan framework _cross-platform_ mobile yang pertama. Pada saat itu sudah ada Ionic dan React Native yang berkuasa. Berkat sponsor resmi dari Google yang memasang Dart sebagai bahasa pemrograman untuk Flutter, popularitas Dart menjadi meroket. 

Dart _virtual machine_ memungkinkan proses _rebuild_ yang sangat cepat saat proses pengembangan aplikasi. Proses pengembangan yang cepat tentu harus dibarengi dengan aplikasi yang cepat pula. Sistem compiler _ahead-of-time_ memungkinkan Dart membuat aplikasi _native_ yang efisien untuk semua jenis platform. 

## Hello World!

Tradisi dalam belajar bahasa pemrograman baru adalah dengan mencetak teks **Hello, World!** ke layar. Berkat pemasangan Flutter SDK yang telah dilakukan pada bab sebelumnya, kita tidak perlu menyiapkan _environment_ khusus untuk bisa menulis dan memproses file-file Dart. 

### Menjalankan File Dart

Compiler Dart bisa membaca satu file Dart dan mengeksekusinya langsung di terminal. Siapkan folder untuk menyimpan file Dart di manapun, lalu buatlah satu file baru bernama `hello_world.dart`.

Berikutnya, tuliskan kode Dart berikut ke file tadi:

```dart
void main() {
    print("Hello, World!");
}
```

Program Dart memperbolehkan _top-level function_ seperti Kotlin. Artinya kita boleh membuat suatu fungsi tanpa memiliki sebuah `class` tidak seperti pada pemrograman java.  Mencetak sesuatu ke layar terminal dilakukan dengan fungsi `print()` dan setiap baris harus diakhiri dengan titik koma. 

Selanjutnya jalankan perintah berikut diterminal, pastikan berada di folder yang sama dengan file `hello_world.dart`. 

```
dart run hello_world.dart
```

Pembaca seharusnya akan dapat melihat teks "Hello, World!" di layar seperti pada gambar di bawah ini. 

![](/assets/images/hello-world-di-pemrograman-dart/hellodart.png)

### Membuat Project Dart

Program-program kecil seperti mayoritas contoh kode pada bagian pertama buku ini, mungkin sudah cukup dijalankan dengan cara yang telah kita pelajari sebelumnya. Akan tetapi, semakin besar project yang dibuat, mungkin pembaca perlu untuk memisahkan program dalam file-file tersendiri dan menyusun project dengan struktur yang lebih rapi. Untuk melakukan hal tersebut, disarankan untuk membuat project Dart yang utuh dengan perintah `dart create`. 

Akses folder yang diinginkan lalu jalankan perintah berikut ini di terminal. 

```
dart create hello_world
```

Perintah di atas akan membuat project kosong dengan beberapa kode standar. 

![](/assets/images/hello-world-di-pemrograman-dart/hellodartproject.png)

### Menjalankan Project Dart

Untuk menjalankan project yang sudah dibuat, masuk ke folder yang telah dibuatkan oleh perintah `dart create`:

```
cd hello_world
```

Berikutnya jalankan project ini dengan perintah:

```
dart run bin/hello_world.dart
```

Pembaca akan melihat teks **Hello world: 42!** yang dibuatkan oleh `create`. Perintah `run` bersifat opsional, kita bisa menjalankan program Dart tanpa perintah ini. 

```
dart bin/hello_world.dart
```
### Membuat Project Dart dengan Visual Studio Code

Visual Studio Code bisa membuatkan project Dart baru untuk kita bila sudah dipasangkan ekstensi **Dart language support**. 

Buka jendela Visual Studio Code lalu buka menu **Extensions** (1), tuliskan kata kunci **dart** di kotak pencarian kemudian pilih hasil teratas (2 & 3), terakhir klik tombol **Install** (4). Restart jendela Visual Studio Code bila diperlukan.

![](/assets/images/hello-world-di-pemrograman-dart/vscodeext.png)

Untuk membuat project Dart baru lewat Visual Studio Code, tekan tombol **Cmd + Shift + P** di MacOS atau **Ctrl + Shift + P** di Windows untuk memunculkan **Command Palette**. Pada popup yang muncul tuliskan dart. 

![](/assets/images/hello-world-di-pemrograman-dart/cmdpallette.png)

Pastikan memilih opsi **New project** lalu di menu berikutnya pilih **Console Application**. 

![](/assets/images/hello-world-di-pemrograman-dart/consoleapp.png)

Visual Studio Code akan meminta kita memilih folder tempat menyimpan project baru. Klik tombol **Select a folder to create the project in** bila telah selesai memilih. 

![](/assets/images/hello-world-di-pemrograman-dart/chooseafolder.png)

Langkah selanjutnya adalah memberikan nama project. Karena sebelumnya sudah membuat project lewat terminal bernama `hello_world`, maka di sini penulis membuat project baru bernama `hello_dart`. 

![](/assets/images/hello-world-di-pemrograman-dart/projectname.png)

Pastikan menggunakan huruf kecil untuk nama project dengan simbol `_` bila ingin memisahkan masing-masing kata. Jangan menggunakan simbol lain seperti `-`. 

![Struktur project baru yang dibuat dengan VS Code](/assets/images/hello-world-di-pemrograman-dart/projectname.png)

Visual Studio Code akan memuat folder berisi project Dart yang baru. Kita bisa menjalankan project ini langsung dari jendela VS Code lewat menu **Run and Debug**. 


![Menjalankan project langsung dari VS Code](/assets/images/hello-world-di-pemrograman-dart/projectname.png)

## Struktur Project Dart

Project yang dibuatkan baik oleh perintah `dart create` maupun Visual Studio Code akan memiliki struktur seperti pada gambar. 

![Menjalankan project langsung dari VS Code](/assets/images/hello-world-di-pemrograman-dart/structure.png)

Tujuan masing-masing file/folder di atas adalah sebagai berikut:

- **.dart_tool**: berisi pengaturan yang dibutuhkan oleh *compiler* Dart.
- **.gitignore**: memberitahukan Git file-file apa saja yang tidak perlu di simpan di repository sehingga tidak ikut di upload ke Github atau yang sejenisnya. 
- **analysis_option.yaml**: menyimpan pengaturan untuk melakukan sebuah proses bernama **linting** yang secara singkat dipakai mendeteksi kesalahan penulisan program sebelum di *compile*. 
- **bin**: berisi kode Dart yang bisa di ekeskusi. 
- **hello_dart.dart**: merupakan program utama yang akan dieksekusi. 
- **lib**: berisi banyak file .dart yang bisa dipakai diberbagai tempat atau di rilis sebagai sebuah *library*. 
- **pubspec.yaml**: berisi dependensi terhadap *library* pihak ketiga yang ingin dipakai di project ini. 
- **pubspec.lock**: file yang memastikan nomor versi dari _library_ yang tertulis di `pubspec.yaml` oleh project ini. 
- **README.md**: file yang mendeskripsikan tentang project ini. Tidak berelasi langsung dengan Dart/Flutter, lebih sebagai informasi bagi developer lain. 
- **test**: berisi file-file untuk melakukan *testing*. 