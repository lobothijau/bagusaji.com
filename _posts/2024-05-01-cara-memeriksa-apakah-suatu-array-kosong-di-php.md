---
title: "Cara Memeriksa Apakah Suatu Array Kosong di PHP"
date: 2024-05-01
description: |
  Ada beberapa cara yang bisa kita lakukan untuk memeriksa apakah suatu array di bahasa pemrograman PHP kosong atau tidak. Cara yang paling sering saya pakai ada tiga yaitu:
tags: php
---

Ada beberapa cara yang bisa kita lakukan untuk memeriksa apakah suatu array di bahasa pemrograman PHP kosong atau tidak. Cara yang paling sering saya pakai ada tiga yaitu:

### Fungsi empty()

Cara yang pertama yaitu dengan memanggil method  `empty()`  bawaan PHP. Method ini menerima sebuah array dan mengembalikan nilai true bila array tersebut tidak kosong, dan sebaliknya akan mengembalikan nilai false bila kosong.

```
$arr = [];

// Bernilai true karena $arr kosong
if (empty($arr)) {
    echo '$arr kosong';
}
```

### Fungsi count()

Fungsi  `count()`  sejatinya dipakai untuk menghitung jumlah elemen dari suatu array. Kita bisa melihat hasil dari  `count()`  untuk menentukan apakah dia kosong atau tidak.

```
$arr = [1, 2, 3];
 
// 3 -> ada tiga elemen di dalam $arr
$count = count($arr);
 
if ($count == 0) {
    // array kosong
} else {
    // array tidak kosong 
}
```

### Operator Not (!)

Dalam bahasa pemrograman PHP, array yang tidak kosong bersifat  _truthy_  alias akan dianggap  **true**  sedangkan array kosong bersifat  _falsy_  alias dianggap  **false**.

```
if ($arr) {
  echo 'ada';
} else {
  echo 'tidak ada';
}
```

Oleh karena itu, kita bisa memanfaatkan operator  **not (!)**  untuk memeriksa apakah suatu array kosong atau tidak.

```
if (!$arr) {
    echo '$arr kosong.';
}
```