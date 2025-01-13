---
title: "Mengabaikan Field di Retrofit Android"
date: 2024-06-01
description: |
  Saat menggunakan Retrofit sebagai http client di sebuah aplikasi native Android, kita pasti akan menggunakan suatu model class. Artiekl ini membahas bagaimana cara mengabaikan sebuah field yang didefinisikan di dalam sebuah model dengan Retrofit.
tags: android, kotlin, retrofit
---

Saat menggunakan Retrofit sebagai http client di sebuah aplikasi native Android, kita pasti akan menggunakan suatu model class. Model class ini pada umumnya akan dibaca oleh Retrofit dengan memanfaatkan salah satu dari beberapa json library yang tersedia seperti gson, moshi, atau jackson. Apabila menggunakan gson, setiap field yang ada di model class tersebut akan dibaca dan digunakan oleh Retrofit misalnya saat akan mengirimkan request POST. Bagaimana bila ada sebuah field yang tidak ingin ikut dikirimkan saat melakukan request POST dengan Retrofit?

Cara pertama yang bisa digunakan ialah dengan anotasi  `@Transient`. Contohnya adalah sebagai berikut:

```
data class User(
  @SerializedName("real_name")
  val name: String,
  val age: String,
  @Transient
  val isAdult: Boolean
)
```

Field  `isAdult`  tidak akan diikutsertakan dengan request POST.

Cara yang kedua ialah dengan menggunakan anotasi  `@Expose`.

```
val gson: Gson = GsonBuilder().excludeFieldsWithoutExposeAnnotation().create()

builder = Retrofit.Builder()
            .client(okHttpClient)
            .baseUrl(URL)
            .addConverterFactory(GsonConverterFactory.create(gson))
            .addCallAdapterFactory(RxJava2CallAdapterFactory.create())
```

```
data class User(
  @SerializedName("real_name")
  val name: String,
  val age: String,
  @Expose(serialize = false, deserialize = true)
  val isAdult: Boolean
)
```

Dengan menggunakan anotasi  `@Expose`, artinya field  `isAdult`  akan dibaca saat konversi JSON ke object Java/Kotlin, tapi akan diabaikan saat konversi dari model ke JSON.