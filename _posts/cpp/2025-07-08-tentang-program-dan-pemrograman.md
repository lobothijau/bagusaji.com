---
title: Belajar Pemrograman C++ Untuk Pemula
date: 2025-07-08
description: "Artikel ini memperkenalkan tentang program dan bahasa pemrograman secara umum sebagai dasar memahami C++."
tags: cpp
series: cpp
series_title: Belajar Pemrograman C++ Untuk Pemula
index: 2
favorite: true
series_order: 15
---

{% include series.liquid %}

Komputer modern sangatlah cepat, dan terus bertambah cepat. Namun, komputer juga memiliki beberapa kekurangan: 
mereka hanya bisa memahami sejumlah instruksi yang terbatas, dan harus diberi tahu secara tepat apa yang harus dilakukan.

Sebuah program komputer adalah sebuah urutan instruksi yang mengarahkan komputer untuk 
melakukan beberapa aksi dalam tahapan tertentu. Program komputer biasanya ditulis dalam suatu bahasa pemrograman, 
yaitu bahasa yang dirancang untuk memudahkan penulisan instruksi untuk komputer. 
Ada banyak bahasa pemrograman yang tersedia, masing-masing ditujukan untuk kebutuhan yang berbeda. 
Aktivitas (dan seni) menulis program disebut pemrograman. 
Kita akan membahas lebih spesifik tentang bagaimana membuat program dalam C++ di pelajaran-pelajaran 
berikutnya.

Ketika sebuah komputer melakukan langkah-langkah yang dijelaskan oleh instruksi dalam sebuah program komputer, 
kita katakan bahwa komputer itu berjalan atau mengeksekusi program tersebut. 
Sebuah komputer tidak akan mulai mengeksekusi program sampai diberi tahu untuk melakukannya. 
Biasanya, hal ini memerlukan pengguna untuk menjalankan (atau menjalankan atau mengeksekusi yang bisa dilakukan dengan memanggil nama program lewat antarmuka teks atau klik dua kali saat menggunakan antarmuka grafis) program, 
meskipun program juga dapat dijalankan oleh program lain.

Program dijalankan pada **perangkat keras** komputer, yang terdiri dari komponen fisik yang membentuk komputer. 
Perangkat keras yang umum ditemukan pada perangkat komputasi termasuk:

- Sebuah CPU (central processing unit, sering disebut "otak" dari komputer), yang tugas aslinya adalah meneksekusi instruksi.
- Memori, dimana program komputer di muat sebelum dieksekusi.
- Perangkat interaktif (misalnya monitor, layar sentuh, keyboard atau moues) yang memungkinkan pengguna berinteraksi dengan komputer.
- Perangkat penyimpanan (misalnya hard drive, SSD, atau flash memory) yang menyimpan informasi (termasuk program yang terpasang) bahkan ketika komputer dimatikan.

Istilah software secara umum mengarah pada program pada sebuah sistem yang didesain agar bisa dieksekusi disuatu perangkat keras. 

Dalam komputasi modern, program dapat berinteraksi dengan program lain juga, bukan hanya perangkat keras. Sementara itu istilah **platform** mengacu pada sekelompok perangkat keras dan software (OS, browser, dll.) yang memberikan ruang bagi suatu software untuk berjalan. Contohnya, "PC" adalah istilah yang mengacu pada platform yang terdiri atas sebuah sistem operasi Windows dengan CPU x86. 

Platform biasanya menyediakan layanan yang bisa dipakai oleh program yang berjalan. Sebagai contoh, aplikasi desktop mungkin meminta sistem operasi memberikan mereka memori kosong, membuat file baru, atau memutar suara. Program yang berjalan tidak perlu tahu bagaimana hal ini sebenarnya difasilitasi. Jika sebuah program menggunakan layanan yang disediakan oleh platform, maka program tersebut menjadi bergantung pada platform itu, dan tidak dapat dijalankan di platform lain tanpa modifikasi. Program yang dapat dengan mudah dipindahkan dari satu platform ke platform lain dikatakan **portabel**. Tindakan memodifikasi program agar dapat berjalan di platform yang berbeda disebut **porting**.

Sekarang setelah kita membahas tentang program, mari kita diskusikan bahasa pemrograman. Kita tidak akan hanya membahas sejarah, tapi juga akan memperkenalkan terminologi yang akan muncul dalam pelajaran-pelajaran mendatang.

## Bahasa Mesin

CPU tidak dapat memahami kode yang ditulis dengan C++. Ia hanya memahami instruksi yang ditulis dalam **bahasa mesin**. Sekelompok instruksi yang dapat dimengerti oleh suatu CPU disebut sebagai **instruction set**.


