---
title: Memanggil View by ID
date: 2024-03-30
description: Artikel ini mendeskripsikan secara singkat bagaimana cara memanggil view yang ada di layout XML dari kode Kotlin. Cara yang paling klasik dan akan bekerja pada semua jenis Android.
tags: android
---

Saat ingin memanggil view yang ada di layout XML dan kode Java atau Kotlin, kita akan menggunakan method  `findViewById()`. Method ini akan meminta sebuah nilai integer yang dibuatkan oleh build system Android ketika memberikan id pada suatu View.

```xml
    <androidx.appcompat.widget.AppCompatImageView
        android:id="@+id/logo"
        android:layout_width="112dp"
        android:layout_height="82dp"
        android:src="@drawable/ic_logo"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />
```

Bila ingin memanggil ImageView pada layout XML di atas di kode Kotlin maka kita akan tuliskan dengan:

```kotlin
val imageView = findViewById<ImageView>(R.id.logo)
```

Method  `findViewById()`  merupakan teknik yang sudah ada sejak dahulu dan sampai sekarang masih bisa digunakan tanpa ada masalah. Hanya saja, kita harus benar-benar teliti saat menggunakannya. Meskipun sangat jarang, ada kalanya kita keliru memanggil ID yang ternyata berada di file XML lain sehingga bisa menyebabkan aplikasi  _crash_.