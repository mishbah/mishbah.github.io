---
layout: post
title: Memperbaiki apt-get update error
categories: ["bug fix", solusi]
---

### Pembukaan
Suatu saat saya pernah ingin menginstal sebuah aplikasi, dan saya awali dengan menjalankan perintah

```bash
sudo apt-get update
```

Dan ketika perintah ini selesai diproses, diakhir outputnya (terkadang) muncul tulisan seperti ini

```bash
W: GPG error: http://security.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

Dan biasanya kalau muncul tulisan sejenis diatas, maka perintah untuk menginstall suatu program tidak berhasil, karena update PPA nya tidak berhasil juga, maka perlu dicari jalan keluarnya. Lantas apa solusi untuk permasalahan tersebut ? Silakan melanjutkan membaca tulisan ini sampai selesai :smile:

## Solusinya
Jika permasalahan tersebut muncul, maka solusinya adalah dengan mengetikkan perintah

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KODE_KEY_DARI_YANG_ERROR
```

Untuk sample kode yang error diatas, maka perintahnya seperti ini

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
```

Jadi yang ditulis adalah kode setelah tulisan `NO_PUBKEY`, jika ada 2 maka jalankan perintahnya 2 kali, jika ada 3 maka 3 kali, dan seterusnya. Jika sudah selesai, maka jalankan lagi perintah update list aplikasi seperti perintah yang paling awal (diatas).

InsyaaAllaah output error diatas tidak akan muncul lagi, dan instalasi aplikasi dapat dilakukan. Semoga tulisan singkat ini dapat membantu kita semuanya. Selamat mencoba

sumber: <http://goo.gl/eKwzJN>
