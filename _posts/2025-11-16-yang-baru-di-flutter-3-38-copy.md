---
title: "Tukar Fungsi Tombol Windows dan Alt Pada Keyboard USB di MacOS"
date: 2025-10-05
description: "Artikel ini membahas cara menukar fungsi tombol Windows dan Alt pada keyboard USB di sistem operasi MacOS."
tags: macos,ios
---

Beberapa waktu yang lalu Google resmi mengumumkan Flutter 3.38 di kuartal keempat 2025. Update terbaru ini diklaim akan meningkatkan produktivitas developer dengan perbaikan pada *developer experience* terutama melalui fitur baru *dot shorthands* serta pembaruan di Widget Previews. 

## Dot Shorthand

Ini adalah fitur baru yang berfungsi untuk mempersingkat aturan penulisan kode Dart. Sebagai contoh, kita bisa menulis `.start` saja daripada kode lengkapnya `MainAxisAlignment.start`. 

```dart
// With shorthands
Column(
  mainAxisAlignment: .start,
  crossAxisAlignment: .center,
  children: [ /* ... */ ],
),

// Without shorthands
Column(
  mainAxisAlignment: MainAxisAlignment.start,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [ /* … */ ],
),
```

Fitur ini juga berlaku bagi named constructor, jadi kita bisa menulis `.all` ketimbang `EdgeInsets.all()`

```dart
Padding(
  padding: .all(8.0),
  child: Text('Hello world'),
),
```

