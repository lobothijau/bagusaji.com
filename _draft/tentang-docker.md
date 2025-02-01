Docker bisa berarti salah satu dari dua hal berikut:

1. Docker sebagai teknologi container, atau
2. Docker sebagai sebuah perusahaan (Docker Inc.)

## Docker sebagai Perusahaan

Mari kita bahas sedikit sejarah awal pengembangan Docker sebagai sebuah perusahaan. Perusahaan ini sebelum menjadi Docker Inc. awalnya bernama *dotCloud*. Perusahaan ini didirikan oleh Solomon Hykes pada tahun 2010. 

Perusahaan *dotCloud* memberikan layanan container bagi perusahaan client  dengan sebuah tool buatan sendiri untuk mengelola container tersebut melalui sebuah *platform as a service*. Tool yang mereka kembangkan ini bernama *Docker*. 

Pada tahun 2013, bisnis *dotCloud* mulai menurun. Solomon Hykes kemudian memutuskan untuk membuat perusahaan baru yang akan mengembangkan *Docker* sebagai produk utamanya. Perusahaan ini kemudian diberi nama *Docker Inc.* dengan impian membawa teknologi container dan software yang mereka kembangkan ke seluruh dunia. 

## Open Container Initiative (OCI)

OCI adalah sebuah organisasi yang didirikan pada tahun 2015. Organisasi ini bertujuan untuk memastikan bahwa teknologi container yang dikembangkan oleh Docker Inc. bisa digunakan oleh semua orang. 

Dahulu, ada sebuah perusahaan yang bernama *CoreOS* yang juga mengembangkan sebuah teknologi container yang bernama *rkt*. Karena ada ketidaksetujuan atas spesifikasi container yang dikembangkan oleh Docker Inc., CoreOS kemudian membuat sebuah spesifikasi baru bernama *appc*. Berdasarkan spesifikasi yang mereka tentukan, CoreOS kemudian membuat sebuah software container sendiri yang bernama *rkt*. 

Untuk mencegah dua standar yang saling berkompetisi, disusunlah sebuah organisasi yang bernama *Open Container Initiative* (OCI). OCI ini bertujuan untuk menaungi bagaimana teknologi container bisa dikembangkan oleh semua orang tanpa harus tunduk pada satu perusahaan saja. Saat ini ada tiga spesifikasi container yang dikembangkan oleh OCI, yaitu:

1. Runtime Container (runtime-spec)
2. Image Format (image-spec)
3. Distribution Format (distribution-spec)

Kembali penulis ingatkan bahwa container merupakan teknologi yang sangat kompleks yang penulis sendiri belum bisa memahami semua bagiannya. Di seri artikel belajar docker ini, kita hanya akan fokus tentang penggunaan container sehari-hari seperti:

- bagaimana membuat image
- bagaimana menjalankan container
- bagaimana mengelola container
- bagaimana mendistribusikan image ke sebuah server
- dst.
