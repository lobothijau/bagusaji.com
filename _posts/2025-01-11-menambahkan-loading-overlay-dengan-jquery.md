---
title: Menambahkan Loading Overlay dengan jQuery
date: 2025-01-11
description: "Menampilkan indikator loading saat melakukan suatu proses misalnya pengiriman form menjadi keharusan untuk memberikan feedback kepada user. Artikel ini membahas bagaimana cara melakukannya dengan jQuery."
tags: jquery
---

Saat mengembangkan suatu aplikasi web, kita sering perlu menampilkan indikator loading saat melakukan operasi asynchronous. Meskipun ada banyak cara untuk melakukannya, hari ini saya akan menunjukkan cara mengimplementasikan loading overlay yang elegan menggunakan plugin  `jquery-loading-overlay`.

Kita akan membuat sistem loading overlay sederhana namun efektif yang dapat dengan mudah diintegrasikan ke dalam aplikasi web Anda. Implementasi kita akan mencakup:

## Persiapan

Pertama, sertakan jQuery dan plugin jquery-loading-overlay dalam project Anda:

```
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gasparesganga-jquery-loading-overlay@2.1.7/dist/loadingoverlay.min.js"></script>
```

## Penggunaan Dasar

Berikut contoh sederhana untuk menampilkan dan menyembunyikan loading overlay:

```
// Menampilkan loading overlay
$.LoadingOverlay("show");

// Menyembunyikan loading overlay setelah 3 detik
setTimeout(function(){
    $.LoadingOverlay("hide");
}, 3000);
```

## Contoh Kasus

Mari kita buat contoh yang lebih praktis dengan pengiriman formulir:

```
<form id="userForm">
    <input type="text" name="username" placeholder="Nama Pengguna">
    <input type="email" name="email" placeholder="Email">
    <button type="submit">Kirim</button>
</form>

<script>
        $(document).ready(function () {
            $("#userForm").on("submit", function (e) {
            e.preventDefault();

            // Tampilkan loading overlay
            $.LoadingOverlay("show");

            // Simulasi pemanggilan API
            setTimeout(() => {
                $.LoadingOverlay("hide");
            }, 3000);
            });
        });
</script>
```

## Kustomisasi Overlay

Plugin ini menawarkan banyak opsi kustomisasi. Berikut cara membuat overlay yang menarik:

```
$.LoadingOverlay("show", {
    background: "rgba(0, 0, 0, 0.5)",
    image: "", // Hapus gambar loading bawaan
    fontawesome: "fas fa-spinner fa-spin",  // Tambahkan ikon FontAwesome
    size: 30,
    maxSize: 50,
    minSize: 20,
    resizing: true,
    text: "Memuat...",
    textColor: "#ffffff",
    textResizing: true,
    textAnimation: "fade",
    imageColor: "#ffffff",
    imageResizing: true,
    imageAnimation: "rotate" // animasi yang ingin dipakai
});
```

## Penggunaan Lanjutan: Indikator Progress

Berikut cara mengimplementasikan indikator progress untuk upload file:

```
let progress = 0;

// Tampilkan overlay dengan progress
$.LoadingOverlay("show", {
    image: "",
    custom: $("<div>", {
        css: {
            "border-radius": "50%",
            "width": "50px",
            "height": "50px",
            "border": "5px solid #f3f3f3",
            "border-top": "5px solid #3498db",
            "animation": "spin 1s linear infinite"
        }
    }),
    text: "Mengupload... 0%"
});

// Update progress
function updateProgress(value) {
    progress = value;
    $.LoadingOverlay("text", `Mengupload... ${Math.round(progress)}%`);
}

// Simulasi upload file
let interval = setInterval(function() {
    progress += 10;
    updateProgress(progress);

    if (progress >= 100) {
        clearInterval(interval);
        $.LoadingOverlay("hide");
    }
}, 500);
```

## Praktik Terbaik

1.  **Selalu panggil “hide” saat error**: Pastikan untuk menyembunyikan overlay ketika suatu proses mengalami kegagalan. Hal ini untuk mencegah user stuck tidak bisa ngapa-ngapain.

```
try {
    $.LoadingOverlay("show");
    // do something
} catch (error) {
    console.error(error);
} finally {
    $.LoadingOverlay("hide");
}
```

2.  **Cegah Multiple Overlay**: Pastikan tidak ada overlay yang bertumpuk.

```
let isLoading = false;

async function performOperation() {
    if (isLoading) return;

    isLoading = true;
    $.LoadingOverlay("show");

    try {
        // do something
    } finally {
        $.LoadingOverlay("hide");
        isLoading = false;
    }
}
```

3.  **Target Elemen Tertentu**: Secara otomatis kita akan menampilkan overlay di satu halaman, menutupi semua elemen. Tapi, kita juga bisa menampilkan overlay pada elemen tertentu:

```
$("#myElement").LoadingOverlay("show", {
    background: "rgba(165, 190, 100, 0.5)"
});
```

## Kesimpulan

Plugin jquery-loading-overlay menyediakan cara yang sederhana namun powerful untuk menambahkan indikator loading ke aplikasi web Anda. Dengan berbagai opsi kustomisasi dan API yang mudah digunakan, Anda dapat membuat loading overlay yang terlihat profesional dan meningkatkan pengalaman pengguna.

Ingatlah untuk selalu menangani kasus error dan membersihkan overlay Anda dengan benar untuk mencegahnya terjebak. Selamat mencoba!