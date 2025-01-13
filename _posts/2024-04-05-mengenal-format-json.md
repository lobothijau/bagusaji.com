---
title: "Mengenal Format JSON (JavaScript Object Notation)"
date: 2024-04-05
description: |
  JSON adalah sebuah format untuk melakukan pertukaran data di internet sebagai alternatif lain dari XML. Artikel ini membahas tentang format JSON dan bagaimana cara memanfaatkannya.
tags: json
---

JSON adalah sebuah format untuk melakukan pertukaran data di internet sebagai alternatif lain dari XML. Sesuai dengan namanya, aturan penulisan JSON diturunkan dari penulisan objek di bahasa pemrograman JavaScript. Meskipun begitu format JSON bersifat terbuka dan bisa dipakai di bahasa pemrograman maupun framework apapun.

Meskipun jarang dilakukan, saat disimpan di dalam sebuah file, JSON akan menggunakan akhiran  `.json`. Saat diproses sebagai sebuah data, JSON juga bisa ditulis sebagai sebuah string, misalnya saat pertukaran data antara server dengan client (melalui suatu API).

Objek JSON merupakan data dengan format  _key-value_  dan ditulis diantara dua kurung kurawal seperti halnya objek dalam pemrograman JavaScript. Berikut contoh JSON sederhana:

```json
{
  "name": "Bagus Aji",
  "city": "Bandung",
  "url": "https://baguzzzaji.com",
  "age": 29
}
```

Dalam prakteknya, sebuah data JSON bisa sangat panjang dan sangat kompleks. Contoh di atas hanya menampilkan data satu level dengan  _key_  yang ditulis di sebelah kiri simbol  `:`  dan  _value_  dari  _key_  tersebut ditulis di sebelah kanan  `:`.  _Key_  merupakan sebuah string dan ditulis dengan tanpa petik juga harus bersifat  _unique_, artinya jangan sampai ada yang sama.  _Key_  harus  _unique_  karena untuk mendapatkan value, kita perlu memanggil key yang bersangkutan. Apabila ada key yang sama, maka ada resiko untuk mendapatkan hasil yang salah.

Value yang bisa ditulis di sebelah kanan titik dua bisa berupa salah satu dari keenam tipe data berikut:

-   string
-   number (int atau double)
-   object
-   array
-   boolean (true atau false)
-   null

Seperti yang dapat pembaca lihat, masing-masing pasangan  _key-value_  dipisahkan oleh tanda koma. Kesalahan penulisan tanda koma bisa menyebabkan JSON menjadi tidak valid.

Meskipun aturan penulisannya diturunkan dari JavaScript dan aturan penulisannya pun sangat mirip, tidak semua yang ada di objek JavaScript tersedia di JSON. Misalnya kita tidak bisa menulis suatu fungsi di dalam JSON.

```json
{
  "name": "Bagus Aji",
  "city": "Bandung",
  "age": 29,
  "url": ["https://baguzzzaji.com", "https://bagusaji.dev"],
}
```

Pada contoh di atas  _key_  url memiliki dua data yang ditulis dalam array. Konsep array yang dipakai secara umum sama dengan array pada pemrograman.