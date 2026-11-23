---
title: Profil koneksi
lang: id
---

Profil menyimpan cara terhubung ke **server produksi** dan ke **database
lokalmu**. Satu profil = satu database server yang disalin ke satu database
lokal.

## Membuat profil

1. Buka Sipdb, pilih **+ Profil baru** di kiri atas.
2. Isi bagian **Server**: host, port (biasanya 3306), user read-only (lihat
   [akun read-only](../akun-read-only/)), password, dan nama database.
3. Isi bagian **Lokal**: host (biasanya `127.0.0.1`), port, user, password,
   dan nama database tujuan. Database lokal yang belum ada dibuat otomatis.
4. Tekan **Tes koneksi**. Sipdb memeriksa hak akun dan menampilkan strategi
   untuk setiap tabel.
5. Tekan **Simpan**.

**Password disimpan di Windows Credential Manager**, tidak di file profil.

## Server di belakang SSH

Kalau server database hanya bisa dijangkau lewat server SSH (bastion), isi
bagian **SSH**: host, user, dan file kunci SSH atau password.

Saat pertama terhubung, Sipdb menanyakan **kunci host** server SSH. Cocokkan
fingerprint-nya dengan yang diberikan admin servermu sebelum menekan
**Percayai**. Kalau kunci itu berubah di kemudian hari, Sipdb menolak
terhubung, karena itu bisa berarti server diganti atau ada penyadapan.

## TLS

Pilih mode TLS sesuai server. `verify-ca` dan `verify-identity` memeriksa
sertifikat server dengan file CA yang kamu berikan.

[Kembali ke panduan](../)
