---
title: Mengatur Vertical Alignment Tabel HTML
date: 2024-10-01
description: |
  Artikel ini membahas cara mengatur vertical alignment sebuah kolom di tabel HTML agar teks tidak berada di tengah secara otomatis
tags: html
---

Beberapa waktu yang lalu, saya baru mengetahui bahwa default vertical alignment sebuah kolom di tabel HTML, ternyata menggunakan  **center**. Cukup mind blowing karena ekspektasi saya default alignment di tabel harusnya di atas.

![](https://www.baguzzzaji.com/wp-content/uploads/2024/10/Screenshot-2024-10-03-at-18.18.15-1024x582.png)

Tapi tenang saja, untuk mengatasinya sangat mudah. Kita cukup atur properti  `vertical-align`  pada element  `td`  di suatu tabel.

```
td {
  vertical-align: top;
}
```

Hanya dengan satu properti tersebut, sekarang konten dari sebuah kolom akan rata atas.

![](https://www.baguzzzaji.com/wp-content/uploads/2024/10/Screenshot-2024-10-03-at-18.33.55-1024x582.png)