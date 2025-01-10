---
title: Bagaimana Cara Menggunakan Nullish Coalescing Assignment Operator di JavaScript
date: 2025-01-10
description: "Nullish coalescing assignment operator adalah operator yang memungkinkan kita untuk menetapkan nilai default ke suatu variabel jika nilainya adalah null atau undefined."
tags: javascript
---


Dalam JavaScript, operator  `??=`  bernama  _nullish coalescing assignment operator_  yang ditambahkan pada ECMAScript 2021 (ES12). Apa gunanya operator ini? Akan lebih mudah menjelaskannya dengan kode:

```
// Sebelum ES12
if (student.age === null || student.age === undefined) {
  user.name = 'Anonymous';
}

// Menggunakan nullish coalescing operator (??)
user.name = user.name ?? 'Anonymous';

// Cara yang baru (mulai dari ES2021)
user.name ??= 'Anonymous';
```

Mudahnya operator ini membantu kita untuk memberikan sebuah  _default value_  saat suatu value yang akan di assign berupa null atau undefined.

Operator  `??=`  akan memeriksa dulu nilai dari variabel disebelah kiri dalam contoh di atas adalah  `user.name`  apakah bernilai  `null`  atau  `undefined`.

Bila bernilai  `null`  atau  `undefined`  maka kode tersebut akan memberikan  _default value_  berupa teks ‘Anonymous’. Yang perlu diingat bahwa string kosongatau nilai 0 akan dianggap valid sehingga tidak akan diberikan  _default value_.

## Mengapa operator ini unggul dibanding opsi lain?

Sebelum  `??=`, ada beberapa cara untuk memberikan  _default value_, tapi setiap opsi memiliki kekurangan.

```
// Menggunakan percabangan - repot dan berulang-ulang
if (user.name === null || user.name === undefined) {
  user.name = 'Anonymous';
}

// Menggunakan operator || - banyak yang harus di handle
user.name = user.name || 'Anonymous';  // Replaces '', 0, false too

// Menggunakan ternary operator - makin ruwet bila opsinya makin banyak
user.name = user.name === null || user.name === undefined
  ? 'Anonymous'
  : user.name;

// Menggunakan ??= - lebih rapi
user.name ??= 'Anonymous';
```

Operator  `??=`  terasa lebih tepat untuk dipakai daam memberikan  _default value_  bagi suatu variabel dibandingkan opsi-opsi pendahulunya, terutama cocok bagi kondisi dimana nilai nol, string kosong atau false merupakan nilai yang valid.

```
let score = 0;
score ??= 100;    // Tetap bernilai 0

let tag = '';
tag ??= 'default'; // Tetap berisi string kosong

let active = false;
active ??= true;   // Tetap bernilai false
```

Referensi [trevorlash](https://www.trevorlasn.com/blog/javascript-nullish-coalescing-assignment-operator).