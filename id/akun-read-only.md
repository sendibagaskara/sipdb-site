---
title: Akun read-only untuk Sipdb
lang: id
---

Sipdb hanya mau memakai akun yang **hanya bisa membaca**. Akun admin atau
akun aplikasi biasa (yang bisa `INSERT`, `UPDATE`, dan seterusnya) ditolak.

Jalankan SQL di bawah **sendiri**, dengan akun admin dan alatmu sendiri
(misalnya HeidiSQL, DBeaver, phpMyAdmin, atau klien `mysql`). Sipdb tidak
pernah meminta atau memakai akun admin.

Ganti tiga hal:

- `<ip-kamu>`: alamat IP tempat Sipdb terhubung. Kalau lewat SSH, ini alamat
  server SSH-nya. Pakai `%` kalau tidak yakin.
- `<password kuat>`: password baru untuk akun ini.
- `app_prod`: nama database yang mau disalin.

## MySQL 8.0.20 ke atas

```sql
CREATE USER 'sipdb'@'<ip-kamu>' IDENTIFIED BY '<password kuat>';
GRANT SELECT, SHOW VIEW ON `app_prod`.* TO 'sipdb'@'<ip-kamu>';
GRANT SHOW_ROUTINE ON *.* TO 'sipdb'@'<ip-kamu>';
```

## MySQL 5.7, dan MariaDB 10.x sampai 11.2

```sql
CREATE USER 'sipdb'@'<ip-kamu>' IDENTIFIED BY '<password kuat>';
GRANT SELECT, SHOW VIEW ON `app_prod`.* TO 'sipdb'@'<ip-kamu>';
GRANT SELECT ON mysql.proc TO 'sipdb'@'<ip-kamu>';
```

## MariaDB 11.3 ke atas

```sql
CREATE USER 'sipdb'@'<ip-kamu>' IDENTIFIED BY '<password kuat>';
GRANT SELECT, SHOW VIEW ON `app_prod`.* TO 'sipdb'@'<ip-kamu>';
GRANT SHOW CREATE ROUTINE ON *.* TO 'sipdb'@'<ip-kamu>';
```

Hak terakhir di setiap contoh (`SHOW_ROUTINE`, `mysql.proc`, `SHOW CREATE
ROUTINE`) hanya untuk menyalin stored procedure dan function. Tanpa hak itu,
tabel dan view tetap tersalin.

## Hosting dengan cPanel

Buat user di menu **MySQL Databases**, tambahkan ke database, lalu centang
**hanya** `SELECT` dan `SHOW VIEW`.

## Memeriksa hasilnya

Di Sipdb, buka halaman **Koneksi** dan tekan **Tes koneksi**. Kalau akunnya
benar, baris Akun berbunyi **LOLOS (hanya hak baca)**. Kalau ditolak, Sipdb
menampilkan hak yang bermasalah dan SQL untuk membuat akun yang benar.

[Kembali ke panduan](../)
