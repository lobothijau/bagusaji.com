---
title: "Menghapus File dan Folder lewat CLI"
date: 2024-07-01
description: |
  Menghapus suatu file merupakan hal dasar yang perlu dilakukan seseorang. Meskipun hal yang mendasar, menghapus file lewat terminal membutuhkan sedikit pengetahuan agar tidak melakukan kesalahan yang fatal.
tags: linux, cli
---

Menghapus suatu file merupakan hal dasar yang perlu dilakukan seseorang. Meskipun hal yang mendasar, menghapus file lewat terminal membutuhkan sedikit pengetahuan agar tidak melakukan kesalahan yang fatal.

Berbeda dengan menghapus file lewat aplikasi File Manager yang akan menyimpan file ke folder Trash atau sejenis Recycle Bin saat dihapus. Menghapus file lewat terminal akan otomatis menghapus file tersebut secara permanen. Artikel ini akan membahas langkah demi langkah yang harus dilakukan untuk menghapus file lewat terminal dengan benar sehingga kita bisa menghapus file atau folder dengan aman.

### Menghapus File

Menghapus file atau folder lewat terminal bisa dilakukan dengan perintah  `rm`  kemudian diikuti dengan nama file yang diinginkan. Formatnya adalah sebagai berikut:

```
rm file1 file2 file3
```

Jika ingin menghapus semua file yang ada di dalam folder yang sedang aktif, maka gunakan simbol  _asterisk_  (`*`). Namun berhati-hatilah saat menggunakan simbol ini karena semua file akan di hapus (tapi tidak dengan folder).

```
rm *
```

Kita bisa menjadi lebih spesifik lagi dengan simbol  _asterisk_. Misalnya ingin menghapus semua file PDF saja.

```
rm *.pdf
```

### Menghapus Folder

Bila ingin menghapus folder, maka kita cukup menambahkan opsi  `-r`  sebelum nama folder.

```
rm -r namafolder
```

Terkadang ada file atau folder yang meminta konfirmasi sebelum di hapus:

```
rm * 
zsh: sure you want to delete the only file in /Users/baguzzzaji/Sandbox/ [yn]? 
```

Kita cukup menekan tombol y atau n untuk setuju menghapus atau tidak setuju.

Untuk menghindari melakukan konfirmasi kita bisa menambahkan opsi  `-f`  atau force.

```
rm -f *
```

Kita juga bisa menggunakan dua opsi sekaligus misalnya:

```
rm -rf *
```

Opsi lain untuk menghapus folder ialah dengan perintah  `rmdir`.

```
rmdir namafolder
```

Namun perlu diingat perintah  `rmdir`  hanya bisa dijalankan bila folder tersebut kosong. Apabila folder tersebut tidak kosong, maka akan muncul error:

```
rmdir: namafolder: Directory not empty
```

### Menghapus File dengan  `shred`

Sebelumnya penulis sempat menyinggung bahwa file yang dihapus dengan rm akan bersifat permanen karena tidak masuk folder  _Trash._ Tapi sebetulnya masih memungkinkan untuk mengembalikan file yang tidak sengaja terhapus meskipun tidak menjamin 100% akan kembali.

Apabila pembaca yakin ingin menghapus suatu file secara permanen, maka gunakanlah perintah  `shred`. Mekanisme  _tool_  ini akan mempersulit proses pengembalian file sehingga bisa dipastikan file yang dihapus tidak bisa dikembalikan lagi secara utuh.

Perintahnya sama dengan  `rm`  yaitu:

```
shred file1 file2 file3
```