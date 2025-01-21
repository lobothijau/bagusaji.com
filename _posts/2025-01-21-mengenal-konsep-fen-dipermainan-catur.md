---
title: Mengenal Konsep FEN (Forsyth-Edwards Notation) di Permainan Catur
date: 2025-01-21 10:00:00 +0700
description: Mengenal Konsep FEN (Forsyth-Edwards Notation) di Permainan Catur
tags: [catur]
---

Membahas catur kok di blog pemrograman? *Well*, sebagai programmer yang juga pecinta catur  penulis tentu cukup familiar dengan konsep-konsep catur di komputer, sehingga kali ini penulis rasa menyinggung catur bisa menjadi variasi diantara artikel-artikel pemrograman yang sudah ada. 

Pembaca harus pahami bahwa catur sudah tidak bisa dipisahkan lagi dari komputer. Banyak turnamen resmi memang masih diselenggarakan dengan cara yang tradisional, tapi diluar pertandingan, catur akan selalu berurusan dengan komputer (baik itu desktop maupun mobile). Kita bisa main catur di komputer, kita juga bisa menonton pertandingan catur di komputer, bahkan kita bisa belajar catur di komputer. Selain ketiga kegiatan tadi, satu kegiatan lain yang sering kita lakukan adalah membagikan posisi papan catur kepada teman kita. 

Saat membagikan posisi papan catur, kita bisa membagikan foto kondisi papan atau dengan membagikan diagram papan catur secara digital. Pertanyaannya, bagaimana komputer itu bisa mendeskripsikan sebuah posisi di atas papan catur? Bagaimana caranya menentukan bahwa ada pion di b3, ada raja di d5, atau ada kuda di f7? Jawabannya adalah dengan menggunakan FEN.

FEN adalah singkatan dari Forsyth-Edwards Notation, yang digunakan untuk menggambarkan susunan papan dalam permainan catur. Steven J. Edwards, yang mencetuskan FEN adalah seorang programmer yang berasal dari Amerika Serikat. Ia mengimplementasikan konsep yang diperkenalkan oleh jurnalis dan penulis catur, David Forsyth. Maka dari itu nama konsep ini menggunakan nama keduanya. FEN memungkinkan pemain dan program komputer untuk memahami posisi papan catur secara akurat. 

Kode FEN dibawah ini menggambarkan posisi awal permainan:

`rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1`

<img class="mx-auto" src="/assets/images/posts/fen-original-position.gif" alt="FEN" style="width: 350px;">

Bagaimana prosesnya? Mari kita bahas satu per satu.

## Posisi Bidak

Apabila pembaca perhatikan, delapan bagian pertama yang dipisahkan oleh `/` adalah posisi bidak di masing-masin baris dimulai dari posisi hitam (dalam diagram catur, hitam berada di bagian atas dan pada umumnya komputer akan memproses suatu matriks dimulai dari atas ke bawah atau dari kiri ke kanan). 

Bagian pertama adalah `rnbqkbnr`, ini merupakan posisi bidak hitam di baris pertama (bidak hitam selalu dinyatakan dengan huruf kecil). Harap ingat bahwa setiap bidak akan menggunakan istilah dalam bahasa Inggris. Berikut adalah istilah bidak hitam:

- `r` : Rook (gajah)
- `n` : Knight (kuda)
- `b` : Bishop (gajah)
- `q` : Queen (menteri/ratu)
- `k` : King (raja)
- `p` : Pawn (pion)

Bagian kedua adalah `pppppppp`, ini merupakan posisi bidak hitam di baris kedua. 

Bagian ketiga sampai bagian keenam ditulis 8. Angka 8 ini menunjukkan kotak kosong yang tidak memiliki bidak. 

Sekarang, mari kita berlatih. Untuk posisi di bawah ini, seperti apa kode FENnya?

![](/assets/images/posts/fen-quiz-1.png)

1. Kita mulai dari posisi paling kiri, ada dua pion berarti `pp`. 
2. Ada satu kotak kosong, berarti `1`, bila kita gabungkan menjadi `pp1`.
3. Kemudian ada satu pion, berarti `p`, bila kita gabungkan menjadi `pp1p`.
4. Lanjutkan dengan dua kotak kosong, berarti `2`, bila kita gabungkan menjadi `pp1p2`.
5. Terakhir, ada dua pion, berarti `pp`, bila kita gabungkan menjadi `pp1p2pp`.

Mari kita lanjutkan setelah empat angka 8, adalah `PPPPPPPP/RNBQKBNR`. Bisa ditebak? Betul, ini merupakan posisi bidak putih di kedua dan pertama dengan aturan yang sama dengan posisi hitam, hanya saja bidak putih selalu dinyatakan dengan huruf kapital. 

Baik, mari kita uji lagi pemahaman pembaca dengan mengubah posisi berikut ke dalam notasi FEN.

<img class="mx-auto" src="/assets/images/posts/fen-quiz-2.gif" alt="FEN" style="width: 350px;">

