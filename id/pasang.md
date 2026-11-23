---
title: Pasang Sipdb
lang: id
---

## Windows

Pasang Sipdb dari **Microsoft Store**. Paketnya ditandatangani Microsoft,
jadi tidak ada peringatan keamanan, dan Store yang mengupdate Sipdb.

Yang terpasang:

- aplikasi **Sipdb** di menu Start;
- perintah **`sipdb`** di terminal (PowerShell atau Command Prompt), untuk
  yang lebih suka baris perintah atau menjadwalkan sync lewat Task
  Scheduler. Lihat [CLI](../cli/).

Butuh Windows 10 versi 1809 atau lebih baru, atau Windows 11.

Sipdb juga butuh **MySQL atau MariaDB di laptopmu** sebagai database lokal
(misalnya dari XAMPP, Laragon, atau installer MySQL). Database lokal itu
yang diisi Sipdb.

## macOS

Versi macOS sedang disiapkan.

## Copot pemasangan

Copot Sipdb dari **Settings → Apps → Installed apps**.

- **Yang ikut terhapus:** profil koneksi, pengaturan, dan file log Sipdb,
  karena semuanya disimpan di folder paket aplikasi.
- **Yang tetap ada:**
  - password di **Windows Credential Manager** (cari entri `sipdb`) — hapus
    sendiri kalau tidak dipakai lagi;
  - database lokalmu, termasuk schema `_sipdb` yang berisi catatan sync.
    Hapus schema itu kalau Sipdb tidak dipakai lagi.

[Kembali ke panduan](../)
