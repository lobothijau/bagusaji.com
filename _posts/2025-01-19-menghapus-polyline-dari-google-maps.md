---
title: "Menghapus Polyline dari Google Maps Android"
date: 2025-01-19
description: "Artikel ini membahas cara menghapus polyline dari Google Maps pada pemrograman Android menggunakan Kotlin"
tags: [google-maps, android]
---

Polyline dalam konteks Google Maps merupakan sekelompok garis yang menghubungkan beberapa titik dalam peta untuk menggambarkan jalur, rute atau bentuk lain. 

Setelah menambahkan suatu polyline ke Google Maps, terkadang kita perlu menghapusnya. Berikut adalah cara untuk menghapus polyline dari Google Maps.

## Menghapus Satu Polyline

Saat kita menambahkan polyline ke Google Maps, kita akan mendapatkan objek polyline yang dapat kita gunakan untuk menghapus polyline tersebut.

```kotlin
this.mMap.addPolyline(); 

// ambil objek polyline yang di return oleh method addPolyline

val polyline = this.mMap.addPolyline();
```

Objek polyline di atas dapat kita gunakan untuk menghapus polyline tersebut.

```kotlin
this.mMap.removePolyline(polyline);

// atau dengan memanggil method remove()

polyline.remove();
```

Tapi bagaimana bila ada banyak polyline yang ingin kita hapus? 

Untuk menghapus banyak polyline, kita sebelumnya harus mencatat setiap objek dalam suatu list. List ini kemudian dapat di-loop untuk memanggil method remove() pada setiap objek polyline.

```kotlin
val polylineList = ArrayList<Polyline>();

polylines.add(this.mMap.addPolyline());

// loop untuk menghapus setiap polyline
for (polyline in polylines) {
    polyline.remove();
}
// Method remove di atas hanya untuk menghapus polyline dari maps, 
// method di bawah untuk membersihkan list dari polyline yang sudah dihapus
polylines.clear();
```

