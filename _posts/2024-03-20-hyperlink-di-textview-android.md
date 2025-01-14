---
title: Hyperlink di TextView di Android
date: 2024-03-20
description: Artikel ini akan membahas tentang cara membuat TextView bisa memproses suatu URL sehingga TextView menjadi sebuah hyperlink.
tags: android
---

Ada dua cara untuk membuat TextView bisa memproses suatu URL sehingga TextView menjadi interaktif layaknya menggunakan tag  `<a>`  di HTML.

Cara yang pertama ialah dengan menambahkan atribut  `autoLink`  di XML:

```xml
<TextView
    android:id="@+id/text"
    android:autoLink="phone|web"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent" />

```

Atau dengan cara yang kedua lewat Kotlin:

```kotlin
val textView = findViewById<TextView>(R.id.text)
Linkify.addLinks(textView, Linkify.PHONE_NUMBERS or Linkify.WEB_URLS)
```

Linkify merupakan  _utility class_  dari package  `android.text.util`  yang akan mencari teks berdasasrkan aturan regular expression dan mengubahnya menjadi link yang bisa di klik. Kelas ini sangat berguna bila kita ingin agar teks yang ada di dalam suatu TextView yang berisi  **nomor telepon** atau  **alamat web**  bisa di klik secara langsung tanpa banyak  _text handling_.

Untuk nomor telepon agar dapat dideteksi dan diproses sebagai sebuah link, maka ia harus dimulai dengan simbol  `+`  misalnya  `+6281214632571`.

![](/assets/images/posts/CleanShot-2024-06-11-at-22.45.36@2x.png)

Apabila ingin pemrosesan URL yang lebih kompleks atau ingin melakukan kostumisasi teks yang lebih banyak, pertimbangkan untuk menggunakan Spannable.
