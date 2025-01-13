---
title: "Destructuring Array dan Object di JavaScript"
date: 2024-08-17
description: |
  JavaScript memiliki fitur untuk melakukan destsructure suatu objek dan array sehingga isinya bisa di assign ke variabel-variabel baru.
tags: javascript
---

JavaScript memiliki fitur untuk melakukan destsructure suatu objek dan array sehingga isinya bisa di assign ke variabel-variabel baru.

## Destructuring Array

Anggap kita memiliki sebuah array berisi nama lengkap seseorang. Bisa ingin mengekstrak setiap elemen ke dalam variabel baru, maka kita akan mengambilnya lewat indeks array.

```
const name = ["Bagus", "Aji", "Santoso"]
const firstName = name[0]
const middleName = name[1]
const lastName = name[2]
```

Dengan fitur destructuring, pengambilan data di atas bisa ditulis dengan:

```
const name = ["Bagus", "Aji", "Santoso"]
const [firstName, middleName, lastName] = name
```

## Destructuring Object

Sama seperti array, kita juga bisa melakukan destructuring di sebuah objek JavaScript.

```
const name = {
    firstName: "Bagus", 
    middleName: "Aji",
    lastName: "Santoso", 
}

const {firstName, lastName} = name
```

Untuk melakukan destructuring suatu objek, kita akan mengambil isi objek tersebut berdasarkan  `key`-nya. Contoh pada kode di atas, kita akan mengambil hanya  `firstName`  dan  `lastName`  saja.