Berikut contoh instruksi bahasa mesin: `10110000 01100001`.

Setiap instruksi dipahami oleh CPU sebagai sebuah perintah untuk melakukan satu tugas spesifik, misalnya "bandingkan dua angka ini", atau "salin angka ini ke lokasi memori". Dulu saat komputer pertama kali diciptakan, programmer harus menulis program langsung dengan bahasa mesin yang mana sangat sulit dan memakan waktu. 

Bagaimana cara kerja instruksi dalam bahasa mesin ini dikelola dan dipahami oleh CPU diluar pembahasan tutorial yang akan kita sama-sama pelajari ini, tapi penting juga untuk memahami bebarapa hal, diantaranya:

Satu, setiap instruksi terdiri atas sekelompok angka 1 dan 0. Setiap angka 0 dan 1 ini disebut dengan **digit biner** atau singkatnya **bit**. Panjang bit dalam instruksi sebuah bahasa mesin bisa bervariasi -- contoh, beberapa CPU memproses instruksi yang akan selalu 32 bit panjangnya, sementara ada beberapa CPU (contohnya dari keluarga x86 yang mungkin pembaca pakai) memiliki instruksi yang panjangnya bisa bervariasi.

Dua, setiap keluarga CPU yang kompatibel (contoh x86 dan arm64) memiliki bahasa mesinnya masing-masing tidak tidak bisa dipakai oleh bahasa mesin dari CPU yang lain. Artinya program yang ditulis untuk satu keluarga CPU tidak bisa dijalankan di jenis CPU yang berbeda. 

