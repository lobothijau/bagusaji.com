Dahulu kala, bila ingin mempublikasikan suatu website atau dalam istilah kerennya, men-*deploy* suatu website ke *environment* production, kita harus memiliki sebuah server. Satu server untuk satu website. 

Hardware itu mahal, sementara tidak semua website bisa memaksimalkan kemampuan hardware tersebut secara optimal. Jika memiliki 3 website yang di-deploy di tiga server, sementara penggunaannya hanya 5-15% dari kemampuan hardware tersebut, maka ada banyak sumber daya yang tidak terpakai dengan baik. 

Sebetulnya secara teknis, satu server bisa menampung banyak website. Software seperti Apache & Nginx bisa diatur sehingga bisa menangani beberapa website sekaligus. Tetapi, cara seperti ini memiliki kekurangan, apabila salah satu software mengalami error (misalnya ada corrupt di versi PHP atau konfigurasi nginx ada yang salah), maka semua website yang ditangani oleh server tersebut akan down secara bersamaan. 

## Virtualisasi

Ada solusi lain agar bisa memaksaimalkan sumber daya hardware dengan lebih optimal sehingga bisa menangani beberapa website sekaligus namun setiap website tidak saling berpengaruh. Teknologi yang bernama *virtualisasi* memungkinkan kita untuk membuat sebuah komputer virtual (*virtual machine* atau VM) didalam sebuah komputer fisik. Bila pernah mendengar nama VMWare atau VirtualBox, itulah salah dua contoh dari aplikasi yang memanfaatkan teknologi ini. 

Berkat teknologi virtualisasi, di dalam sebuah komputer bisa dibuat beberapa komputer virtual. Meskipun virtual, software yang di dalamnya bisa berjalan seolah-olah berada di komputer tersendiri. Artinya apabila salah satu VM mengalami kendala, maka hanya website yang berada di VM tersebut yang akan bermasalah, tidak mempengaruhi website yang ada di VM lainnya. 

## Container

Meskipun VM bisa menawarkan solusi yang bisa memaksimal penggunaan sumber daya server, namun VM masih belum sempurna. 

- Setiap VM akan membutuhkan sistem operasi masing-masing.
- Setiap sistem operasi yang dijalankan di dalam VM mengkonsumsi CPU, RAM dan sumber daya. 
- Setiap sistem operasi perlu dikelola secara terpisah (update sistem keamanan, update sistem operasi, dll).
- Setiap VM butuh waktu lama untuk booting. 
- VM kurang portable sehingga memindahkan VM dari satu server ke server yang lain tidak mudah.

Container diciptakan untuk mengatasi kekurangan VM. Ia adalah sebuah software yang memanfaatkan teknologi virtualisasi, namun dengan cara yang lebih ringkas dan ringan. Sebuah server yang hanya bisa memiliki 10 VM, bisa menjalankan puluhan bahkan ratusan container. Hal ini tentu saja membuat pemanfaatan sumber daya server menjadi lebih optimal. 

**Docker** adalah sebuah software yang membuat teknologi sekompleks container menjadi lebih mudah digunakan bagi semua orang. Ada banyak teknologi container lain sebelum Docker, tapi Docker lah yang membuat container menjadi sepopuler ini. 