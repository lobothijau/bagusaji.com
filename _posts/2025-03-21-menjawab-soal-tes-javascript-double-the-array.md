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