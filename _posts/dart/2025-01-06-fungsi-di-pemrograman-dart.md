---
title: "Fungsi di Pemrograman Dart"
date: 2025-01-06
description: "Fungsi adalah blok kode yang bisa dipanggil diberbagai tempat setelah didefinisikan."
series: dart
series_title: "Fungsi di Pemrograman Dart"
---

{% include series.liquid %}


Sampai dengan bab perulangan, aplikasi Dart yang kita tulis selalu berada dalam sebuah fungsi bernama `main`. Tapi, apa itu fungsi?

Fungsi merupakan sebuah blok kode yang bisa dipanggil atau dipakai ulang (_reuseable_) tanpa menuliskan kodenya dua kali. Sebuah program yang kompleks akan terdiri dari sekelompok fungsi yang masing-masing memiliki tugasnya sendiri. 

Dalam pemrograman, ada sebuah konsep bernama _don't repeat yourself_. Saat ada kode yang sama tapi dipakai berulang kali (dengan _copy paste_ contohnya), maka itu lah saat kita membutuhkan sebuah fungsi. 

Sebuah fungsi terdiri dari empat komponen yaitu _return type_ (1), nama fungsi (2), parameter (3), dan _return value_ (4).

![](/assets/images/fungsi-di-pemrograman-dart/basic_function.png)

Sebuah fungsi dibuat dengan menentukan _return_type_-nya. Apa yang akan di berikan oleh suatu fungsi? Ketika kita menggunakan pemanggang roti maka yang akan di dapatkan adalah roti yang telah matang. Saat menggunakan _juicer_ maka yang akan kita dapatkan adalah jus. Bila menggunakan penanak nasi, maka hasil yang akan kita dapatkan adalah nasi yang matang. Saat menulis sebuah fungsi, kita tentukan data apa yang akan dihasilkan. 

```dart
int sum(int one, int two) {
    return one + two;
}

String generateOrderCode() {
    return "ORD/25052024/0001";
}

void greetings() {
    print("Welcome back");
}

void main() {
    greetings();

    var result = sum(1, 2);

    var code = generateCode();
}
```

Pada tiga contoh di atas kita memiliki empat buah fungsi yang masing-masing akan memberikan sebuah data berupa integer, string dan dua fungsi tidak memiliki return type. 

Saat suatu fungsi memiliki return type, hasilnya bisa kita tampung dalam sebuah variabel yang bisa dipakai untuk proses lainnya. Tipe data yang ditulis pada definisi fungsi harus sama dengan data yang di-return. 

```dart
int circle(double r) {
    var result = 3.14 * r * r;

    return result;
}
```

Program di atas tidak akan bisa di _compile_ karena variabel `result` akan menampung data bertipe `double`, sementara fungsi `circle` memiliki return `int`. Agar bisa di compile, tipe data dan apa yang di _return_ harus disesuaikan.

## Parameter Fungsi

Saat menggunakan penanak nasi, ia akan meminta dua hal, beras dan air. Beras dan air dalam konsep fungsi merupakan parameter. Tanpa kedua parameter ini, penanak nasi tidak akan berfungsi. Ketika kita menyatakan bahwa suatu fungsi dalam program Dart membutuhkan suatu data, maka tulislah apa saja yang dibutuhkan dalam definisi fungsi tersebut.

```dart
double circle(double r) {
    var result = 3.14 * r * r;

    return result;
}
```

Pada contoh program penghitung luas lingkaran di atas, kita membutuhkan data berupa jari-jari. Bila jari-jari tidak ada, maka luas lingkaran tidak mungkin bisa di hitung. Kita juga menentukan bahwa jari-jari ini harus bertipe integer, user tidak bisa mengirimkan tipe data yang lain. 

```dart
void main() {
    circle("14"); // Error
    circle(3); // Error 
}
```

### _Multiple Parameter_

Parameter boleh ditulis lebih dari satu buah. Setiap penulisannya dipisahkan oleh koma. 

```dart
double rectangle(double length, double width) {
    return length * width;
}

void main() {
    final length = 4.0;
    final width = 10.0;
    print("Luas persegi panjang = ${rectangle(length, width)}");
}
```

Saat memanggil fungsi, kita perlu memberikan urutan data yang sesuai dengan permintaan parameternya. Salah mengirimkan urutan posisi parameter bisa saja memberikan hasil yang tidak sesuai. Karena parameter meminta data yang harus sesuai posisi, maka penulisan di atas juga biasa disebut dengan _positional parameter_. 

### _Optional Parameter_

Saat menggunakan positional parameter, semua parameternya harus lengkap. Bila kita hanya mengirimkan satu parameter saja, maka program Dart tidak bisa dijalankan. 

```dart
rectangle(4.0);
//Error: Too few positional arguments: 2 required, 1 given.
```

Pesan error di atas menunjukkan jenis errornya, harus ada 2 parameter, tapi hanya 1 yang diberikan. Argumen hanyalah istilah bagi parameter yang ditulis saat memanggil fungsi. 

Anggaplah kita ingin agar fungsi penghitung luas persegi panjang di atas bisa menerima hanya satu parameter. Bila hanya 1 parameter yang diberikan, kita anggap user akan menghitung luas persegi karena panjang sisinya sama. 

```dart
double rectangle(double length, [double? width]) {
    if (width == null) return length * length;

    return length * width;
}
```

