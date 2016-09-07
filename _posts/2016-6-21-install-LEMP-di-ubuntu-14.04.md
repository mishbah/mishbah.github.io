---
layout: post
title: Install LEMP (Linux, Nginx, MySql, PHP) di Ubuntu 14.04 LTS
categories: tutorial
---

Karena spesialisasi saya di bidang web programming, maka menginstall LEMP merupakan kegiatan yang sering saya lakukan. Oleh karena itu, biar tidak sering search di google, lebih baik saya simpan ingatan saya pada tulisan ini (yang sudah terbukti berhasil terinstall di pc dan laptop saya).

Pada tulisan saya kali ini saya tidak akan membahas bagaimana menginstall linux, saya akan langsung menginstall Nginx, MySQL, dan PHP. Ok tidak berpanjang dan berlebar lagi, selamat membaca :books:

## 1. Install Nginx
Untuk menginstall nginx buka terminal, dan ketik langkah berikut

```
sudo apt-get update
sudo apt-get install nginx
```

Setelah terinstall, maka nginx sudah siap, dan sudah halaman defaultnya sudah dapat diakses. Kita dapat mengeceknya dengan mengunjungi [localhost](http://localhost){:target="_blank"}

Jika tampilannya seperti gambar dibawah ini, maka kita berhasil menginstall nginx
![Nginx default welcome page](/images/default_page_of_nginx.png)

## 2. Install MySQL
Untuk menginstall MySQL ketik langkah berikut di terminal

```
sudo apt-get install mysql-server
```

Kita akan dimintai password untuk user `root` (administrator). Setelah instalasi selesai, ada beberapa langkah yang harus kita lakukan yaitu dengan mengetik:

```
sudo mysql_install_db
```

Perintah diatas untuk menseting database pada MySQL. Kemudian untuk keamanan kita lanjut dengan mengetik

```
sudo mysql_secure_installation
```

Masukkan password yang kita ketik sebelumnya, dan ikuti langkah2 yang ada pada layar terminal. Catatan: jika kita ditanya tentang pergantian password, maka jika kita tidak mau merubahnya, tinggal tekan `N` untuk tidak dan tekan enter.

Setelah semuanya dilakukan coba ketik

```
mysql -V
```

Jika keluar output seperti ini

```
mysql  Ver 14.14 Distrib 5.5.49, for debian-linux-gnu (x86_64) using readline 6.3
```

Maka MySQL terinstall dengan benar

## 3. Install PHP
Saat ini saya ingin menginstall PHP v 5.6, untuk menginstall PHP versi 5.6 maka lakukan langkah berikut

```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
```

Tekan ENTER, jika terdapat error, maka kita install python-software-properties dengan mengetik

```
sudo apt-get install python-software-properties
```

Dan ketik lagi perintah sebelumnya kemudian ketik perintah berikut

```
sudo apt-get update
sudo apt-get install php5.6-fpm php5.6 php5.6-mysql
```

### Konfigurasi PHP
Agar PHP lebih aman maka perlu dikonfigurasi. Buka file `/etc/php5/fpm/php.ini` dengan perintah

```
sudo nano /etc/php5/fpm/php.ini
```

Cari baris dengan tulisan `cgi.fix_pathinfo`. dan ganti dari angka `1` menjadi angka `0` sehingga baris tulisan tersebut menjadi

```
cgi.fix_pathinfo=0
```

Simpan file tersebut, dan restart PHP dengan perintah

```
sudo service php5.6-fpm restart
```

Dengan merestart, maka perubahan yang telah kita edit akan terimplementasi

## 4. Konfigurasi Nginx untuk menggunakan PHP
Agar php dapat berjalan di server Nginx maka perlu konfigurasi. Untuk itu perlu diganti dengan membuka file `/etc/nginx/sites-available/default` dengan mengetik perintah berikut

```
sudo nano /etc/nginx/sites-available/default
```

Jika comment pada konfigurasi nginx dihilangkan, maka akan seperti ini

```
server {
    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

    root /usr/share/nginx/html;
    index index.html index.htm;

    server_name localhost;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Akan berubah menjadi seperti berikut

```
server {
    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

    root /usr/share/nginx/html;
    index index.php index.html index.htm;

    server_name localhost;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page 404 /404.html;
    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
        root /usr/share/nginx/html;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/var/run/php/php5.6-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
```

Setelah diganti jangan lupa kita simpan dan restart Nginx-nya agar perubahan dari setingan kita terimplementasikan dengan mengetikkan perintah

```
sudo service nginx restart
```

Jika konfigurasinya tidak ada kesalahan maka akan tampak seperti gambar berikut ini
![Restart Nginx](/images/restart-nginx-ok.png)

Selesai sudah kita menginstall LEMP, selamat mencoba :ok_hand: