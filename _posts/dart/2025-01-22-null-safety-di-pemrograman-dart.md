## Apa itu Null? 

Dalam konsep pemrograman Dart, null berarti "tidak ada nilai". Konsep ini sangat penting karena membantu dalam mengatasi kesalahan yang sering terjadi dalam pemrograman, yaitu kesalahan yang terjadi karena nilai yang diharapkan tidak ada. 

```dart
int age = 17;
```

Contoh kasus, anggap seorang siswa belum memiliki data yang lengkap sehingga belum diketahui umurnya. Bagaimana cara kita menyatakan hal tersebut? Mungkin cara yang paling mudah adalah dengan memberikan nilai `-1` untuk menandakan bahwa umur siswa tersebut belum diketahui. 

```dart
int age = -1;
```

Nilai `-1` bermakna "tidak ada nilai", tapi bagi compiler, nilai tersebut tetaplah sebuah integer yang valid. Kita harus bisa memberitahu developer lain, bahwa -1 itu artinya "tidak ada nilai" sehingga harus di handle dengan baik. Bisa lewat komentar atau lewat dokumentasi lainnya. 

Nilai `null` diciptakan untuk menjelaskan ketiadaan nilai pada suatu variable. Nilai ini secara global bermakna "tidak ada nilai", sehingga kita tidak perlu lagi menambahkan komentar atau dokumentasi lainnya. Bahkan compiler bisa memberitahu developer, bahwa nilai tersebut tidak valid, sehingga mungkin perlu membuat kondisi khusus untuk menanganinya. 

```dart
int age = null;
```

Pada versi Dart sebelum 2.12, kita bisa menetapkan nilai `null` ke suatu variabel seperti pada contoh di atas. Namun sekarang, kita akan diberikan error oleh Dart. 

```dart
A value of type 'Null' can't be assigned to a variable of type 'int'.
```

## Null Safety

