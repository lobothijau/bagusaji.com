---
title: TextField dan BasicTextField di Compose
date: 2024-03-29
description: Artikel ini akan membahas perbedaan dan persamaan antara TextField dan BasicTextField di Jetpack Compose.
tags: jetpack-compose
---

Jetpack Compose memiliki banyak komponent (composable function) untuk membangun antarmuka, dua diantaranya adalah  `TextField`  dan  `BasicTextField`. Kedua komponen ini dipakai untuk menerima input dari user. Pada artikel kali ini kita akan membahas perbedaan dan persamaan keduanya.

## Apa itu TextField

`TextField`  merupakan composable yang memberikan komponen yang lengkap, sebuah field yang mengimplementasi aturan-aturan Material Design, dengan tampilan dan berbagai fitur bawaan.

Saat menggunakan TextField, kita sudah mendapatkan sebuah komponen yang cantik dengan styling yang sudah mengikuti standar Material Design. Kita sudah mendapatkan label, placeholder, error message dan lain sebagainya.

Berikut contoh penggunaan TextField.

```kotlin
TextField(
    value = text,
    onValueChange = { text = it },
    label = { Text("Label") },
    placeholder = { Text("Placeholder") },
    isError = isError,
    modifier = Modifier.fillMaxWidth()
)

```

## Apa itu BasicTextField

`BasicTextField`  bisa dibilang sebagai TextField yang lebih minim fitur dengan tampilan yang jauh lebih sederhana. Komponen BasicTextField hanya fokus pada fitur utama yaitu input teks. Tujuannya satu, memberikan kebebasan bagi developer untuk membuat text input dengan tampilan dan  _behavior_  sendiri.

Berikut conoth penggunaan BasicTextField:

```kotlin
BasicTextField(
    value = text,
    onValueChange = { text = it },
    modifier = Modifier
        .border(1.dp, Color.Gray)
        .padding(8.dp)
        .fillMaxWidth()
)

```

## TextField atau BasicTextField

Karena  `TextField`  sudah memiliki standar tampilan Material Design dan beragam fitur bawaan, komponen ini cocok jika kita membutuhkan input teks standar tanpa banyak modifikasi.  `TextField`  mudah dan cepat digunakan dan fitur utama yang sering dipakai pun sudah tersedia. Namun, bila aplikasi kita ternyata tidak begitu mengikuti standar Material Design atau membutuhkan  _behavior_  yang tidak disediakan oleh  `TextField`  atau justru tidak ingin input teks nya seperti  `TextField`, maka gunakan  `BasicTextField`.

`BasicTextField`  akan memberika input teks yang minimalis sehingga siap untuk dimodifikasi sesuai dengan kebutuhan. Namun, perlu diketahui juga bahwa kita akan membutuhkan  _effort_  yang lebih besar untuk mengimplementasikannya.