1. Pada baris pertama, ada satu buah benteng hitam, berarti `r`, diikuti satu kotak kosong, menjadi `r1`. Kemudian ada gajah dan menteri, menjadi `r1bq`. Lalu ada satu kotak kosong, menjadi `r1bq1`. Lalu ada benteng dan raja, menjadi `r1bq1rk`. Diakhiri oleh dua kotak kosong menjadi `r1bq1rk1`.
2. Pada baris kedua ada tiga buah pion, berarti `ppp`, diikuti dengan dua kotak kosong, menjadi `ppp2`. Lalu ada tiga buah pion, menjadi `ppp2ppp`. 
3. Pada baris ketiga ada dua kotak kosong, berarti `2`, diikuti dengan satu kuda, menjadi `2n`. Lalu ada dua buah pion, menjadi `2npp`. Ada satu kuda lagi, menjadi `2nppn`, diakhiri dua kotak kosong menjadi `2nppn2`.
4. Pada baris keempat ada enam kotak kosong, berarti `6`, diikuti dengan satu **gajah putih**, menjadi `6B` (ingat putih selalu kapital). Diakhiri dengan satu kotak kosong menjadi `6B1`.
5. Pada baris kelima dimulai dengan kotak kosong, berarti `1`, diikuti oleh gajah hitam dan gajah putih, menjadi `1bB`. Lalu ada dua buah pion, menjadi `1bBpp`. Diakhiri tiga kotak kosong menjadi `1bBpp3`.
6. Pada baris keenam ada dua buah kotak kosong, berarti `2`, diikuti oleh kuda putih, menjadi `2N`. Lalu ada dua kotak kosong diikuti pion putih, menjadi `2N2P` dan dikahiri dengan dua kotak kosong menjadi `2N2P2`.
7. Pada baris ketujuh ada tiga pion diikuti oleh menteri putih, menjadi `PPPQ`. Kemudian ada kuda putih dengan 1 kotak kosong, menjadi `PPPQN1`. Lalu tiga pion putih, menjadi `PPPQN1PPP`. Diakhiri dengan dua kotak kosong menjadi `PPPQN1PPP2`.
8. Baris terakhir ada dua kotak kosong, berarti `2`, diikuti oleh raja putih, menjadi `2K`. Kemudian ada benteng, tiga kotak kosong dan benteng, menjadi `2KR3R`. 

Jadi, kode FENnya adalah `r1bq1rk1/ppp2ppp/2nppn2/6B1/1bBPP3/2N2P2/PPPQN1PP/2KR3R`.

Selamat, pembaca sudah menguasai konsep posisi bidak dalam notasi FEN. 

## Siapa yang Jalan Berikutnya? 

Setelah mendesripsikan posisi bidak di atas papan, FEN menentukan siapa yang akan jalan berikutnya. Melihat kode FEN yang pertama, pemain yang jalan berikutnya adalah pemain putih. Perhatikan bagian `w` yang berarti white (putih). Untuk giliran hitam akan tertulis `b` yang artinya black (hitam).

```
// Giliran putih
rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1

// Giliran hitam
rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR b KQkq - 0 1
```

## Rokade

Bagian berikutnya memberitahu kita apakah rokade dapat dilakukan atau tidak. KQkq artinya putih dan hitam masih bisa melakukan rokade sayap raja maupun sayap menteri

<img class="mx-auto" src="/assets/images/posts/fen-castling.gif" alt="FEN" style="width: 350px;">

Pada diagram di atas, apakah pembaca bisa menebak kondisi rokadenya? Karena Putih bisa rokade ke sayap menteri tapi tidak bisa ke sayap raja maka hanya ditulis `Q`. Begitu pula dengan hitam, karena hanya bisa ke sayap raja tapi tidak bisa ke sayap menteri maka hanya ditulis `k`. Sehingga bila digabungkan menjadi `Qk`. Posisi lengkap diagram di atas bila dituliskan dalam FEN adalah `4k2r/6r1/8/8/8/8/3R4/R3K3 w Qk - 0 1`.

## En Passant

Posisi berikutnya mendeskripsikan kemungkinan langkah en passant. 

<img class="mx-auto" src="/assets/images/posts/fen-en-passant.gif" alt="FEN" style="width: 350px;">

Pada contoh diagram di atas, karena ada bidak hitam di d4, maka langkah putih ke e4 memberikan kemungkinan en passant di e3. Notasi lengkap yang menunjukkan kemungkinan en passant tersebut adalah sebagai berikut:

```
rnbqkbnr/ppp1pppp/8/8/3pP3/8/PPPP1PPP/RNBQKBNR b KQkq e3 0 1
```

Bila tidak ada kemungkinan en passant, maka akan ditulis `-` seperti pada contoh posisi awal. 


## Halfmove Clock dan Fullmove Number

Dua bagian terakhir pada suatu FEN adalah `halfmove clock` dan `fullmove number`. 

```
8/p7/8/1N2k2q/8/5n2/PPP5/1K1N4 b - - 3 38
```

Angka `3` adalah `halfmove clock`. Halfmove clock merupakan sebuah cara untuk mengplikasikan aturan *50 move rule* (aturan 50 langkah). Aturan ini menyatakan apabila dalam 50 langkah tidak ada pion yang melangkah atau dipukul, maka permainan bisa dianggap draw. Angka ini di reset setiap kali ada pion yang melangkah atau dipukul. 

Angka `38` adalah `fullmove number`. Angka ini akan dinaikkan setiap kali hitam melangkah. 


## Kesimpulan

Banyak juga yang sudah kita pelajari di artikel ini. Tapi sebenarnya pembaca tidak harus selalu menerjemahkan kode FEN secara manual. FEN diciptaka untuk memudahkan komunikasi antara pemain dan program komputer. Kita jarang harus berurusan seara langsung dengan kode FEN, mayoritas akan dituliskan oleh program komputer, sehingga yang kita lakukan biasanya hanya membagikan kodenya saja. 

Tetapi sebagai pemain catur, bisa memahami konsep FEN akan memudahkan kita untuk memahami hubungan antara permainan catur dengan komputer dan bagaimana komputer melihat suatu susunan papan. 