---
layout: post
title: Memperbaiki "Impossible to create the root directory" Saat Menjalankan PHPUnit
categories: bug-fix solusi test phpunit
---

Apabila terjadi pesan error seperti itu, salah satu kejadiannya ketika menjalankan phpUnit di console (seperti yang saya alami saat ini). Maka solusinya adalah merubah kepemilikan dari directory (folder) tersebut, sehingga phpunit bisa membuat folder yang dibutuhkan.

Berikut perintah untuk merubah kepemilikan directory (saya menggunakan sudo untuk hal ini)

```bash
sudo chown -R <your_name>:_www path/of/your/directory
```

Rubahlah `<your_name>` dengan user anda, dan `_www` adalah nama grup dari web yang saya punya. Kalau mac OS grup yang digunakan ketika menggunakan `nginx` server adalah `_www`, sedangkan OS lain biasanya `www`. Silakan sesuaikan nama grup sesuai OS anda.
Kenapa memakai nama grup dengan `_www` atau `www` kenapa nama grupnya mengguanakan user kita? jawabannya adalah, karena ketika kita menjalankan website kita di browser, maka yg akan mengakses file2 di dalam directory yg ada menggunakan username `_www` atau `www`, bukan usename kita, sehingga web tersebut masih leluasa untuk mengakses (read and write) di directory tersebut.

Setelah menjalankan perintah diatas, maka phpunit kita akan berjalan sebagaimana mestinya. Selamat mencoba