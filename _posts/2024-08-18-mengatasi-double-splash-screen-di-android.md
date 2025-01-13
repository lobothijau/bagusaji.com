---
title: "Mengatasi Double Splash Screen di Android Kotlin"
date: 2024-08-18
description: |
  Sejak Android 12, Android SDK menyediakan SplashScreen API yang dapat dipakai untuk menampilkan gambar atau animasi sebelum aplikasi dibuka. Bila maintenance aplikasi yang diupgrade untuk mendukung Android 12 ke atas, ada kemungkinan kita akan mendapatkan dua buah splashscreen yaitu yang dibuat sendiri serta bawaan dari Android API.
tags: android, kotlin
---

Sejak Android 12, Android SDK menyediakan SplashScreen API yang dapat dipakai untuk menampilkan gambar atau animasi sebelum aplikasi dibuka. Bila maintenance aplikasi yang diupgrade untuk mendukung Android 12 ke atas, ada kemungkinan kita akan mendapatkan dua buah splashscreen yaitu yang dibuat sendiri serta bawaan dari Android API.

Implementasi SplashScreen API yang baru akan membutuhkan waktu, terkadang kita tidak diberikan waktu cukup untuk mengubah dari splash screen yang sudah ada, sehingga saat muncul  _issue_  _double splash screen_, solusi yang paling simpel adalah dengan menyembunyikan SplashScreen yang otomatis diberikan oleh Android API.

Untuk menyembunyikan splash screen bawaan Android, pertama buat sebuah style dengan atribut  `windowIsTranslucent`. Atribut ini akan menyembunyikan splash screen bawaan Android. SplashScreen API sejatinya merupakan sebuah  _window_, ia berada di atas Activity (menimpa), sehingga bila window tersebut dibuat translucent/transparan, maka secara tidak langsung kita menyembunyikannya.

```
<style name="Theme.RemoveSplashScreenTheme" parent="@style/BaseTheme">
    <item name="android:windowIsTranslucent">true</item>
</style>
```

Theme di atas perlu di panggail oleh Activity splash screen yang kita buat sendiri. Bila splash screen sudah memiliki style sendiri, maka tidak perlu membuat theme yang baru, cukup tambahkan atribut  `windowIsTranslucent`  nya.

```
<activity
        android:name="com.bagusaji.SplashScreenActivity"
        android:launchMode="singleInstance"
        android:theme="@style/Theme.RemoveSplashScreenTheme"
        android:noHistory="true" />
```

Referensi: [stackoverflow](https://stackoverflow.com/questions/67921860/disable-android-12-default-splash-screen)
