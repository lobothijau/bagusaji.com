---
title: Mencetak PDF dari Browser
date: 2024-10-03
description: |
  Artikel ini membahas teknik mencetak PDF dari browser untuk kebutuhan export data dengan menggunakan JavaScript tanpa menggunakan library pihak ketiga.
tags: javascript
---

Dalam sebuah project penulis mendapatkan sebuah task untuk melakukan export PDF untuk suatu data. Teknik yang saya gunakan pada awalnya menggunakan  **[laravel-dompdf](https://github.com/barryvdh/laravel-dompdf)**, it works well in local machine sampai di upload ke shared hosting.

![](/assets/images/posts/print-pdf-in-browser.jpeg)

Booom

Setelah berjam-jam tidak menemukan solusi, maka solusi jitu adalah dengan menggunakan fungsi print bawaan tiap-tiap  _browser_. Meskipun hasilnya sedikit berbeda, tapi kebetulan tidak terlalu jauh beda.

Triknya sederhana, buka tab baru yang menampilkan konten yang ingin di-pdf-kan, lalu panggil kode berikut:

```
    document.addEventListener("DOMContentLoaded", function(event) {
        setTimeout(function() {
            window.print();
        }, 500);
        window.onfocus = function() {
            setTimeout(function() {
                window.close();
            }, 500);
        }
    });
```

Konsepnya sederhana, setelah halaman HTML selesai dimuat, tunggu 500 milidetik, lalu panggil dialog  _print_  yang dimiliki browser untuk mengunduh PDF, kemudian tutup tab.

Hasil PDF nya memang tidak ebgitu bagus karena hanya mengikuti apa adanya dari browser, tapi jadi solusi jitu karena saat ini hanya menggunakan shared hosting yang sedikit merepotkan dalam menggunakan Laravel.