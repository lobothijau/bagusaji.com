---
title: Konversi Array menjadi JSON di PHP
date: 2024-09-27
description: |
  Artikel ini membahas cara mengubah array menjadi sebuah JSON di bahasa pemrograman PHP.
tags: php
---

Dalam beberapa kasus kita perlu memproses data JSON dalam sebuah aplikasi PHP. Karena aturan penulisan JSON berbeda dengan PHP maka kita membutuhkan method khusus untuk mengubah objek PHP menjadi sebuah JSON. Perhatikan contoh berikut:

```
$data = [
  "from" => [
    "email" => "bagus@bagusaji.com"
  ],
  "content" => [
    [
      "type" => "text/html",
      "value" => "Hello World"
    ]
  ]
];

$json = json_encode($data);

echo $json;
```

Fungsi  `json_encode()`  akan mengubah array, objek, atau tipe data primitif menjadi sebuah JSON. Kita juga bisa menangkap error yang terjadi saat melakukan proses di atas dengan:

```
$json = json_encode($data);

if (json_last_error() !== JSON_ERROR_NONE) {
    echo json_last_error_msg();
}
```

Fungsi  `json_last_error_msg()`  akan memberikan pesan error yang terjadi saat proses konversi objek PHP menjadi JSON.

Alternatif lainnya adalah dengan menggunakan try – catch.

```
try {
  $data = [
    // sama dengan di atas supaya lebih singkat
  ];

  $json = json_encode($array, JSON_THROW_ON_ERROR);
  echo $json;

} catch (JsonException $exception) {
  exit($exception->getMessage());
}

```