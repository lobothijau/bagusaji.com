---
title: Memahami File Manifest di Android
date: 2024-03-23
description: Artikel ini akan membahas tentang apa itu file manifest yang digunakan di dalam sebuah project Android.
tags: android
---

Tulisan ini akan membahas tentang fondasi dari setiap aplikasi Android, file manifest yang bernama  `AndroidManfiest.xml`. File ini terletak di folder  `src/main`  masing-masing module (dalam hal ini  `app`).

Apa yang sebetulnya dilakukan oleh file manifest di Android?

File manifest yang dimiliki oleh project Android digunakan untuk mendeklarasikan activity dan service yang dipakai oleh suatu aplikasi. File ini juga dipakai untuk menentukan  _behavior_  sebagian activity, misalnya untuk menentukan activity mana yang akan dipakai secara launcher.

Manifest akan selalu dibuatkan saat kita membuat project Android. Untuk aplikasi biasa, file yang dibuatkan oleh Android Studio sudah mencukupi, tapi saat project semakin besar, konten file juga akan makin gemuk.

Mirip seperti file  `build.gradle`, dulu file manifest juga memiliki informasi  _package name_, namun di versi Android yang baru, file manifest yang dibuatkan sudah tidak mengikutsertakan package lagi.

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.bagusjai.manifest"
    >
```

Child pertama sebuah file manifest saat pertama kali dibuat adalah  `<application>`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    >

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.BelajarFragment"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

Biasanya juga ada sebuah activity di dalam  `<application>`. Saat menambahkan activity atau service baru, maka akan ada tag baru yang ditambahkan di dalam  `<application>`.

## Permission

Makin banyak fitur yang dipakai oleh suatu aplikasi Android, maka ada kemungkinan kita membutuhkan ijin tertentu agar fitur tersebut bisa dijalankan. Misalnya, membaca atau membuat file, menggunakan kamera, menggunakan internet, atau meminta informasi lokasi.

Menambahkan informasi permission dilakukan dengan menulis permission tertentu, contoh:

```xml
<uses-permission android:name="android.permission.CAMERA"/>
```

Untuk Android 6.0 ke atas, selain menambahkan permission di manifest, kita juga perlu mengimplementasi runtime permission, tapi itu perlu di bahas di tulisan terpisah.

## Feature

Bila aplikasi yang kita buat memerlukan suatu fitur hardware atau software tertentu, maka tambahkanlah  `<uses-feature>`  di file manifest. Contoh, bila kita kita membutuhkan fitur camera, maka tambahkan:

```xml
<uses-feature android:name="android.hardware.camera.any" android:required="true" />
```

atribut  `android:name`  menentukan fitur apa yang dibutuhkan oleh aplikasi ini. Bila  `required`  bernilai  _true_, artinya aplikasi ini tidak bisa dipasang bila fitur yang diminta tidak ada.

Kunjungi  [laman <uses-feature>](https://developer.android.com/guide/topics/manifest/uses-feature-element) untuk melihat dokumentasi lengkapnya.

## Auto Backup

Jika pembaca perhatian, di dalam  `<application>`  terdapat beberapa atribut salah satunya  `allowBackup="true"`. Atribut ini menandakan sebuah aplikasi akan mengikuti sistem  _backup_  otomatis milik Android.

Biasanya pembaca akan mengubahnya ke false karena autobackup di sini diatur oleh Google dan kita kurang mendapat kontrol untuk mengatur bagian mana yang di backup, maka yang tidak.