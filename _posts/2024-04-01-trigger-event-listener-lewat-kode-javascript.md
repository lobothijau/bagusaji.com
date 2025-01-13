---
title: "Trigger Event Listener Lewat Kode JavaScript"
date: 2024-04-01
description: |
  Artikel ini akan membahas bagaimana jika kita ingin agar kode yang ada di dalam addEventListener bisa dieksekusi dengan menyimulasikan event yang di-listen.
tags: javascript
---

Apabila menuliskan aplikasi web dengan vanilla JavaScript, pasti kita akan menggunakan method addEventListener untuk menunggu suatu event terjadi. Biasanya yang akan ditunggu adalah event click, change, atau input. Artikel ini akan membahas bagaimana jika kita ingin agar kode yang ada di dalam addEventListener bisa dieksekusi dengan menyimulasikan event yang di-listen.

Anggap kita memiliki suatu form input yang me-listen event setiap kali user mengubah isi dari field tersebut.

```javascript
var element = document.getElementById('username');
element.addEventListener('change', function() {
    console.log('The value is now ' + element.value);
});
```

Agar kita bisa memanggil kode di dalam addEventListener, gunakan method dispatchEvent(). Method tersebut akan meminta sebuah objek Event dengan tipe event yang ingin dipanggil. Karena listener di atas adalah sebuah change listener, maka event yang di dispatch harus menyesuaikan.

```javascript
element.dispatchEvent(new Event('change'));
```

Pastikan object element merupakan objek yang sama.
