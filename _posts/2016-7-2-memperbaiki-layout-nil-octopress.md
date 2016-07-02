---
layout: post
title: Memperbaiki Layout Nil Octopress
categories: ["bug fix", solusi]
---

### Pembukaan
Selain baru belajar jekyll, saya tertarik untuk menggunakan octopress. Dan ketika saya mencoba memasang theme baru, muncul warning. Dan pada kesempatan inilah kita akan membahas salah satu warningnya yaitu `Layout 'nil'`. Outputnya seperti ini

```bash
Build Warning: Layout 'nil' requested in blog/tags/git/atom.xml does not exist.
```

Jika ada tulisan tersebut, maka ada file layout yang berisi `nil`. Dan ini tidak dikenali pada jekyll versi 3 keatas (CMIIW).

## Solusinya
Jika permasalahan tersebut muncul, maka solusinya adalah dengan mencari file yang bersangkutan, dalam perintah diatas adalah file `atom.xml`. Dan rubah baris

```bash
layout: nil
```

Menjadi

```bash
layout: null
```

Rubah semua file yang terdapat pada warning, maka insyaaAllaah warningnya tidak akan muncul lagi. Selamat mencoba

sumber: <http://goo.gl/xmaAqW>
