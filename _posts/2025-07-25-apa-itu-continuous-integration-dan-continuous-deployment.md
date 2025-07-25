---
title: Apa yang dimaksud dengan Continuous Integration dan Continuous Deployment (CI/CD)?
date: 2025-07-25
description: Artikel ini akan menjawab secara singkat pertanyaan tentang apa itu CI/CD?
tags: cicd
---

Hari ini kita akan membahas tentang konsep *continuous integration* dan *continuous deployment* atau yang lebih sering dibahas dengan singkatannya yaitu CI/CD. 

## Apa itu CI/CD?

Secara sederhana, **Continuous Integration** (CI) adalah proses dimana developer melakukan *merge* setiap perubahan yang mereka lakukan ke sebuah repository. Setiap *merge* akan secara otomatis menjalankan proses build dan proses. Ide utamanya ialah untuk mendapatkan error lebih cepat sehingga bisa memperbaikinya segera sehingga memastikan *codebase* selalu dalam kondisi terbaik. 

Sementara itu **Continuous Deployment** (CD) akan melanjutkan proses sebelumnya untuk secara otomatis melakukan *deploy* pada setiap *automated test* ke *production* (atau environment manapun). Hal ini membuat software yang kita buat selalu memiliki rilis terbaru.

## Mengapa menerapkan CI/CD?

CI/CD membantu kita menemukan bug lebih cepat, mengurangi masalah integrasi, memastikan kode yang di push selalu dalam kondisi siap di deploy. Apalagi, proses ini semuanya berjalan secara otomatis sehingga meurangi waktu dan *effort* untuk melakukan semua proses deployment. 

## Bagiamana cara kerja CI/CD?

- **Commit**: Pertama kita melakukan perubahan kode lalu melakukan *commit*. 
- **Push**: Lalu perubahan di atas kita upload ke *repository* bersama. Proses ini bisa dilakukan dengan push biasa (bila punya hak akses) atau biasanya akan melalui proses *peer review* lewat mekanisme *pull request* atau *merge request*. 
- **Automated Build**: Ketika kode yang kita tulis sudah masuk ke repository, maka server CI akan mengambil perubahan terakhir lalu melakukan proses build. Proses ini memastikan perubahan sebelumnya bis terinterasi dengan kode sekarang. 
- **Automated Test**: Bila build sudah sukses, maka server CI selanjutnya akan melakukan *automated test* (meskipun dalam beberapa kasus bisa saja suatu project tidak menerapkannya). 
- **Feedback**: Bila terjadi error yang menyebabkan proses gagal ataupun ketika prosesnya berhasil dengan benar, server CI akan memberikan informasi. Informasi ini bisa lewat email, notifikasi slack, notifikasi telegram, atau lewat berbagai kanal lain. Pada umumnya server CI akan mendukung banyak cara untuk memberikan *feedback* agar developer mendapat informasi terbaru dengan cepat. 
- **Deploy**: Apabila proses build sukses, maka selanjutnya adalah deployment. Kita bisa mengaturnya agar masuk ke server staging untuk pengujian *end to end* atau bahkan mengaturnya masuk ke server production. 

## Solusi CI/CD

- Github Actions: Solusi CI dari Github yang terintegrasi dengan setiap repository.
- Gitlab CI/CD: Mirip seperti Github, Gitlab pun memiliki layanan CI.
- Jenkins: Server otomasi *open source*. Meskipun gratis harus punya pengetahuan tentang server secara umum agar bisa di setup. 
- Travis CI: Server CI cloud-based yang mudah di integrasikan dengan GitHub. 
- CircleCI: Solusi pihak ketiga lain yang mudah di integrasikan dengan GitHub, GitLab, maupun Bitbucket. 
- BitRise: Solusi CI/CD untuk mobile development. 
- CodeMagic: Mirip seperti BitRise juga untuk mobile development.

Implementasi CI/CD sangat direkomendasikan baik untuk web maupun mobile app. Bila belum pernah punya pengalaman, saran penulis cobalah dengan GitHub Actions karena sudah tersedia langsung di GitHub. Secara pribadi penulis pernah menggunakan GitHub, GitLab, Jenkins dan BitRise. Setiap layananan punya kelebihan dan kekurangan masing-masing, tapi tujuan akhirnya sama, meminimalisir kerja developer setelah melakukan push code sampai bisa ter-deploy ke server. 

https://mail.google.com/mail/u/1/#inbox/FMfcgzQbgRpRhlckHSmwzjmLQwGbLHpk