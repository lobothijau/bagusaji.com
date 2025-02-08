---
title: "Menggunakan Leaflet.js sebagai alternatif Google Maps"
date: 2025-02-08
description: "Artikel ini akan membahas cara menggunakan Leaflet.js untuk menampilkan map interaktif di website kita."
tags: leaflet, javascript, map
---

Beberapa waktu kemarin, penulis menyadari bahwa _tracker_ kurir Shopee Express, menggunakan Leaflet.js untuk menampilkan map dan posisi si kurir. Melihat hal tersebut, penulis tertarik untuk menuliskan sesuatu mengenai Leaflet.js.

## Tentang Leaflet.js

Leaflet.js adalah sebuah library JavaScript yang digunakan untuk menampilkan peta interaktif dan dinamis. Leaflet.js adalah alternatif dari Google Maps, dan memiliki banyak fitur yang sama dengan Google Maps, seperti menampilkan marker, menambahkan overlay, atau menambahkan layer.

Dahulu, penulis akan selalu menggunakan Google Maps, tapi sejak ada keharusan untuk mengaktifkan Google Billing hanya untuk menampilkan map, penulis mulai mencari alternatif lain. Alternatif terbaik yang bisa penulis temukan adalah [Leaflet.js](https://leafletjs.com/).

Artikel kali ini akan membahas cara menggunakan Leaflet.js untuk menampilkan lokasi tempat-tempat yang enak untuk kerja.

## Cara Menggunakan Leaflet.js

Kita akan menggunakan layout yang sangat sederhana tanpa banyak styling karena inti dari artikel ini hanya untuk membahas bagaimana cara menggunakan Leaflet.js.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Cafe</title>

    <script src="https://cdn.tailwindcss.com"></script>
  </head>
  <body class="bg-gray-100 min-h-screen p-8">
    <div class="max-w-4xl mx-auto">
      <h2 class="text-3xl font-bold text-gray-800 mb-4 text-center">
        Cafe Buat Kerja
      </h2>

      <p class="text-gray-600 mb-6 text-center">
        Gunakan map di bawah untuk mencari cafe yang enak untuk kerja.
      </p>

      <div id="map" class="w-full h-[500px]"></div>
    </div>
  </body>
</html>
```

Pada potongan kode di atas, yang perlu diperhatikan adalah sebuah div dengan id `map`, inilah tempat dimana map akan ditampilkan.

Lanjut, kita perlu menambahkan styling dari Leaflet.js ke dalam proyek kita. Tambahkan kode berikut di dalam tag `<head>`:

```html
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  crossorigin=""
/>
```

Selanjutnya, tambahkan library javascript dari Leaflet.js ke dalam proyek kita. Tambahkan kode berikut di dalam sebelum penutup tag `</body>`

```js
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
```

## Menampilkan Map

Sebelum menampilkan map, kita perlu tahu posisi awal yang ingin ditampilkan. Karena studi kasus kali ini membahas cafe-cafe yang enak dipakai untuk kerja di Bandung, maka kita pakai saja koordinat dari gedung sate.

Setelah menentukan koordinat, kita juga perlu menentukan zoom level dari map untuk menentukan ketinggian map-nya. Kita akan menggunakan zoom level 13 untuk menampilkan map dengan detail yang tidak terlalu tinggi tapi juga tidak terlalu rendah.

```js
let map = L.map("map").setView([-6.914744, 107.60981], 13);
```

Bila dijalankan di browser, maka kita akan mendapatkan tampilan seperti berikut:

![](/assets/images/posts/leaflet-empty.png)

Loh, mana map-nya?

Leaflet.js memang tidak memiliki tile map sendiri sehingga kita perlu menambahkan penyedia mapnya terlebih dahulu. Di sini kita akan menggunakan tile map dari OpenStreetMap.

Tambahkan kode berikut di dalam tag `<script>`:

```js
L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
  attribution:
    '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
}).addTo(map);
```

Bila dijalankan di browser, maka kita akan mendapatkan tampilan seperti berikut:

![](/assets/images/posts/leaflet-map.png)

Sekarang map sudah tampil, posisinya pun sudah menunjuk gedung sate sebagai pusat map.

Mari kita lanjutkan dengan menambahkan marker cafe-cafe yang enak untuk kerja di map tersebut.

## Menambahkan Marker

Untuk menambahkan lokasi cafe, kita perlu menambahkan koordinat cafe tersebut ke method `L.marker()`:

```js
  <script>
  const map = L.map("map").setView([-6.914744, 107.60981], 13);
  L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution:
      '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
  }).addTo(map);

  L.marker([-6.914744, 107.60981]).addTo(map);
