Beberapa tahun terakhir ini saya sudah mempelajari konsep-konsep pemrograman web dengan Ruby on Rails. Hanya sjaa, karena kurang populer dibandingkan dengan Laravel, kesempatan untuk mengerjakan sebuah project komersil lebih kecil karena kurangnya *circle* yang bekerja dengan Rails. 

Ditahun 2025 ini, daripada menunggu adanya project komersil yang menggunakan Rails, penulis putuskan untuk membuat sebuah aplikasi web dengan Rails 8. Aplikasi ini adalah aplikasi yang meniru layanan dari [Letterboxd](https://letterboxd.com).

## Apa itu Letterboxd?

Letterboxd adalah sebuah layanan sosial media bagi pecinta film. Layanan ini memungkinkan pengguna untuk menulis review, mencatat daftar film yang telah ditonton, dan membuat daftar film yang ingin ditonton dan membagikannya, serta berinteraksi dengan pengguna lain. 

Meniru semua fitur yang dimiliki oleh Letterboxd, tentu saja tidak akan mudah karena Letterboxd memiliki banyak fitur yang kompleks. Oleh karena itu, penulis membatasi diri untuk hanya meniru fitur-fitur yang paling penting saja.

## Fitur-fitur yang akan diimplementasikan

- User bisa melihat daftar film populer, top rated dan sebagainya. 
- User bisa mencatat film yang telah ditonton dan menulis review.
- User bisa membuat daftar film yang ingin ditonton (watchlist).
- User bisa membagikan daftar film dan membagikannya (List) juga bisa melihat daftar film yang dibagikan oleh pengguna lain.
- User bisa berinteraksi dengan pengguna lain melalui like, comment, dan sebagainya.

Daftar fitur di atas mungkin terlihat sederhana, tapi banyak hal yang perlu dilakukan agar ia dapat berjalan dengan baik. 

## Implementasi

Website ini akan dikerjakan dengan Ruby on Rails 8. Setiap interaksi yang membutuhkan JavaScript akan dikerjakan dengan framework yang telah disediakan, bisa dengan Hotwire, Stimulus, Turbo atau yang lainnya. 

Untuk data film tentu saja akan memanfaatkan data dari [The Movie Database](https://www.themoviedb.org/). Hanya saja, penulis juga ingin agar web ini tidak hanya memiliki data film tapi juga anime dalam satu wadah. 