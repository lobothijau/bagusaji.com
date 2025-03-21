---
title: "Menjawab Soal Tes JavaScript - Jumlah Isi Array"
date: 2025-03-21
description: "Artikel ini membahas bagaimana cara menjawab soal tes untuk menjumlahkan isi dari suatu array."
tags: javascript, interview
---

Buat sebuah fungsi bernama `add` yang menerima sebuah array dan mengembalikan jumlah dari setiap item di dalam array tersebut. 

```js
function add(arr) {
  let result = 0;
  for (let i = 0; i < arr.length; i++) {
    result += arr[i];
  }
  return result;
}
```