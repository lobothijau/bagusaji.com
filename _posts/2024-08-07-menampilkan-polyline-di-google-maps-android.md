---
title: "Menampilkan Polyline di Google Maps Android"
date: 2024-08-07
description: |
  Artikel kali ini akan sedikit membahas bagaimana cara menampilkan icon di Google Maps Android yang dibuat dengan Polyline. Pada salah satu project yang penulis kerjakan, terdapat kebutuhan untuk menampilkan icon penanda start (titik awal) dan finish (titik akhir) dari perjalanan sebuah  _truck_.
tags: google-maps, android
---

Artikel kali ini akan sedikit membahas bagaimana cara menampilkan icon di Google Maps Android yang dibuat dengan Polyline. Pada salah satu project yang penulis kerjakan, terdapat kebutuhan untuk menampilkan icon penanda start (titik awal) dan finish (titik akhir) dari perjalanan sebuah  _truck_.

Menampilkan icon di Google Maps Android dicapai dengan memanfaatkan MarkerOption. Betul, MarkerOptions yang berwarna merah itu bisa diganti dengan icon yang lain.

![](/assets/images/posts/Screenshot-2024-08-07-at-11.44.27.png)

Pertama, siapkan method untuk mengubah suatu Drawable menjadi Bitmap karena MarkerOptions tidak bisa menggunakna Drawable secara langsung.

```
private fun getMarkerIconFromDrawable(drawable: Drawable): BitmapDescriptor {
    val canvas = Canvas()
    val bitmap = Bitmap.createBitmap(
        (drawable.intrinsicWidth * 1.5).toInt(),
        (drawable.intrinsicHeight * 1.5).toInt(),
        Bitmap.Config.ARGB_8888
    )
    canvas.setBitmap(bitmap)
    drawable.setBounds(0, 0, (drawable.intrinsicWidth * 1.5).toInt(), (drawable.intrinsicHeight * 1.5).toInt())
    drawable.draw(canvas)
    return BitmapDescriptorFactory.fromBitmap(bitmap)
}
```

Selanjutnya kita siapkan icon yang dibutuhkan:

```
val startIcon = getMarkerIconFromDrawable(ContextCompat.getDrawable(requireContext(), R.drawable.start_icon)!!)
val endIcon = getMarkerIconFromDrawable(ContextCompat.getDrawable(requireContext(), R.drawable.finish_icon)!!)

mMap.addMarker(
    MarkerOptions().anchor(0.5f, 0.5f).position(listLatLng.first())
        .icon(startIcon)
)
mMap.addMarker(
    MarkerOptions().anchor(0.5f, 0.5f).position(listLatLng.last())
        .icon(endIcon)
)
```

Object  `mMap`  di atas merupakan instance dari  `GoogleMap`  yang sebelumnya sudah disiapkan (penulis asumsikan pembaca sudah menampilkan Maps).

```
private lateinit var mMap: GoogleMap
```

Sementara itu  `listLatLng`  merupakan array atau list yang berisi daftar koordinat yang rutenya ditampilkan oleh Polyline. Karena icon start akan ditampilkan di awal, maka kita akan menampilkannya pada latitude dan longitude yang pertama, sebaliknya di titik akhir mengambil lokasi yang terakhir.