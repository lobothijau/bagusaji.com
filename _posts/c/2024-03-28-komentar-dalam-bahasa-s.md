---
title: Komentar dalam Bahasa C
date: 2024-03-25
description: Artikel ini akan membahas tentang penggunaan komentar dalam bahasa pemrograman C.
tags: c
series: c   
series_title: Belajar Pemrograman C untuk Pemula
index: 3
series_order: 30
---

{% include series.liquid %}

Saat menulis program C kita bisa memberikan komentar sebagai penjelasan tentang bagaimana cara kerja program tersebut. Setiap komentar tidak diproses oleh compiler karena tujuannya hanya agar dibaca oleh progarmmer.

```c
int main()
{
      /* Ini adalah baris komentar */
}
```

Komentar juga bisa ditulis lebih dari satu baris:

```c
int main()
{
      /* Ini adalah komentar
      yang lebih dari satu baris */
}

```

Komentar yang hanya terdiri dari satu baris juga bisa ditulis dengan  `//`.

```c
int main()
{
      // Komentar satu baris
}

```

Saat menulis sebuah fungsi, gunakan komentar untuk menjelaskan  _logic_  yang ada di dalamnya secara umum. Dengan begitu, siapapun programmer yang membacanya, bisa mengerti mengapa fungsi tersebut dibuat dan bagimana cara kerjanya secara umum meskipun mungkin secara keseluruhan implementasi kode program C nya belum dipahami.