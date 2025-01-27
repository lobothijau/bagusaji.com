---
title: "Menggunakan Perintah pwd"
date: 2025-01-26
description: "Perintah pwd digunakan untuk menampilkan path direktori saat ini. Perintah ini berguna agar kita mengetahui posisi direktori saat ini dan menentukan path mana yang akan kita gunakan untuk navigasi."
tags: cli
series: cli
series_title: "Menggunakan Perintah pwd"
series_order: 20
---

{% include series.liquid %}

Untuk menguasai command line, kita harus menguasai bagaimana melakukan navigasi di dalamnya. Artikel ini akan membahas salah satu perintah paling dasar yakni `pwd`. 

Dalam konteks command line, direktori yang saat ini sedang aktif disebut dengan *current working directory*. Untuk mengetahuinya, kita bisa menggunakan perintah `pwd` tadi. 

```bash
$ pwd

/Users/bagusaji
```

Hasil yang akan pembaca dapat tentu akan berbeda dengan contoh di atas. Biasanya hasil pertama dari perintah `pwd` adalah path home. Di linux biasanya ditampilkan dengan `/home/bagusaji`, sementara itu karena penulis menggunakna Mac OS, maka hasilnya adalah `/Users/bagusaji`.

Tips, home directory memiliki simbol khusus yakni `~`. Sehingga, terkadang di beberapa terminal saat pertama kali dijalankan, kita akan melihat simbol ini yang menandakan bahwa kita berada di home directory.

![](/assets/images/cli/pwd.png)

Perintah `pwd` berguna agar kita mengetahui posisi direktori saat ini. dan menentukan path mana yang akan kita gunakan untuk navigasi, terutama bila kita ingin melakukan navigasi ke direktori lain yang relatif terhadap direktori saat ini.

