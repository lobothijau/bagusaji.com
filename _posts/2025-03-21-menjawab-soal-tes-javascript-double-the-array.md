---
title: "Menjawab Soal Tes JavaScript - Double the Array"
date: 2025-03-21
description: "Artikel ini membahas bagaimana cara menjawab soal tes untuk menggandakan item array."
tags: javascript, interview
---

Tulis sebuah fungsi bernama `double` yang menerima sebuah array dan mengembalikan sebuah array baru setelah menggandakan setiap item dari array tersebut. 

```js
function double(arr) {
  let results = [];
  for (let i = 0; i < arr.length; i++) {
    results.push(arr[i] * 2);
  }
  return results;
}
```

Cara di atas menggunakan *step by step* yang memanfaatkan pembuatan array baru dan pengisian data dengan *looping*. Tidak ada yang salah dengan cara di atas, tapi JavaScript juga memiliki satu method yang bisa dimanfaatkan untuk melakukan hal yang sama method tersbeut adalah map. 

```js
function double(arr) {
  return arr.map((item) => item * 2);
}
```

Method map akan secara internal melakukan looping dan mengembalikan sebuah array baru. 