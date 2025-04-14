---
title: "Menghapus Folder node_modules dari Repository Git"
date: 2025-04-14
description: "Artikel ini membahas bagaimana cara menghapus folder node_modules dari repository git."
tags: git,cli
---

Hari ini penulis tidak sengaja mancatatkan node_modules ke project yang digenerate dengan VuePress. Ternyata project yang dibuat dengan VuePress CLI tidak memiliki file `.gitignore`. Alhasil sekian MB data harus terpakai dan ikut terupload ke GitHub. Maka di kesempatan kali ini penulis akan membahas cara menghapus folder node_modules dari repository Git. 

Langkah pertama, buat file `.gitignore` dan tambahkan folder node_modules` (contoh):

```
node_modules // pastikan tambahkan folder ini

# VitePress specific
.vitepress/dist
.vitepress/cache
.vitepress/.temp

# Vite
.vite

# konfigurasi lainnya

```

Langkah kedua, hapus node_modules dari pencatatan Git. Perhatikan bahwa untuk menghapusnya harus pakai `git rm` ya bukan dengan perintah `rm`:

```
git rm -r --cached node_modules
```

Selanjutnya, lakukan commit untuk memperbarui gitignore dan juga menghilangkan history node_modules. 

```
git commit -m "Hapus node_modules dari pencatatan Git"
```

Terakhir, push perubahan supaya folder di server Github juga dihapus. 

```
git push
```

Setelah melalui langkah-langkah di atas, folder node_modules akan diabaikan oleh Git dan tidak akan ikut di-commit. Siapapun yang mengkloning atau melakukan pull tidak perlu mengunduh folder tersebut dan cukup menjalankan `npm install` untuk mendapatkannya. 