</script>
```

![](/assets/images/posts/leaflet-marker.png)

Mari kita buat beberapa data cafe dalam sebuah array.

```js
const cafes = [
  {
    name: "Two Cents Coffee",
    location: { latitude: -6.9147, longitude: 107.6089 },
    description: "Cafe modern dengan suasana cozy di Dago",
    telp: "081234567890",
    website: "https://twocents.co.id",
  },
  {
    name: "Upstairs Coffee",
    location: { latitude: -6.9039, longitude: 107.6078 },
    description: "Coffee shop dengan view kota Bandung",
    telp: "081234567890",
    website: "https://upstairs.co.id",
  },
  {
    name: "Dago Bakery Punclut",
    location: { latitude: -6.8563, longitude: 107.6218 },
    description: "Cafe dengan pemandangan kota dari ketinggian",
    telp: "081234567890",
    website: "https://dagobakery.co.id",
  },
  {
    name: "Yellow Truck Coffee",
    location: { latitude: -6.9172, longitude: 107.6191 },
    description: "Coffee shop klasik dengan area kerja yang nyaman",
    telp: "081234567890",
    website: "https://yellowtruck.co.id",
  },
  {
    name: "Contrast Coffee",
    location: { latitude: -6.9134, longitude: 107.6088 },
    description: "Tempat ngopi minimalis dengan wifi cepat",
    telp: "081234567890",
    website: "https://contrast.co.id",
  },
  {
    name: "Sejiwa Coffee",
    location: { latitude: -6.9176, longitude: 107.6097 },
    description: "Coffee shop dengan berbagai pilihan working space",
    telp: "081234567890",
    website: "https://sejiwa.co.id",
  },
  {
    name: "Woodlane Coffee",
    location: { latitude: -6.9031, longitude: 107.6079 },
    description: "Cafe dengan konsep industrial dan outdoor seating",
    telp: "081234567890",
    website: "https://woodlane.co.id",
  },
  {
    name: "SMITH Coffee",
    location: { latitude: -6.9142, longitude: 107.6099 },
    description: "Coffee shop modern dengan menu yang beragam",
    telp: "081234567890",
    website: "https://smith.co.id",
  },
  {
    name: "Nomina Coffee",
    location: { latitude: -6.9129, longitude: 107.6067 },
    description: "Cafe minimalis dengan suasana tenang",
    telp: "081234567890",
    website: "https://nomina.co.id",
  },
  {
    name: "Masagi Coffee",
    location: { latitude: -6.9251, longitude: 107.6206 },
    description: "Coffee shop dengan nuansa Sunda modern",
    telp: "081234567890",
    website: "https://masagi.co.id",
  },
];
```

Hapus kode marker sebelumnya dan gantikan dengan loop untuk menampilkan marker cafe-cafe di atas.

```js
cafes.forEach((cafe) => {
  const location = [cafe.location.latitude, cafe.location.longitude];
  L.marker(location).addTo(map);
});
```

Sekarang kita sudah memiliki map yang menampilkan 10 lokasi cafe yang enak untuk kerja.

![](/assets/images/posts/leaflet-markers.png)

Tapi lokasi saja tidak cukup, kita juga perlu menampilkan informasi dari masing-masing cafe saat markernya di klik.

## Menampilkan Informasi Cafe

Cara paling sederhana untuk menampilkan informasi cafe adalah dengan menampilkan popup saat marker di klik. Kita akan menambahkan popup ke masing-masing marker cafe dengan method `bindPopup()`.

```js
cafes.forEach((cafe) => {
  const location = [cafe.location.latitude, cafe.location.longitude];
  L.marker(location).addTo(map).bindPopup(cafe.name);
});
```

Sekarang setiap kali marker di klik, secara otomatis akan muncul popup yang menampilkan nama cafe.

![](/assets/images/posts/leaflet-bindpopup.png)

Selain menampilkan plain-text, kita juga bisa menampilkan HTML di dalam popup. Kita akan menambahkan informasi tambahan seperti deskripsi, nomor telepon, dan link ke website cafe.

```js
cafes.forEach((cafe) => {
  const location = [cafe.location.latitude, cafe.location.longitude];
  L.marker(location)
    .addTo(map)
    .bindPopup(
      `<b>${cafe.name}</b><p>${cafe.description}</p><div class="flex flex-col"><span>${cafe.telp}</span><a href="${cafe.website}" target="_blank">${cafe.website}</a></div>`
    );
});
```

![](/assets/images/posts/leaflet-html.png)

Mudah sekali bukan? Bagaimana jika pembaca mencoba sendiri untuk menampilkan gambar di popup?

## Penutup

Artikel ini hanya membahas dasar-dasar dari Leaflet.js, dan masih banyak fitur yang bisa kita gunakan untuk menampilkan map yang lebih menarik. 

Tentu saja fitur-fitur Leaflet.js mungkin masih tidak selengkap Google Maps, tapi karena sifatnya yang open source, developer lain banyak juga yang menyediakan plugin untuk memperluas fungsinya.

Semoga artikel ini bermanfaat.
