---
title: Cara Merubah Nama Aplikasi di Android Studio
date: 2024-03-26
description: Artikel ini akan membahas bagaimana cara merubah nama aplikasi di Android Studio yang akan muncul di perangkat Android pengguna.
tags: android
---

Setiap kali membuat project baru, sistem  _templating_  Android Studio akan menggunakan nama project sebagai nama aplikasi. Seringkali nama aplikasi yang ingin kita tampilkan ke pengguna berbeda dengan nama project. Untuk mengganti nama aplikasi tersebut caranya sangat mudah.

Buka file  `AndroidManifest.xml`  di folder  `app/src/main`  lalu ubah atribut  `android:label`  dengan nama yang diinginkan.

```
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
```

Selain bisa ditulis langsung di file manifest, kita juga bisa mengubahnya dengan mengganti label  `app_name`  di file  **res/values/strings.xml**. Dengan mengubah konten  `app_name`, secara otomatis label yang ada di manifest juga akan ikut berubah.

```
<resources>
    <string name="app_name">BelajarFragment</string>
</resources>
```