Untuk menentukan bahwa suatu parameter bersifat _optional_ atau boleh tidak diberikan, tuliskan di dalam tanda kurung siku. Karena boleh dikosongkan, maka tipe datanya wajib menggunakan tanda tanya diakhir yang menandakan variabel tersebut merupakan _nullable_. Sekarang, program di atas bisa kita panggil dengan 2 cara:

```dart
rectangle(4.0);
rectangle(4.0, 10.0);
```

Yang perlu pembaca ingat, _optional parameter_ harus disimpan terakhir. Kita tidak bisa menuliskan `[double? width]` sebelum `length`. _Optional parameter_ juga boleh lebih dari satu, bahkan semua parameter boleh dijadikan _optional_.

### Default Value

Saat menggunakan _optional paramater_, sistem Dart akan memberikan nilai null pada variabel `width` saat fungsi `rectangle` hanya mengirimkan satu argumen. Dart juga memungkinkan kita untuk menentukan sendiri apa nilai _default_ bagi suatu parameter. 

```dart
int multiply(int a, [int b = 1]) {
    return a * b;
}

multiply(2, 2); // 4
multiply(5); // 5
```

Program di atas akan mengalikan variabel `a` dengan variabel `b`. Apabila fungsi `multiply` hanya memberikan satu argument untuk variabel `a` saja, maka variabel `b` secara otomatis menampung nilai `1` sesuai dengan _default value_ yang tertulis. 

Berbeda dengan optional parameter yang sebelumnya bisa bernilai null, saat diberikan _default value_, parameter ini pasti akan mendapatkan nilai meskipun tidak dikirim. Oleh karena itu tipe datanya boleh tidak berupa nullable. 

### _Named Parameter_

Fungsi di pemrograman Dart memiliki fitur bernama _named parameter_ untuk membuat nama parameter pada fungsi yang dipanggil lebih jelas. Untuk membuat _named parameter_, berikan tanda kurung kurawal pada parameter yang diinginkan:

```dart
void printTime(int hour, {int minute = 0, int second = 0}) {
  var  hourStr = hour.toString().padLeft(2, "0");
  var  minStr = minute.toString().padLeft(2, "0");
  var  secStr = second.toString().padLeft(2, "0");
  
  print("$hourStr:$minStr:$secStr");
}

void main() {
    printTime(5); 05:00:00
    printTime(5, second: 33, minute: 10); // 05:10:33
}
```

Variabel `minute` dan `second` berada di dalam tanda kurung kurawal, artinya kita harus menuliskan nama variabelnya saat memanggil fungsi tersebut. Perhatikan juga bahwa Dart tidak melihat urutan _named parameter_ karena kita sudah menentukan apa parameter yang dituju. Sementara itu, variabel yang bukan _named parameter_ harus ditulis sesuai urutan penulisannya. 

```dart
void printTime({int hour, int minute = 0, int second = 0}) {
}

void main() {
    printTime();
}
```

Pada contoh berikutnya, kita membuat `hour` menjadi _named parameter_. Akan tetapi setiap _named parameter_ merupakan _optional_ sehingga bila tidak diberikan _default value_ ia harus dideklarasikan sebagai nullable (`int? hour`). Bila kita tidak menentukan _default value_, maka kita bisa menambahkan `required` agar saat fungsi dipanggil, parameter tersebut tetap wajib dituliskan. Agar suatu _named parameter_ wajib dikirim saat fungsi dipanggil, kita bisa menambahkan `required`.

```dart
void printTime({required int hour, int minute = 0, int second = 0}) {
}

void main() {
    printTime(hour: 3); // 03:00:00
}
```

## Parameter Tanpa Tipe Data

Suatu parameter bila tipe datanya tidak dituliskan akan otomatis diberikan tipe data `dynamic`. 

```dart
double circle(r) {
    var result = 3.14 * r * r;

    return result;
}
```

Program akan tetap bisa di _compile_, kita pun bisa memanggil fungsi ini dengan mengirimkan `int` maupun `double`, tapi bila mengirimkan data yang tidak sesuai, maka aplikasi akan crash. 

```dart
void main(){ 
    circle("15");
    // Unhandled exception:
    // type 'String' is not a subtype of type 'num'
}
```

Visual Studio Code atau editor lainnya tidak bisa mendeteksi error sebelum di _compile_ karena parameter `r` tidak ditentukan tipe datanya. 

![](/assets/images/fungsi-di-pemrograman-dart/dynamic.png)

Hal yang sama juga berlaku untuk _return type_ fungsi. Secara umum penulis lebih menyarankan untuk menuliskan tipe data secara eksplisit untuk menghindari berbagai error yang mungkin muncul. 

## Arrow Function

Fungsi yang isinya hanya terdiri dari satu baris bisa ditulis dengan _arrow function_. 

```dart
int add(int a, int b) {

}
```

Fungsi di atas bisa ditulis ulang menjadi:

```dart
int add(int a, int b) => a + b;
```

Blok dalam kurung kurawal dan perintah `return` digantikan oleh tanda panah `=>`. Penggunaan tanda panah hanya berlaku bagi fungsi yang memiliki _return type_ dan bisa ditulis dalam satu baris saja. Bila blok kodenya lebih dari satu baris, maka tidak bisa dituliskan sebagai _arrow function_. 