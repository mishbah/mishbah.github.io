---
layout: post
title: Memperbaiki PDOException Saat Menjalankan PHPUnit
categories: bug-fix solusi
---

Bermula ketika saya mencoba menjalankan PHPUnit di console (Ubuntu 14.04), dan saat test filenya berkaitan dengan database (untuk performa saya menggunakan sqlite) muncul error dengan pesan

```bash
PDOException: could not find driver
```

Untuk mengatasi hal tersebut kita tidak hanya perlu menginstall sqlite (saya menggunakan sqlite3), tetapi juga menginstall php5.6-sqlite (jika menggunakan php versi 5 yang diinstall php5-sqlite) dengan perintah

```bash
sudo apt-get install php5.6-sqlite
```

Setelah terinstall maka PHPUnit dapat dijalankan sebagaimana mestinya. Selamat mencoba