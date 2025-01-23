---
title: "Percabangan di Pemrograman Dart"
date: 2025-01-04
description: "Untuk menghasilkan suatu aplikasi yang bisa bekerja dengan baik, kita perlu membuat suatu program yang bisa membuat suatu keputusan berdasarkan suatu kondisi."
series: dart
series_title: "Percabangan di Pemrograman Dart"
series_order: 40
---

{% include series.liquid %}


Percabangan dipakai untuk mengatur alur program tersebut sehingga terkadang disebut juga dengan kontrol alur atau _control flow_. Program paling sederhana sekalipun pasti akan memiliki bagian untuk memutuskan apa yang perlu dilakukan pada suatu kondisi:

- Apakah user sudah dewasa (berumur lebih dari 17 tahun)? 
- Apakah user sudah terdaftar? 
- Apakah user sudah login? 
- Apakah email sudah terverifikasi? 
- Apakah status koneksi internet _online_? 

Pertanyaan-pertanyaan di atas merupakan kondisi yang akan sering ditemukan pada sebuah aplikasi mobile. Semuanya merupakan pertanyaan dengan jawaban ya atau tidak atau dalam bahasa pemrograman pertanyaan yang bisa dijawab dengan `true` atau `false`. 

Selanjutnya, bagaimana cara memeriksa suatu kondisi dalam bahasa pemrograman Dart? 

## Percabangan `if`

Metode yang paling dasar untuk melakukan percabangan dalam bahasa pemrograman apapun adalah perintah `if`. Ia dipakai untuk mengeksekusi suatu blok apabila komparasinya berhasilkan nilai `true`. 

```dart
var age = 22;

if (age > 17) {
    print("Adult user");
}
```

Blok `if` pada kondisi di atas memeriksa apakah user sudah dewasa atau belum berdasarkan umurnya. Apabila umurnya lebih dari 17 tahun, maka user dianggap sudah dewasa. 

Lalu bagimana bila kita ingin melakukan sesuatu bila user belum berusia 17 tahun?

## Percabangan dengan `else`

Blok `else` dipakai untuk melakukan sesuatu apabila kondisi pada blok `if` tidak terpenuhi. 

```dart
var age = 22;

if (age > 17) {
    print("Adult user");
} else {
    print("Non-adult user");
}
```

Saat menggunakan percabangan `if-else`, hanya akan ada salah satu blok saja yang dieksekusi berdasarkan hasil komparasinya, apakah memenuhi atau tidak memenuhi syarat. 

## Percabangan dengan `else if`

Untuk beberapa kasus, kita memerlukan kondisi tambahan lainnya seperti pada contoh:

- Baby: 0-2 tahun
- Child: 3-12 tahun
- Teen: 13-17 tahun
- Young Adult: 18-27 tahun
- Adult: lebih dari 27 tahun

Kondisi di atas bisa dikontrol dengan memanfaatkan `else if`. 

```dart
var age = 15;

if (age > 27) {
    print("An adult");
} else if (age > 17) {
    print("A young-adult");
} else if (age > 12) {
    print("A teenager");
} else if (age > 3) {
    print("A child");
} else {
    print("A baby");
}
```

Sama seperti sebelumnya, dalam suatu deretan `if-else if-else`, hanya akan ada satu blok yang dieksekusi. Program akan menguji kondisinya satu per satu sampai ada kondisi yang bernilai `true`. Bila tidak ada, maka blok `else` akan selalu dieksekusi. Ubah-ubah nilai variabel `age` untuk mendapatkan hasil yang berbeda-beda. 

Saat membuat kondisi dengan banyak percabangan, perhatikan urutan yang ditulis karena bisa menentukan blok mana yang akan dieksekusi terlebih dahulu. 

## Operator Boolean

Pada contoh penggunaan percabangan `if`, kita melakukan komparasi dengan menguji apakah sautu nilai bernilai `true` atau tidak dengan memakai _operator boolean_. Operator inilah yang akan menghasilkan nilai `true` atau `false` dengan melakukan perbandingan. 

Berikut bagaimana cara melakukan perbandingan dalam bahasa pemrograman Dart. 

### Menguji Nilai Sama Dengan

Menguji nilai sama dengan dilakukan menggunakan _equality operator_ yang dipakai dengan simbol `==`, dua kali tanda sama dengan. Salah satu kesalahan yang paling sering dilakukan pemula adalah menggunakan satu kali tanda sama dengan saat menulis kondisi `if`. 

```dart
var department = "Computer Science";

print(department == "Mathematics"); // false
```

### Menguji Nilai Tidak Sama Dengan

Apabila simbol `==` dipakai untuk menguji nilai sama dengan, maka untuk menguji nilai tidak sama dengan dilakukan dengan simbol `!=` yang disebut juga sebagai _inequality operator_. 

```dart
var department = "Computer Science";

print(department != "Mathematics"); // true
```

### Menguji Nilai Lebih Dari dan Kurang Dari

Untuk membandingkan dua angka dan memeriksa apakah salah satunya bernilai lebih besar atau lebih kecil dapat dilakukan dengan simbol `>` atau `<`. Kedua simbol ini bersifat _exclusive_, artinya angka yang sama akan dianggap `false`. 

```dart
print(4 < 5); // true
print(5 < 5); // false
print(4 > 5); // false
print(5 > 5); // false
```

