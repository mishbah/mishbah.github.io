---
layout: post
title: Perintah (Dasar) Ubuntu
categories: tutorial
---

### Pembukaan
Karena saya pengguna ubuntu, maka untuk mengingat perintah2 pada ubuntu melalui terminal, maka saya akan memubat daftar perintah dan kegunaannya.

### Catatan:

* Semua perintah berikut, kita jalankan didalam terminal (command prompt).
* Tulisan ini akan terus kita update, sesuai dengan kebutuhan

## Install dan uninstall
Kita sering install aplikasi ataupun kalau ternyata aplikasi yang kita install atau sudah terinstall tidak kita inginkan, maka yang kita lakukan adalah uninstall. Berikut perintahnya:

```bash
# perintah penambahan PPA
sudo apt-add-repository ppa:nama_ppa-nya

# perintah update list aplikasi.
# jika menambahkan PPA maka perintah ini biasanya harus dijalankan
sudo apt-get update

# untuk install
sudo apt-get install nama_aplikasinya

# untuk uninstall
sudo apt-get remove nama_aplikasinya

# perintah penghapusan PPA (jika awalnya kita menambahkan PPA, sifatnya optional)
sudo apt-add-repository --remove ppa:nama_ppa-nya

# perintah menghapus segala hal yg berkaitan dengan aplikasi (data, setingan, dll, sifatnya optional)
sudo apt-get purge nama_aplikasinya

# perintah menghapus segala aplikasi depedensi yang sudah tidak dibutuhkan lagi (sifatnya optional)
sudo apt-get autoremove
```

### Apa itu PPA ?
PPA singkatan dari **Personal Package Archive**, dimana kita bisa menambahkan aplikasi yang tidak disediakan secara _official_ oleh ubuntu. Jadi aplikasi berbasis komunitas

sumber dari PPA: <https://goo.gl/mXeLyb>  
sumber dari perintah install uninstall: <http://goo.gl/4l38Jg>
