---
layout: post
title: Install Composer di Ubuntu 14.04 LTS
---

### Pembukaan
[Composer](http://getcomposer.org) adalah manajemen depedensi yang populer untuk bahasa pemrograman PHP. Kemampuannya untuk memilihkan versi depedensi yang sesuai dengan requirement dari program PHP yang kita miliki.

Berikut kita akan menunjukkan cara install composer di Ubuntu 14.04

## Kebutuhan
Untuk tutorial ini, kita sudah memiliki:

* Sistem operasi Ubuntu 14.04 LTS
* Memiliki user yang memiliki sudo permission

## 1. Install beberapa depedency
Sebelum menginstall composer, maka dibutuhkan beberapa program yang terinstall. Berikut perintah untuk menginstallnya

```bash
sudo apt-get update
sudo apt-get install curl php5.6-cli git
```

`curl` digunakan untuk mendownload Composer, `php5.6-cli` untuk menjalankan script yang telah didownload oleh `curl`, dan `git` digunakan Composer untuk mendownload _depedency_ yang dibutuhkan

## 2. Install Composer
Untuk menginstall composer bisa dengan mengetik perintah berikut

```bash
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```

Dengan perintah ini kita akan mendownload dan menginstall `composer` pada folder `/usr/local/bin`. Untuk mengecek apakah composer sudah terinstall, dapat mengeceknya dengan perintah

```bash
composer
```

Dan akan terlihat output seperti berikut

```bash
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 1.1.2 2016-05-31 19:48:11.
Usage:
  command [options] [arguments]

Options:
  -h, --help                     Display this help message
  -q, --quiet                    Do not output any message
  -V, --version                  Display this application version

...
```

Selamat mencoba :fist:

sumber: <https://goo.gl/AczjXr>