Untuk memeriksa kondisi lebih dari sama dengan, dilakukan dengan simbol `>=`. 

```dart
print(4 <= 5); // true
print(5 <= 5); // true
```

Sebaliknya memeriksa kondisi kurang dari sama dengan dilakukan dengan simbol `<=`.

```dart
print (5 >= 5); // true
```

### Operator AND

Pada beberapa contoh kasus di atas, kita selalu memeriksa satu kondisi saja. Pada mayoritas kasus, memeriksa satu kondisi saja cukup. Namun tidak jarang juga akan ada dua kondisi yang perlu diperiksa sekaligus. Dua kondisi ini bisa digabungkan dalam satu komparasi, salah satunya dengan operator AND atau simbol `&&`. 

```dart
var age = 16;
var withParent = true;

if (age < 17 && withParent) {
    print("Can buy ticket");
} else {
    print("Can't buy ticket");
}
```

Pada contoh di atas kita memeriksa apakah user berusia dibawah 17 tahun dan datang bersama orang tua. Bila keduanya bernilai `true` maka akan menghasilkan nilai `true` juga. Namun bila salah satu `false`, maka nilai akhirnya menjadi `false` juga. 

Untuk memeriksa kondisi `== true`, bisa disingkat tanpa menuliskannya. Pada contoh di atas cara yang lebih lengkap adalah dengan menulis `withParent == true`, tapi karena variabel ini bertipe boolean, maka bisa disingkat saja. 

### Operator OR

Dalam kondisi AND, semua komparasi harus bernilai `true` sementara pada operator OR cukup satu saja ondisi bernilai   `true` maka hasil ahirnya akan bernilai `true`. Penulisan operator or menggunakan simbol `||`. 

```dart
var status = "closed";

var isStatusAccepted = status == "closed" || status == "approved"

print (isStatusAccepted)
```

### Operator NOT

Secara sederhana operator _not_ akan menyangkal suatu nilai boolean. Operator not dipakai dengan menambahkan simbol `!` didepan suatu variabel. 

```dart
var age = 20;
var isAdult = age > 17;

print(!isAdult)
```

Pada contoh di atas `isAdult` akan bernilai true karena komparasi nilai variabel `age` lebih besar dari 17. Namun, dengan adanya operator not, maka nilai pada komparasi `if` menjadi `false` (not true berarti false dan not false berarti true). 

### Prioritas Operator dengan `()`

Mirip seperti pada operasi aritmatika, penggunaan operator di bahasa pemrograman Dart bisa diatur urutan prioritasnya, mana kondisi yang akan diuji terlebih dahulu dengan menggunakan simbol `()`. Penambahan simbol dalam kurung tersebut akan membantu kode menjadi lebih mudah dibaca ketika satu proses komparasi melibatkan banyak kondisi.

```dart
print((6 > 2 && 1 < 3) || 1 < 3); // true
```

## Ternary Operator

Saat memiliki kondisi `if-else` seperti pada contoh di bawah:

```dart
var level = 101;
String message;

if (level > 100) {
    message = "You win!";
} else {
    message = "Play more games";
}
```

Bisa kita tulis ulang dengan _ternary operator_ untuk mendapatkan kode yang lebih ringkas. 

```dart
String message = (level > 100) ? "You win!" : "Play more games";
```

Sintaks menggunakan _ternary operator_ adalah:

```
(kondisi yang ingin diperiksa) ? nilai jika true : nilai jika false;
```

Terkadang menggunakan _ternary operator_ membuat program menjadi tidak begitu jelas di baca. Kita harus lebih cermat memahami alur kode yang ditulis daripada menggunakan `if-else` biasa yang meskipun lebih panjang namun _logic_ masing-masing blok akan terlihat lebih jelas. 

## Switch

Selain menggunakan `if-else` juga _ternary operator_, cara lain untuk melakukan kontrol alur program adalah menggunakan perintah `switch`. Aturan penulisannya sebagai berikut:

```dart
var command = 'OPEN';
switch (command) {
  case 'CLOSED':
    // do something
    break;
  case 'PENDING':
    // do something
    break;
  case 'APPROVED':
    // do something
    break;
  case 'DENIED':
    // do something
    break;
  case 'OPEN':
    // do something
    break;
  default:
    print("Command is not valid");
}
```

Setelah menuliskan perintah `switch`, tulis nama variabel yang ingin diperiksa isinya di dalam tanda kurung. Setiap `case` akan memeriksa apakah variabel yang ada di dalam tanda kurung nilainya sama dengan yang ditentukan oleh `case`. Jika sama, maka kode yang berada di antara titik dua dan `break;` akan dieksekusi. 

Perintah `break` berfungsi untuk mengelompokkan satu `case` dengan `case` lain. Bila suatu `case` tidak memiliki `break` dan di bawahnya ada `case` lain, maka blok `case` di bawahnya akan ikut dieksekusi. 

Blok `default` berfungsi sama dengan blok `else`, dieksekusi hanya bila tidak ada `case` yang sesuai. 

Seperti percabangan `if`, dengan `switch` kita juga bisa memakai _logical operator_:

```dart
switch (value) {
  case value == 2 || (value / 2) == 0 : // or 
  case value > 0 && value % 2 == 1: // and
  default:
    print("Error");
}
```