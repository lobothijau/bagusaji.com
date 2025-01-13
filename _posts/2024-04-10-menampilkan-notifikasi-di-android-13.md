---
title: "Menampilkan Notifikasi di Android 13"
date: 2024-04-10
description: |
  Notifikasi merupakan sebuah cara bagi suatu aplikasi untuk menginformasikan pengguna tentang event yang terjadi ketika aplikasi sedang tidak dibuka. Artikel ini akan membahas cara menggunakan dan menampilkan notifikasi di Android 13 dengan Kotlin.
tags: android, kotlin
---

Notifikasi merupakan sebuah cara bagi suatu aplikasi untuk menginformasikan pengguna tentang event yang terjadi ketika aplikasi sedang tidak dibuka. Contoh event seperti pesan masuk ketika aplikasi sedang ditutup, pengumuman terkait fitur tertentu, perkiraan cuaca baru dan lain sebagainya. Artikel ini akan membahas cara menggunakan dan menampilkan notifikasi di Android dengan Kotlin.

## Meminta Ijin Menampilkan Notifikasi

Mulai dari Android 13, sebelum bisa menampilkan notifikasi kita harus meminta  _runtime permission_  terlebih dahulu. Pertama, kita siapkan dulu method untuk memeriksa apakah aplikasi sudah mendapatkan ijin, bila belum maka tampilkan popup-nya. Bila ijin ditolak, maka tampilkan  _snackbar_  untuk membuka halaman Settings dan mengijinkan permission Notification secara manual.

```kotlin
private val requestPermissionLauncher = registerForActivityResult(
    ActivityResultContracts.RequestPermission()
) { isGranted: Boolean ->
    if (isGranted) {
        Snackbar.make(findViewById(R.id.main), "Notifications permission granted", Snackbar.LENGTH_SHORT)
            .show()
    } else {
        Snackbar.make(
            findViewById(R.id.main),
            "${getString(R.string.app_name)} can't post notifications without Notification permission",
            Snackbar.LENGTH_INDEFINITE
        ).setAction("Open Settings") {
            if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
                val settingsIntent: Intent = Intent(Settings.ACTION_APP_NOTIFICATION_SETTINGS)
                    .addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
                    .putExtra(Settings.EXTRA_APP_PACKAGE, packageName)
                startActivity(settingsIntent)
            }
        }.show()
    }
}

private fun askNotificationPermission() {
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
        if (ContextCompat.checkSelfPermission(this, android.Manifest.permission.POST_NOTIFICATIONS) ==
            PackageManager.PERMISSION_GRANTED
        ) {
            // Lakukan sesuatu bila permission allowed
        } else {
            // Meminta ijin pengguna untuk menampilkan notification
            requestPermissionLauncher.launch(android.Manifest.permission.POST_NOTIFICATIONS)
        }
    }
}
```

Panggil method  `askNotificationPermission()`  di method  `onCreate()`.

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        askNotificationPermission()

        // kode-kode yang lain
    }
```

![](/assets/images/posts/WhatsApp-Image-2024-07-15-at-13.12.52-837x1024.jpeg)

Bila tidak user memilih  **jangan izinkan,** maka user harus mengijinkannya lewat menu Settings.

![](/assets/images/posts/WhatsApp-Image-2024-07-15-at-13.13.58-461x1024.jpeg)

![](/assets/images/posts/WhatsApp-Image-2024-07-15-at-13.13.55-461x1024.jpeg)

## Notification Channel

Pada sistem Android sebelum Nougat, semua notifikasi dari satu aplikasi berada pada level yang sama. Ketika user memutuskan untuk tidak memperbolehkan suatu notifikasi, maka semua notifikasi tidak akan muncul. Pada versi Android yang baru sejak Nougat, diperkenalkan fitur bernama  _notification channel_  yang berfungsi untuk mengelompokkan notifikasi dari suatu aplikasi. Contoh untuk notifikasi iklan dibuat dengan  _channel_  _sales_, notifikasi percakapan dengan  _channel_  _chat_. dan lain-lain. Dengan begitu, bila kita tetap ingin menerima notifikasi terkait percakapan tapi tidak ingin menerima notifikasi dari penjualan, maka cukup matikan channel  _sales_.

Selanjutnya, buat sebuah method untuk menampilkan notifikasi:

```kotlin
private fun showNotification() {
    val manager = getSystemService(NOTIFICATION_SERVICE) as NotificationManager

    // 1
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O && manager.getNotificationChannel(
            "announcement"
        ) == null
    ) {
        manager.createNotificationChannel(
            NotificationChannel(
                "announcement",
                "Pengumuman", NotificationManager.IMPORTANCE_DEFAULT
            )
        )
    }
    
    // 2
    val builder = NotificationCompat.Builder(this, "announcement")
    builder
        .setAutoCancel(true) 
        .setContentTitle("Pengumuman Aplikasi")
        .setContentText("Aplikasi akan menjalani maintenance bulanan dan tidak dapat diakses selama 2 jam.")
        .setSmallIcon(android.R.drawable.star_on) 

    // 3
    val intent = Intent(this, MainActivity::class.java)
    val pendingIntent = PendingIntent.getActivity(this, 0, intent, PendingIntent.FLAG_UPDATE_CURRENT or PendingIntent.FLAG_IMMUTABLE) // 4
    builder.setContentIntent(pendingIntent)

    // 5
    manager.notify(212, builder.build())
}
```

1.  Kita periksa terlebih dahulu apakah sudah ada notification channel dengan id yang kita inginkan, dalam contoh ini adalah channel “announcement”. Jika belum ada maka buat channel baru.
2.  Berikutnya kita membuat objek notification builder baru dan mengatur:
    -   setAutoCancel: Bila true maka notifikasi akan hilang saat di klik
    -   setContentTitle: Mengatur judul notifikasi
    -   setContentText: Mengatur body notifikasi
    -   setSmallIcon: Mengatur icon yang akan tampil di  _tray_ notifikasi.
3.  Mengatur PendingIntent atau intent yang akan aktif ketika notifikasi di klik, pada contoh di atas kita akan membuka MainActivity.
4.  Untuk Android 12 ke atas, setiap pending intent wajib memiliki PendingIntent.FLAG_IMMUTABLE atau PendingIntent.FLAG_MUTABLE, jika tidak aplikasi akan crash.
5.  Meminta notification manager untuk menampilkan notifikasi.

Berikutnya panggil method  `showNotification()`  pada tempat yang dibutuhkan. Contohnya di sini penulis menampilkan notifikasi saat sebuah button di klik.

```kotlin
val button = findViewById<Button>(R.id.showNotification)
button.setOnClickListener {
    showNotification()
}
```

![](/assets/images/posts/WhatsApp-Image-2024-07-15-at-13.24.37-562x1024.jpeg)

Tampilan notifikasi

Apabila pembaca membuka membuka halaman Info aplikasi (_application info_), pembaca bisa melihat semua channel yang dimiliki aplikasi tersebut diikuti engan sebuah  _switch_  untuk menonaktifkan channel tertentu.

![](/assets/images/posts/WhatsApp-Image-2024-07-15-at-13.26.23-461x1024.jpeg)

Semoga artikel ini bermanfaat.