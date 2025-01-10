---
title: "Class dan Object di Pemrograman Dart"
date: 2025-01-07
description: "Setelah memahai tentang fungsi, berikutnya kita akan mempelajari tentang apa itu class dan object di bahasa pemrograman Dart dan bagaimana cara menggunakannya."
series: dart
series_title: "Class dan Object di Pemrograman Dart"
---

{% include series.liquid %}

Tipe data yang sudah kita gunakan sampai bab ini merupakan tipe data yang sudah ditentukan sebelumnya seperti `String`, `int`, atau `bool`. Kali ini kita akan mendiskusikan bagaimana membuat tipe data sendiri dengan menggunakan `class`. 

Class bagaikan sebuah template yang di dalamnya terdapat variabel, fungsi dan komponen-komponen lain. Dalam konsep pemrogramn berorientasi objek/*object oriented programming (OOP)*, class sering dicontohkan sebagai sebuah *blueprint* sebuah desain awal yang produksinya bisa menghasilkan berbagai jenis objek. Contoh, Mitsubishi memiliki satu desain mobil Expander, tapi dari satu desain itu mereka bisa memproduksi mobil dengan berbagai macam warna, berbagai macam jenis tempat duduk, tapi juga masih memiliki mesin yang sama, rangka yang sama, setir yang sama dan lain sebagainya. 

Semua nilai dalam pemrograman Dart merupakan sebuah objek. Objek dalam konsep OOP adalah variabel yang dibuat dari sebuah class. Sejatinya tipe data seperti int, double dan bool semuanya merupakan objek. Class merupakan komponen mendasar pemrogaman berorientasi objek, saat nanti membuat aplikasi mobile dengan Flutter, kita akan memakai class di mana-mana. 

## Cara Membuat Class

Berikut ini merupakan contoh class sederhana dengan dua buah properti:

```dart
class Student {
    int age = 0;
    String name = '';
}
```

Sebuah class didefinisikan dengan menulis *keyword* **class** diikuti dengan nama yang diinginkan. Nama suatu class ditulis dengan format CamelCase lalu diikuti oleh blok kurung kurawal. Pada contoh di atas, kelas `Student` memiliki dua buah properti yaitu `age` dengan tipe data `int` serta `name` dengan tipe data `String`. Properti adalah istilah bagi suatu variabel yang dideklarasikan di dalam suatu `class`. Istilah lain bagi properti yang mungkin akan sering pembaca temukan adalah `fields`. 

## Membuat Objek dari Sebuah Class

Seperti yang sudah pernah disinggung sebelumnya, sebuah objek adalah sesuatu yang dibuat dari suatu class atau istilah lain bagi sebuah objek adalah suatu `instance`. Berikut contoh membuat sebuah objek dari class `Student`. 

```dart
var andi = Student();
```

Kita membuat sebuah *instance* dari class `Student` dengan nama `andi`. Perhatikan tanda kurung setelah menuliskan nama class. Tanda kurung ini wajib dituliskan dan berfungsi untuk memanggil *constructor* dari kelas `Student` yang akan kita bahas selanjutnya. 

Membuat objek dengan cara yang dicontohkan baru bisa dilakukan pada versi Dart 2.0. Pada versi-versi sebelumnya kita wajib menuliskan keyword `new` sebelum menulis nama kelas. Pada saat itu kode yang harus kita tuliskan adalah sebagai berikut:

```dart
var andi = new Student();
```

Meskipun masih bisa dipakai namun penulisan keyword `new` tidak begitu disarankan. Bahkan editor seperti Android Studio akan menyarankan kita untuk tidak menuliskannya. 

## Mengubah Nilai Properti

Kelas `Student` yang kita buat memiliki dua buah properti yaitu `age` dan `name`. Untuk mengisi nilai baru pada properti kita akan mengaksesnya menggunakan *dot notation*.

```dart
void main() {
  final andi = Student();
  andi.name = "Andi Malarangeng";
  andi.age = 23;
  print(andi.name);
}

class Student {
  int age = 0;
  String name = '';
}
```

Bila kode di atas dijalankan maka kita akan mendapat `Andi Malarangeng` di cetak oleh perintah print. Apa yang terjadi bila yang kita print adalah objeknya? 

```dart
print(andi);
// Instance of 'Student'
```

## Memanfaatkan Method `toString()`

Hasil yang kita dapat tentu tidak memiliki informasi yang berharga. Umumnya, saat mencetak suatu objek kita juganingin melihat semua atau sebagian dari properti yang dimiliki objek tersebut. 

Setiap objek yang ada di Dart memiliki method `toString` untuk mengatur teks yang didapatkan saat objek di print. 

```dart
class Student {
  int age = 0;
  String name = '';

  @override
  String toString() {
    return "Student(age: $age, name: $name)";
  }
}
```

Sesuatu yang di awali dengan tanda `@` disebut dengan *annotation*. *Annotation* berfungsi untuk memberitahu *compiler* informasi mengenai kode yang ada di bawahnya. Khusus annotation `@override`, ia memberi tahu bahwa method `toString` diturunkan (_inherited_) dari class lain dan class yang kita miliki akan memiliki implementasi yang berbeda. _Annotation_ akan kita bahas di kesempatan lain. 

## Konstruktor

Konstruktor merupakan salah satu komponen yang erat kaitannya dengan sebuah `class` dan akan sangat sering dipakai dalam membuat program menggunakan Dart. Konstruktor merupakan fungsi yang akan selalu dipanggil pertama kali ketika membuat objek baru. Pada umumnya konstruktor dipakai untuk menentukan nilai awal properti-properti dari suatu kelas. 

Setiap konstruktor dalam bahasa pemrogaman Dart memiliki nama yang sama persis dengan nama `class`. Ada beberapa cara dalam membuat konstruktor, mari kita pelajari satu per satu. 

### Default Constructor

Saat kita membuat sebuah `class` tanpa konstruktor, sebetulnya di belakang layar, _compiler_ dart akan menambahkan satu konstruktor secara implisit. 


```dart
class Student {
    int age = 0;
    String name = '';
}
```

Potongan kode di atas sama artinya dengan kita menuliskannya dengan cara:

```dart
class Student {
  Address();

  int age = 0;
  String name = '';
}
```

Karena hanya dipakai untuk membuat objek saja tanpa ada parameter tertentu, penulisan _default constructor_ menjadi tidak wajib karena compiler dapat melakukannya untuk kita. 

### Format Panjang

Saat kita ingin menentukan nilai awal dari properti-properti yang ada di dalam suatu class, maka kita perlu membuat konstruktor khusus. Pembaca masih ingat cara kita membuat objek baru dan menentukan properti `name` dan `age` pada bab sebelumnya? 


```dart
void main() {
  final andi = Student();
  andi.name = "Bang Jay";
  andi.age = 23;
  print(andi.name);
}

class Student {
  int age = 0;
  String name = '';
}
```

Kita dapat membuat sebuah konstruktor khusus pada class Student dengan cara:


```dart
class Student {
  int age = 0;
  String name = '';

  Student(String name, int age) {
  	this.name = name;
  	this.age = age;
  }
}
```

Dengan adanya konstruktur baru ini kita dapat mengubah cara menginisialisasi _instance_ dari class Student sebagai berikut:

```dart
void main() {
  final andi = Student("Bang Jay", 23);
  print(andi.name);
}
```

Lebih ringkas bukan? 

### Apa itu `this`? 

Bila pembaca perhatikan, di dalam konstruktor kita menuliskan `this`. Apa fungsinya? 

Dalam sebuah konstruktor maupun dalam method yang lain, kata kunci `this` dipakai untuk membedakan antara variabel lokal (yang dideklarasikan di dalam method atau nomor 3 & 4) dengan variabel yang ada di luar fungsi tersebut (dideklarasikan di dalam class atau nomor 1 & 2). 

![](/assets/images/class-dan-object-di-pemrograman-dart/this.png)

Apabila suatu fungsi memiliki variabel yang sama namanya dengan variabel milik class, maka saat menuliskan `age` atau `name`, kita akan selalu mengacu pada variabel lokal (3 & 4). Maka dari itu setiap ingin memanggil properti suatu class (1 & 2) maka kita perlu menggunakan `this`. 

### Format Pendek

Saat sebuah konstruktor hanya berfungsi untuk melakukan inisialisasi data pada properti seperti pada contoh sebelumnya, Dart memberikan opsi untuk menyingkat penulisannya. 

```dart
class Student {
  int age = 0;
  String name = '';
  
  Student(this.name, this.age);
}
```

Pada contoh di atas kita tidak perlu menuliskan tipe data karena Dart sudah membacanya dari saat deklarasi apabila menggunakan format pendek. 

### Named Constructor

Pada umumnya diberbagai bahasa pemrograman, konstruktor akan selalu memiliki nama yang sama dengan nama kelasnya. Namun, Dart memiliki satu fitur yang sedikit beda dan memperbolehkan konstruktor memiliki nama yang tidak sama dengan nama kelasnya. 

Contoh, saking banyaknya siswa bernama Siti yang berumur 16 tahun, kita ingin membuat konstruktor khusus untuk siswa ini. 

```dart
class Student {
  int age = 0;
  String name = '';

  Student(this.name, this.age);

  Student.siti() {
    name = "Siti";
    age = 16;
  }
}
```

Aturan penulisan _named constructor_ adalah NamaKelas.konstruktor(). Kita bisa menerima parameter seperti format panjang, bisa juga tidak. Karena disini tidak ada parameter yang namanya sama dengan properti, jadi kita tidak perlu menuliskan `this`. 


Konstruktor tambahan yang kita buat bisa dipanggil seperti pada contoh di bawah:


```dart
void main() {
  var student = Student.siti();

  print(student);
}
```

Kita bisa memiliki lebih dari satu konstruktor dalam sebuah class dan bisa menggunakan konstruktor yang dibutuhkan sesuai dengan kebutuhan. 


## Membuat Method Sendiri

Secara sederhana method adalah sebuah fungsi yang terikat dengan class tempat ia berada dan memiliki akses terhadap properti-properti di dalamnya. Pada contoh sebelumnya, method `toString()` dapat mengakses properti age dan name yang tertulis di dalam class `Student`. Kita juga dapat menulis method sendiri. Tapi kapan kita perlu menulis suatu method? 

Pada umumnya, kita perlu menulis method saat ingin memproses data yang dimiliki oleh suatu class. Masih bingung? Mari kita ambil satu contoh kasus. Anggap kita memiliki sebuah lingkaran:

```dart
class Circle {
  
}
```

Suatu lingkaran akan memiliki jari-jari (radius atau `r`) dan diameter. Jari-jari adalah jarak antara pusat lingkaran dengan titik pada lingkaran sedangkan diameter adalah garis yang menghubungkan dua titik pada lingkaran melalui titik pusat. Dalam matematika jari-jari itu nilainya setengah dari diameter atau diameter itu nilainya dua kali jari-jari. 

Berdasarkan definisi tersebut kita bisa membuat sebuah class sebagai berikut. 

```dart
class Circle {
  double r;
  double diameter;

  Circle(this.r, this.diameter);
}
```

Dengan kode seperti di atas kita harus mengelola dua properti yang bisa disimpan dalam satu properti saja. Bagaimana caranya? Kita pilih salah satu properti yang diinginkan, anggap jari-jari (radius). 

```dart
class Circle {
  double r;

  Circle(this.r);
}
```

Dengan hanya menyimpan nilai jari-jari, kita bisa mendapatkan nilai diameter kapan saja dengan membuat sebuah method `getDiameter()`. Method ini akan mengembalikan nilai diameter yang didapat dari perhitungan 2 kali jari-jari. Mari kita lihat bagaimana cara menggunakannya:

```dart
class Circle {
  double r;

  Circle(this.r);

  double getDiameter() {
    return 2 * r;
  }
}

void main() {
  var lingkaran = Circle(7);
  print(lingkaran.r); // 7.0
  print(lingkaran.getDiameter()); // 14.0
}
```

## Getter dan Setter

Dalam pemrograman berorientasi objek, ada konsep yang disebut dengan encapsulation atau enkapsulasi. Salah satu penerapan enkapsulasi adalah mengontrol akses terhadap properti dalam sebuah class. Dart menyediakan cara untuk melakukan hal ini menggunakan getter dan setter.

Getter adalah method khusus yang berfungsi untuk membaca nilai properti, sedangkan setter digunakan untuk mengubah nilai properti. Mari kita ubah class Circle kita menggunakan getter:

```dart
class Circle {
  double _r; // menggunakan underscore untuk membuat properti private
  static const double pi = 3.14159;

  Circle(this._r);

  // getter dengan arrow function
  double get radius => _r;
  double get diameter => 2 * _r;
  double get luas => pi * _r * _r;
  double get keliling => 2 * pi * _r;

  // setter
  set radius(double value) {
    if (value <= 0) {
      throw Exception('Jari-jari tidak boleh bernilai nol atau negatif');
    }
    _r = value;
  }
}
```

Perhatikan beberapa perubahan yang terjadi:

1. Properti r diawali dengan underscore (_r) yang dalam Dart berarti properti tersebut bersifat private
2. Getter ditulis dengan format tipe get nama => expression;
3. Setter ditulis dengan format set nama(tipe parameter) { ... }
4. Kita bisa menambahkan validasi di dalam setter

Cara menggunakan class yang baru:

```dart
void main() {
  var lingkaran = Circle(7);
  
  print(lingkaran.radius); // menggunakan getter
  print(lingkaran.diameter); // menggunakan getter
  print(lingkaran.luas); // menggunakan getter
  
  lingkaran.radius = 10; // menggunakan setter
  print(lingkaran.keliling);
  

  // akan terjadi error dengan exception
  lingkaran.radius = -5;
}
```

Penggunaan getter dan setter membuat kode kita lebih rapi dan aman. Kita bisa mengontrol bagaimana properti diakses dan diubah, serta menambahkan validasi untuk mencegah nilai yang tidak valid.

## Rangkuman
Dalam bab ini kita telah mempelajari:

1. Mengenal tentang apa itu class
2. Cara membuat class dan objek dalam Dart
3. Berbagai jenis konstruktor (default, format panjang, format pendek, dan named constructor)
4. Penggunaan keyword this
5. Cara membuat method dalam class
6. Penggunaan getter dan setter untuk mengontrol akses properti

Class merupakan konsep fundamental dalam pemrograman berorientasi objek dan akan sangat sering digunakan saat membangun aplikasi Flutter. Pemahaman yang baik tentang class dan objek akan sangat membantu dalam perjalanan Anda menjadi developer Flutter yang handal.

Pada bab selanjutnya, kita akan membahas konsep inheritance (pewarisan) dan bagaimana suatu class bisa mewarisi sifat-sifat dari class lainnya.