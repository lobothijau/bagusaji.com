---
title: Tutorial Exposed Dropdown di Android
date: 2024-03-18
description: Artikel ini akan membahas tentang cara menggunakan exposed dropdown untuk memberikan tampilan dropdown yang lebih menarik dibandingkan Spinner.
tags: android
---

Di tutorial ini kita akan belajar cara menggunakan exposed dropdown menu. Menu ini memanfaatkan `TextInputLayout` dan `AutoCompleteTextView` untuk memberikan tampilan dropdown yang lebih menarik dibandingkan saat menggunakan Spinner.

Langkah pertama yang perlu dilakukan adalah menambahkan `TextInputLayout` dan `AutoCompleteTextView` di layout XML.

```xml
<com.google.android.material.textfield.TextInputLayout
    style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox.ExposedDropdownMenu"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_marginStart="32dp"
    android:layout_marginTop="20dp"
    android:layout_marginEnd="32dp"
    android:hint="Pendidikan Terakhir"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent">

    <AutoCompleteTextView
        android:id="@+id/autoCompleteTextView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_weight="1"
        android:inputType="none"
        tools:text="SD" />
</com.google.android.material.textfield.TextInputLayout>
```

Perhatian atribut `style` pada `TextInputLayout` di atas. Atribut itulah yang mengatur tampilan dropdown yang ingin kita miliki. Floating label diatur lewat atribut `hint` sama saat seperti kita akan membuat sebuat text input karena pada dasarnya layoutnya sama, hanya style nya yang berbeda.

![Desain dropdown di layout XML](/assets/images/posts/image.png)

Selanjutnya, buat sebuah string array untuk pilihan-pilihan di dropdown yang kita buat di file `strings.xml`.

```xml
<string-array name="pendidikan">
    <item>SD</item>
    <item>SMP</item>
    <item>SMA</item>
    <item>S1</item>
    <item>S2</item>
    <item>S3</item>
</string-array>
```

Lalu kita buat sebuah layout XML baru sebagai layout pilihan masing-masing item di dropdown. File ini penulis namakan `dropdown_item.xml` di folder **res > layout.**

```xml
<?xml version="1.0" encoding="utf-8"?>
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/textViewFeelings"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="8dp"
    android:text="TextView"
    android:textColor="@color/black"
    android:textSize="16sp"
    app:layout_constraintTop_toTopOf="parent" />
```

Selanjutnya buka `MainActivity` atau kelas yang memiliki `TextInputLayout` dan `AutoCompleteTextView`. Buat sebuah variabel baru untuk mengambil array string yang berisi pilihan untuk dropdown.

Kemudian kita buat sebuah ArrayAdapter dengan layout item yang sebelumnya sudah di buat (`R.layout.dropdown_item`). Adapter ini kemudian dipasangkan ke `AutoCompleteTextView`.

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)


        val items = resources.getStringArray(R.array.pendidikan)
        val arrayAdapter = ArrayAdapter(this, R.layout.dropdown_item, items)

        val autoCompleteTextView = findViewById<AutoCompleteTextView>(R.id.autoCompleteTextView)
        autoCompleteTextView.setAdapter(arrayAdapter)
    }
}
```

Terakhir, jalankan aplikasi ke emulator, exposed dropdown menu sudah bisa digunakan.

Untuk mendeteksi perubahan item yang dipilih dari exposed dropdown yang baru saja dibuat, kita bisa memanfaatkan method `OnItemClickListener`.

```kotlin
// ... code sebelumnya
autoCompleteTextView.setAdapter(arrayAdapter)

autoCompleteTextView.onItemClickListener =
    OnItemClickListener { adapterView, view, position, id ->
        val selectedValue = arrayAdapter.getItem(position)
        Log.d("MainActivity", "onCreate: $selectedValue")
    }
```