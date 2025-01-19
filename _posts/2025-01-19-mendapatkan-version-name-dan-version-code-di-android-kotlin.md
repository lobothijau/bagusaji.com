---
title: "Mendapatkan Version Name dan Version Code di Android Kotlin"
date: 2025-01-19
description: "Artikel ini membahas cara mendapatkan version name dan version code dari aplikasi yang kita buat dengan Kotlin"
tags: [android, kotlin]
---

Terkadang kita perlu mendapatkan version name atau version code dari aplikasi yang kita buat dengan Kotlin setelah program dijalankan. Contoh paling sederhana misalnya untuk menampilkan versi aplikasi tersebut di *splash screen*. 

Berikut adalah cara untuk mendapatkan version name dan version code dari aplikasi yang kita buat lewat kode Kotlin.

```kotlin
val manager = context?.packageManager
val info = manager?.getPackageInfo(
    context?.packageName, 0
)

val versionName = info?.versionName
val versionNumber = if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.P) {
                        info?.longVersionCode
                    } else {
                        info?.versionCode
                    }
```
