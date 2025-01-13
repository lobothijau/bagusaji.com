---
title: Konversi Gambar menjadi WebP
date: 2024-09-12
description: |
  Kali ini penulis akan membahas cara mengubah semua gambar menjadi file WebP dengan ukuran yang jauh lebih kecil tapi kualitas yang hampir sama dengan gambar asli.
tags: cli
---

Beberapa waktu yang lalu ada sebuah _project_ yang perlu melakukan konversi semua file gambar menjadi WebP. Cara yang paling cepat tentu saja lewat  _command line interface_  atau lewat terminal. Caranya tidak sulit, pertama cukup install package webp:

```
brew install webp
```

Setelah ini kita bisa memanggil perintah  `cwep`  untuk melakukan konversi gambar. Contoh sintaksnya adalah sebagai berikut:

```
cwebp gambar.png -o gambar.webp
```

Tanpa melakukan banyak konfigurasi, perintah di atas akan mengubah gambar png menjadi webp dengan ukuran yang jauh lebih kecil.

Kita juga bisa mengubah semua file yang ada di dalam suatu folder dengan memanfaatkan shell script. Buat sebuah file baru, di sini penulis beri nama  `webp.sh`. Isi file tersebut dengan kode berikut:

```
#!/bin/bash

PARAMS=('-m 6 -q 70 -mt -af -progress')

if [ $# -ne 0 ]; then
        PARAMS=$@;
fi

cd $(pwd)

shopt -s nullglob nocaseglob extglob

for FILE in *.@(jpg|jpeg|tif|tiff|png); do
    cwebp $PARAMS "$FILE" -o "${FILE%.*}".webp;
done
```

Buat file  `webp.sh`  sebagai  _executable_:

```
chmod +x webp.sh
```

Panggil script tersebut dari dalam folder yang ingin kita ubah gambar-gambar di dalamnya.

```
./webp.sh
```

Referensi: [github](https://gist.github.com/tabrindle/ed9f77b4e96f4c98b49b)