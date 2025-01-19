---
title: Belajar Vim untuk Pemula
date: 2025-01-19
description: Artikel perkenalan tentang seri belajar Vim untuk pemula yang akan mulai membahas cara memasng, membuka dan menutup Vim untuk pertama kali.
tags: vim
series: vim
series_title: Belajar Vim untuk Pemula
favorite: true
---

{% include series.liquid %}

**Vim**, mungkin pembaca pernah mendengar nama ini, mungkin juga tidak. Vim adalah salah satu editor teks yang cukup populer di kalangan programmer, meskipun tidak semua programmer mengenal dan menggunakannya. Vim memiliki fitur-fitur unik yang membautnya menjadi pilihan bagi sebagian orang. 

Penulis sendiri sudah mengenal Vim sejak lama, sejak jaman masih sekolah di Sekolah Menengah Kejuruan (SMK) jurusan Teknik Komputer Jaringan. Di SMK, penulis mempelajari tentang dasar-dasar Vim untuk mengedit file di sebuah server. Meskipun sudah lebih dari 10 tahun mengenal Vim, penulis tidak mengggunakannya secara rutin atau menjadikannya editor utama. 

Vim memang memiliki fitur unik yang akan membuat penggunaannya menjadi lebih cepat dan efisien. Namun, mempelajari Vim membutuhkan waktu dan kesabaran. Tidak seperti Visual Studio Code atau Sublime Text yang sangat ramah pemula, Vim bahkan "memaksa" kita untuk menghafal beberapa perintah sekedar untuk membuka, menulis sebuah file dan menutupnya. 

## Mengapa Menggunakan Vim? 

*Text editor* yang paling sering penulis pakai adalah Visual Studio Code atau Android Studio bila berhubungan dengan Android/Flutter development. Dikedua editor tersebut, penulis memasang sebuah plugin yang membuat kita bisa memanfaatkan sebagian fitur Vim di dalamnya. Fitur ini sering disebut sebagai *Vim mode* atau *Vim emulation*. Vim memang secanggih itu, sampai-sampai editor lain dibuat agar bisa meniru sebagian fiturnya. 

Vim tidak wajib dipakai kok, tapi penulis bisa jamin menguasai editor ini bisa membuat kita lebih produktif dan "terlihat" lebih keren.  Apakah pamer itu alasan buruk untuk belajar sesuatu? Silahkan nilai sendiri. Tapi, di kesempatan ini penulis ingin membagi sedikit pengalaman dalam belajar Vim sehingga pembaca bisa ikut belajar. 

## Vim atau Neovim? 

Neovim merupakan aplikasi yang dikembangkan dari Vim. Neovim mengklaim memiliki banyak fitur yang lebih baik dibandingkan Vim misalnya dengan pilihan bahasa pemrograman yang lebih modern, plugin yang lebih banyak dan terkini, dan lain sebagainya. 

Di seri belajar Vim ini, penulis akan menggunakan Vim tanpa membahas mengenai Neovim karena penulis sendiri belum begitu menguasainya. Apakah pembaca perlu merisaukan pemilihan [Vim](https://www.vim.org/) atau [Neovim](https://neovim.io/)? **Penulis rasa tidak perlu**, setidaknya sampai dengan pembahasan *plugin*, semua yang kita lakukan di Vim 8 bisa kita lakukan pula di Neovim. 

## Memasang dan Membuka Vim Untuk Pertama Kali

Vim pada umumnya sudah terpasang di sistem operasi Linux maupun Mac OS X. Untuk Windows, pembaca bisa mengunjungi [website resmi Vim](https://www.vim.org/) untuk mendownloadnya. Untuk pengguna Linux dan Mac OS X, pembaca bisa menggunakan perintah berikut untuk memasangnya: 

```bash
# Ubuntu/Debian
sudo apt install vim 

# Fedora
sudo dnf install vim

# Arch Linux    
sudo pacman -S vim

# Mac OS X
brew install vim
```

Untuk memastikan vim sudah terpasang, pembaca bisa mengetikkan perintah berikut di terminal: 

```bash
vim
```

Jika Vim sudah terpasang, pembaca akan melihat tampilan seperti berikut: 

![Tampilan Vim](/assets/images/vim/vim.png)

## Cara Menutup Vim

Menutup Vim bisa dilakukan dengan mengetikkan perintah `:q` atau `:quit`. Tapi, sebelum menuliskan perintah tersebut, pastikan untuk menekan tombol `ESC` untuk kembali ke tampilan normal (alasannya kita bahas di bagian selanjutnya). Pastiakn tekan tombol `ENTER` agar perintah aktif. 

![Menutup Vim](/assets/images/vim/vim-quit.png)

Tidak semua orang bisa menutup Vim dengan benar. Bagi yang tidak tahu, bisa saja dengan menutup aplikasi terminal langsung atau dengan restart komputernya. Karena banyak yang tidak tahu cara menutup Vim dengan benar, "how to exit Vim" menjadi sebuah pertanyaan yang sering dibahas di berbagai komunitas. 

## Penutup

Belajar Vim bukan hal yang mudah, tapi jika mau bersabar, tekun dan terus berlatih, skill menggunakan Vim akan membuat kita makin produktif dan efisien dalam menulis kode. Bila sudah menguasainya, tanpa berniat untuk pamer pun, sudah akan terlihat cukup keren karena bisa menguasai salah satu editor yang cukup kompleks ini. 