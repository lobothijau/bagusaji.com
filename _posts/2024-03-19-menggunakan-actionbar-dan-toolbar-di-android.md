---
title: Menggunakan ActionBar dan Toolbar di Android
date: 2024-03-19
description: Artikel ini akan membahas tentang ActionBar dan Toolbar di Android.
tags: android
---

Action bar adalah istilah bagi komponen yang berada dibagian atas sebuah Activity. Di komponen ini kita bisa menginformasikan nama aplikasi, apa halaman yang sedang aktif, terkadang tombol untuk melakukan berbagai aksi seperti kembali ke halaman sebelumnya, atau mengakses fitur lain. Bentuk Action Bar bisa terlihat pada gambar di bawah ini.

![Sumber: Stackoverflow](/assets/images/posts/DraggedImage-3.png)

Sumber: Stackoverflow

Kemudian pada rilis Android Lollipop yang mengenalkan konsep Material Design, Google merilis  **Toolbar**. Secara umum Toolbar memiliki konsep yang sama dengan Action Bar namun dengan banyak opsi yang lebih kaya, diantaranya:

-   Navigation button: Bisa berupa  _up arrow_, navigation drawer hamburger button, dll.
-   Logo: Gambar logo yang bisa ditambahkan dan menyesuaikan tinggi Toolbar.
-   Title dan Subtitle: Subtitle bisa menambahkan deskripsi yang lebih lengkap tentang Activity yang aktif.
-   Custom View: Toolbar bisa memiliki  _custom view_  di dalamnya, misalnya gambar yang akan menghilang saat aplikasi di scroll.
-   Action menu: Menu yang terletak di ujung Toolbar untuk melakukan aksi yang dinilai penting atau sering dilaukan (filter, search, dsb.)

![Sumber: Android Developer](/assets/images/posts/DraggedImage-1-1.png)

Sumber: Android Developer

## Cara Menggunakan Toolbar

Untuk menggunakan  `Toolbar`, tambahkan kode berikut ke layout milik Activity.

```xml
<androidx.appcompat.widget.Toolbar
   android:id="@+id/toolbar"
   android:layout_width="match_parent"
   android:layout_height="?attr/actionBarSize"
   android:background="?attr/colorPrimary"
   android:elevation="4dp"
   android:theme="@style/ThemeOverlay.AppCompat.ActionBar"
   app:popupTheme="@style/ThemeOverlay.AppCompat.Light"/>

```

Atribut  `elevation`  akan memberikan sedikit  _shadow_  di bawah Toolbar sehingga membuatnya sedikit melayang. Selanjutnya, panggil method  `setSupportActionBar()`  dari dalam method  `onCreate()`  Activity yang bersangkutan.

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
    setSupportActionBar(findViewById(R.id.toolbar))
}
```

Toolbar secara otomatis akan menggunakan  _project name_  yang ada di atribut  `label`  di dalam file  `AndroidManifest.xml`.

![](https://www.baguzzzaji.com/wp-content/uploads/2024/06/WhatsApp-Image-2024-06-09-at-22.06.50.jpeg)

Jika ingin mengganti title nya, tambahkan kode berikut:

```kotlin
setContentView(R.layout.activity_main)
setSupportActionBar(findViewById(R.id.toolbar))

// tambahkan baris berikut
supportActionBar?.title = "Custom Title"

```