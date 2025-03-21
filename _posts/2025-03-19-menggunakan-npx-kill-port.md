---
title: "Kill Process yang Berjalan di Port Tertentu dengan npx kill-port"
date: 2025-03-19
description: "Artikel ini membahas trik untuk menutup process yang berjalan di port tertentu lewat package kill-port"
tags: nodejs,nodemon
---

Kantor baru menggunakan Express.js sebagai backend dengan beberapa script yang sudah disiapkan. Salah satu script adalah untuk menjalankan development server dengan nodemon. 

Nodemon merupakan package untuk menjalankan sebuah server Express di development agar setiap kali melakukan perubahan, server tersebut akan otomatis *restart* tanpa perlu kita tutup dan jalankan lagi. Sayangnya, entah kenapa laptop yang saya pakai setiap kali melakukan `CTRL+C` selalu saja gagal menutup process nodemon dengan sempurna. Meskipun sudah ditutup, process-nya masih jalan dan request yang dikirim lewat Postman masih mendapat response. 

Salah satu trik yang penulis temukan adalah dengan meng-kill process nya dengan perintah:

```
lsof -i:8080
```

Setelah mendapatkan ID dari process yang berjalan di port 8080, kita bisa kill process tersebut dengan perintah:

```
kill -9 <PID>
```

Ternyata, ada package npm yang menyederhanakan proses di atas yaitu kill-port. Caranya hanya dengan menjalankan perintah berikut:

```
npx kill-port 8080
```

Process nodemon yang masih berjalan di background akan ditutup dengan sempurna. Postman pun sudah tidak bisa lagi mengirimkan request. 