---
title: "Tutorial Install MySQL di Ubuntu"
date: 2024-07-02
description: |
  MySQL merupakan database management system yang paling populer sejagat, oleh karena itu tutorial ini akan membahas langkah demi langkah bagaimana cara install MySQL versi 8 di sistem operasi Ubuntu 22.04.
tags: mysql, ubuntu
---

MySQL merupakan database management system yang paling populer sejagat. Sistem database ini menggunakan Structured Query Language (SQL) untuk mengelola data di dalamnya. Meskipun bisa dipakai dengan bahasa pemrograman apapun, MySQL merupakan pasangan PHP yang paling umum dipakai. Pembaca akan sering meliaht kedua teknologi tersebut dituliskan bersama-sama.

Tutorial ini akan membahas langkah demi langkah bagaimana cara install MySQL versi 8 di sistem operasi Ubuntu 22.04 server. Setelah menyelesaikan tutorial, pembaca akan memiliki database relasional yang bisa dipakai untuk membangun suatu website.

### Langkah 1: Install MySQL

Penulis akan mengasumsikan pembaca sudah memiliki server Ubuntu 22.04 yang sudah aktif.

Update dahulu indeks  `apt`  untuk mendapatkan paket terbaru:

```
sudo apt update
```

Lalu install paket  `mysql-server`:

```
sudo apt install mysql-server
```

Pastikan service mysql berjalan dengan perintah:

```
sudo systemctl start mysql.service

```

Berikutnya, kita akan mengambankan pemasangan MySQL di server ini dengan menjalankan perintah:

```
sudo mysql_secure_installation
```

Perintah di atas akan memberikan serangkaian pertanyaan Ya/Tidak untuk melakukan beberapa perubahan.

Pertanyaan pertama adalah apakah kita ingin melakukan validasi password atau tidak. Tekan tombol  `Y`  lalu  `ENTER`  untuk melanjutkan.

```

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: Y
```

Ada tiga level validasi yaitu hanya memeriksa panjang password saja atau harus disertai validasi agar mengandung angka, huruf besar & kecil, simbol khusus dsb.

```
There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary                  file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 0
```

Jawaban terbaik tentu opsi  `STRONG/2`, tapi karena ini hanya server lokal, maka saya pilih opsi  `LOW/0`  saja. Tekan angka yang diinginkan lalu lanjutkan dengan tombol  `ENTER`.

MySQL memungkinkan adanya  _anonymous user_, siapapun bisa mengaksesnya tanpa menggunakan akun. Hapus akses ini dengan memilih  `Y`.

```
Remove anonymous users? Press y|Y for Yes, any other key for No: Y
```

Selanjutnya kita bisa menolak akses login root secara remote (harus akses root dari  `localhost`). Hal ini dilakukan untuk mencegah seseorang menebak nebak password root dari jarak jauh.

```
Disallow root login remotely? Press y|Y for Yes, any other key for No: Y
```

Setelah itu, kita bisa menghapus database bawaan bernama  `test`  yang bisa diakses semua orang karena memang dibuatkan untuk testing. Kita bisa hapus database ini. Setelah menghapus database  `test`, kita reload privilege table MySQL untuk mengaktifkan perubahan-perubahan sebelumnya.

```
Remove test database and access to it? Press y|Y for Yes, any other key for No: Y
Reload privilege tables now? Press y|Y for Yes, any other key for No: Y
```

### Membuat User Baru

Setiap pemasangan MySQL akan memberikan user bernama  `root`. User ini mendapatkan akses penuh terhadap semua yang berhubungan dengan MySQL di server ini. Sangat berbahaya menggunakan user root diluar dari kebutuhan manajemen server. Apabila nantinya kita akan membuat sebuah website yang menggunakan MySQL ini, sebaiknya buat user baru khusus untuk satu website tersebut.

Masuk ke  _prompt_ MySQL dengan perintah:

```
sudo mysql -u root -p
```

Ketikkan password sudo diikuti tombol  `ENTER`.

Setelah masuk ke dalam  _prompt_ MySQL, buat satu user baru dengan perintah  `CREATE USER`.

```
mysql> CREATE USER 'belajardikelas'@'localhost' IDENTIFIED BY 'password';
```

Pastikan password sudah sesuai dengan kebijakan password yang sebelumnya sudah di pilih.

Setelah user baru dibuat, selanjutnya atur wewenang user tersebut. Pada contoh di bawah ini user  `belajardikelas`  hanya memiliki akses ke sebuah database bernama  `belajardikelas`  pula. Langkah yang dilakukan ini bertujuan untuk berjaga-jaga apabila ada satu user/database yang bobol, maka ia tidak bisa langsung menguasai keseluruhan database MySQL.

```
mysql> GRANT PRIVILEGE ON belajardikelas TO 'belajardikelas'@'localhost';
```

Sebelumnya pastikan database tersebut sudah dibuat terlebih dahulu:

```
mysql> CREATE DATABASE belajardikelas;
```

Setiap melakukan perubahan privileges, disarankan untuk selalu menjalankan perintah  `FLUSH PRIVILEGES`. Perintah ini akan membersihkan memori dan cache MySQL di server.

```
mysql> FLUSH PRIVILEGES;
```

Selanjutnya kita bisa melakukan login dengan user dan password yang telah dibuat.

```
mysql -u belajardikelas -p
```

### Penutup

Sekarang kita sudah memiliki instalasi MySQL yang siap pakai di server Ubuntu 22.04. Kita juga sudah menyiapkan satu user dan database khusus untuk satu kebutuhan aplikasi untuk mengamankan server dari resiko kebocoran di salah satu database di masa depan.