> Keluarga CPU memiliki istilah formal yaitu "instruction set architecture" (ISA). Pembaca bisa melihat daftar keluarga CPU yang tersedia di [Wikipedia](https://en.wikipedia.org/wiki/Comparison_of_instruction_set_architectures#Instruction_sets)

## Bahasa Assembly

Instruksi bahasa mesin (seperti `10110000 01100001`) ideal bagi sebuah CPU, tapi sulit diipahami manusia. Karena mayoritas program (setidaknya secara historis) selalu ditulis dan dikelola oleh manusia, masuk akal jika bahasa pemrograman haursnya didesain untuk bisa digunakan oleh manusia. 

**Bahasa assembly** (atau sering disebut assembly saja) adalah secara sederhana berfungsi sebagai bahasa mesin yang lebih mudah dibaca bagi manusia. Berikut ini kode assembly x86 untuk instruksi di atas: `mov al, 0x61`.

Karena CPU tidak mengerti bahasa assembly, program yang ditulis harus diterjemahkan ke dalam bahasa mesin sebelum bisa dieksekusi. Penerjemahan ini dilakukan oleh program yang disebut dengan **assembler**.

Sama halnya ketika setiap keluarga CPU punya bahasa mesin sendiri-sendiri, mereka juga punya variasi assembly masing-masing. Oleh karena itu, ada banyak jenis bahasa assembly di dunia ini. Meski secara konsep sama, setiap bahasa assembly memiliki sekelompok instruksi yang bisa berbeda-beda, aturan penamaan sendiri, dll. 

## Bahasa Tingkat Rendah

Bahasa mesin dan assembly dianggap sebagai bahasa tingkat rendah karena keduanya memberikan abstraksi minimal dari suatu arsitektur mesin. Dalam kata lain, bahasa pemrograman tersebut dibuat sespesifik mungkin terhadap **instruction set** sesuai arsitektur dari sistem yang akan dijalankan. 

Bahasa tingkat rendah memiliki beberapa catatan:

- Program yang ditulis dengan bahasa tingkat rendah tidak portabel. Karena bahasa tingkat rendah didesain agak spesifik terhadap **instruction set** yang dimiliki oleh suatu arsitektur, maka program yang ditulis juga spesifik terhadap suatu sistem. Melakukan porting program ke arsitektur lain tidak mudah. 

- Menulis program dengan bahasa tingkat rendah tidak mudah karena membutuhkan pengetahuan yang mendetail bukan hanya bahasanya, tapi juga arsitektur CPU nya. Contoh, perintah `mov al, 061h` memerlukan programmer untuk tahu bahwa `al` mengarah pada register CPU yang tersedia di satu platform ini saja, dan paham bagaimana memanfaatkan register tersebut. Di arsitektur yang berbeda, register ini mungkin punya nama yang berbeda, mempunya batasan yang berbeda atau malah tidak ada sama sekali. 

- Bahasa tingkat rendah sulit dimengerti. Meskipun perintah assembly masih cukup bisa dibaca, namun tetap sulit untuk memahami secara keseluruhan apa yang sebetulnya dilakukan oleh sekelompok perintah assembly. Karena program assembly umumnya memerlukan instruksi bahkan untuk tugas paling sederhana, program tersebut biasanya akan cukup panjang. 

- Sulit untuk menulis program assembly yang melakukan proses yang rumit dan kompleks karena bahasa tersebut hanya bisa memberikan fitur primitif yang terbatas. Programmer harus mengimplementasi semua fitur yang ia butuhkan sendiri. 

Keuntungan utama dari bahasa tingkat rendah adalah kecepatan. Assembly masih dipakai hari ini untuk porsi dimana performa menjadi segalanya. Bahasa ini juga dipakai dibeberapa kasus, salah satunya akan kita bahas sebentar lagi. 

## Bahasa Tingkat Tinggi

Untuk mengatasi kekurangan di atas, bahasa tingkat tinggi diciptakan seperti C, C++, dan Pascal (dan kemudian, bahasa lain seperti Java, Javascript, dan Perl). 

Berikut ini perintah yang sama dari kode assembly di atas dalam bahasa C/C++: `a = 97;`. 

Sama seperti program assembly yang harus diproses oleh assembler, program yang ditulis dalam bahasa tingkat tinggi harus diterjemahkan ke dalam bahasa mesin sebelum bisa di eksekusi. Ada dua cara utama untuk melakukannya, *compiling* dan *interpreting*. 

Program C++ umumnya di-*compile*. Sebuah **compiler** adalah program (atau sekelompok program) yang membaca kode sumber dari suatu bahasa (biasanya bahasa tingkat tinggi) dan diterjemahkan dalam bahasa lain (biasanya bahasa tingkat rendah). Contoh, *compiler* C++ menerjemahkan kode-kode C++ menjadi kode mesin. 

> Mayoritas compiler C++ juga bisa diatur untuk menghasilkan kode assembly. Cara ini berguna saat developer ingin melihat apa yang dilakukan bagian dari suatu instruksi yang spesifik. 

Kode mesin yang dihasilkan oleh *compiler* dapat dipaketkan kedalam sebuah file *executable* (berisi instruksi bahasa mesin) yang bisa didistribusikan lalu dijalankan oleh suatu sistem operasi. Mengeksekusi file *executable* tidak memerlukan *compiler*.

Pada awalnya compiler masih cukup promitif yang hanya dapat menghasilkan, kode mesin atau kode assembly yang lambat dan tidak optimal. Namun, seiring dengan berjalannya waktu, *compiler* kini menghasilkan kode yang optimal, cepat dan dalam kasus tertentu lebih baik daripada apa yang manusia bisa lakukan!

Berikut simplifikasi proses kompilasi yang dilakukan *compiler*:

![](/assets/images/cpp/Compiling-min.png)

Alternatif dari *compiler* adalah **interpreter**, sebuah program yang mengeksekusi seperangkat instruksi secara langsung dari source code tanpa melalui proses kompilasi. Interpreter biasanya lebih fleksibel daripada compiler, tapi tidak lebih efisien karena proses *interpreting* dilakukan setiap saat program ingin dijalankan. Ini artinya interpreter harus selalu terpasang disetiap mesin yang ingin menjalankan program tersebut. 

Berikut simplifikasi proses interpretasi yang diolakukan *interpreter*:

![](/assets/images/cpp/Interpreting-min.png)

> Perbandingan keuntungan dari *compiler* vs *interpreter* bisa dibaca [disini](https://stackoverflow.com/a/38491646)
> 
> Keuntungan lain dari program yang dikompilasi adalah distribusi program tersebut tidak membutuhkan distribusi *source code*. Dalam lingkungan yang tidak *open source*, hal ini bisa menjadi proteksi *intelectual property*. 

Mayoritas bahasa pemrograman tingkat tinggi ada yang dapat dikompilasi maupun di interpretasi. Bahasa seperti C, C++ atau Pascal dikompilasi, sementara bahasa *scripting* seperti Perl, JavaScript dan Python di interpretasi. Beberapa bahasa lain seperti Java menggunakan kombinasi keduanya. Kita akan mengeksplor *compiler* C++ dikesempatan mendatang.

## Keuntungan Bahasa Tingkat Tinggi

Bahasa tingkat tinggi dinamakan demikian karena mereka memberikan *high level abstraction* dari arsitektur di bawahnya. 

Mari kita lihat instruksi `a = 97;`. Instruksi ini memungkinkan kita menyimpan nilai berupa angka `97` di memori, tanpa tahu dimana lokasi memori tersebut berada, atau instruksi kode mesin apa yang perlu diberitahu ke CPU untuk menyimpan hal tersebut. Bahkan tidak ada perintah *platform-specific* di instruksi tadi. *Compiler* melakukan semua hal yang dibutuhkan oleh kode C++ tadi dalam menerjemahkannya ke dalam kode mesin yang ditujukan untuk platform tertentu. 

Bahasa tingkat tinggi memungkinkan programmer menulis program tanpa harus menguasai platform apa program tersebut berjalan. Hal ini tidak hanya memudahkan penulisan program tapi juga membuatnya relatif lebih portabel. Jika kita berhati-hati, satu program C++ akan bisa dikompilasi disemua platform yang memiliki *compiler* C++! Program yang didesain untuk bisa berjalan di berbagai platform disebut dengan **cross-platform**. 

![](/assets/images/cpp/Portability-min.png)

> Berikut ini 
>
> - Banyak sistem operasi seperti Microsoft Windows memberikan fitur *platform-specific* yang bisa dipakai di kode kita. Hal ini memudahkan proses penulisan untuk sistem operasi tertentu, atau mendapatkan integrasi yang lebih mendalam dari sistem operasi yang ditargetkan. 
> - Banyak library pihak ketiga yang hanya tersedia di platform tertentu saja. Jika menggunakannya, maka kita hanya bisa merilis program di platform yang didukung oleh library tersebut. 
> - Banyak *compiler* mendukung *extensions*, atau fitur-fitur yang hanya tersedia di compiler tertentu. Jika menggunakannya, maka program kita tidak bisa dikompiler oleh *compiler* lain yang tidak memiliki *extensions* yang sama tanpa modifikasi. Kita akan bahas hal ini setelah memasang sebuah *compiler*. 
> - Dalam beberapa kasus bahasa C++ memungkinkan ocmpiler untuk menentukan bagaimana sesuatu dapat terjadi. Topik ini akan kita bahas di bab 1. 
> 
> Jika hanya menargetkan satu platform, maka *portability* tidak menjadi hal penting. Tapi kebanyakan aplikasi dewasa ini didesain untuk mendukung banyak platform agar memperluas pasarnya. Contoh, aplikasi mobile yang ingin tersedia di iOS maupun Android. 
> 
> Bahkan bila *portability* bukan topik yang terlihat berguna, banyak aplikasi yang awalnya hanya didesain untuk satu platform (PC) akhirnya perlu di *porting* ke platform lain (Mac atau konsol) saat meraih kesuksesan atau minat. Jika tidak mulai memikirkan portability sejak awal akan ada lebih banyak tugas yang perlu dilakukan saat melakukan porting. 

Di seri tutorial ini, kita akan menghindari kode-kode yang *platform-specific* sebanyak mungkin sehingga program yang kita tulis bisa berjalan di platform manapun dengan *compiler* C++ modern. 

Keuntungan lain dari bahasa tingkat tinggi adalah:

- Mudah di baca, ditulis dan dipelajari karena cara penulisannya lebih dekat ke bahasa manusia dan matematika dan sering kita pakai sehari-hari. Dalam banyak kasus, bahasa tingkat tinggi membutuhkan instruksi yang lebih ringkas untuk melakukan tugas yang sama dengan bahasa tingkat rendah. Contoh, di C++ kita bisa menuliskan `a = b * 2 + 5;` dalam satu baris. Di assembly, instruksi tersebut akan membutuhkan 4 sampai 6 instruksi. Hal tersebut membuat program yang ditulis dengan bahasa tingkat tinggi lebih ringkas yang membuatnya lebih mudah dipahami.

- Bahasa tingkat tinggi umumnya memiliki kemampuan lebih yang membuatnya makin mudah untuk melakukan tugas-tugas programming tertentu, seperti meminta satu blok memori untuk manipulasi teks. Sebagai contoh, hanya perlu satu instruksi untuk menentukan apakah karakter "abc" ada dalam suatu teks (dan bisa iya, ada berapa teks sampai "abc" ditemukan"). Hal ini dapat mengurangi kompleksitas.

Meskipun C++ dianggap sebagai bahasa tingkat tinggi, bahasa pemrograman baru (*scripting language*) bisa memberikan abstraksi yang lebih tinggi lagi. oleh karena itu, terkadang C++ pun dianggap sebagai "bahasa tingkat rendah" meskipun kurang akurat. 

> Catatan penulis: Dewasa ini, C++ mungkin lebih akurat bila dianggap sebagai bahasa tingkat menengah. Namun, hal tersebut juga menunjukkan salah satu kelebihan utama C++: ia mampu memberikan kemampuan untuk bekerja di tingkat abstraksi yang berbeda. Kita bisa memilih mode tingkat rendah untuk mengejar performa atau bekerja ditingkat tinggi untuk mendapatkan kemudahan.
