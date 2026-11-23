---
title: Panduan Sipdb
lang: id
---

Sipdb menyalin database produksi MySQL atau MariaDB ke database lokal di
laptopmu, supaya kamu bisa mengembangkan dan menguji dengan data yang mirip
produksi.

- **Server hanya dibaca.** Sipdb hanya mau memakai akun yang bisa membaca,
  dan setiap perintah ke server diperiksa dulu sebelum dikirim.
- **Setelah salinan pertama, yang dibaca hanya yang baru dan berubah**
  (sync cepat). Pemeriksaan penuh sesekali menangkap sisanya, termasuk baris
  yang dihapus di server.
- **Data lokalmu sendiri dibiarkan.** Baris yang kamu tambahkan untuk
  pengujian tidak ikut dihapus.

## Langkah demi langkah

1. [Pasang Sipdb](pasang/)
2. [Buat akun read-only di server](akun-read-only/)
3. [Buat profil koneksi](profil/)
4. [Sync pertama, sync cepat, dan pemeriksaan penuh](sync/)
5. [Jadwal otomatis dan notifikasi](jadwal/)

## Lainnya

- [Memakai Sipdb dari terminal (CLI)](cli/)
- [Keamanan: kenapa server tidak bisa berubah](keamanan/)
- [Kalau ada masalah](masalah/)
- [Kebijakan privasi](privasi/)

[English version](../en/)
