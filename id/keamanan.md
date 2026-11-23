---
title: Keamanan
lang: id
---

Sipdb dibuat untuk satu janji: **server produksimu tidak pernah berubah
karena Sipdb.** Janji itu dijaga empat lapis, dan setiap lapis berdiri
sendiri:

1. **Akun yang hanya bisa membaca.** Sebelum membaca data apa pun, Sipdb
   memeriksa hak akun di server. Akun yang bisa menulis, atau yang haknya
   tidak bisa dipastikan, ditolak.
2. **Sesi read-only.** Setiap koneksi ke server diminta menjadi sesi
   read-only di sisi server.
3. **Penjaga perintah.** Setiap perintah diperiksa di laptopmu sebelum
   dikirim. Yang bukan bacaan (misalnya `INSERT`, `UPDATE`, `DELETE`,
   `CREATE`, `DROP`, atau `SELECT … FOR UPDATE`) diblokir dan tidak pernah
   sampai ke server.
4. **Diuji di setiap versi.** Sebelum dirilis, Sipdb dijalankan ke enam
   versi MySQL dan MariaDB, dan log server membuktikan hanya ada perintah
   baca.

Sipdb juga **menjaga beban server**: data dibaca per batch kecil lewat
index, berhenti sebentar kalau server sedang sibuk, dan memakai satu koneksi
saja.

## Password

Password server, database lokal, dan kunci SSH disimpan di **Windows
Credential Manager**, bukan di file. Password tidak pernah ditulis ke log,
support bundle, atau ditampilkan di aplikasi.

## Database lokalmu

Sipdb hanya menulis ke database lokal di profil, dan menolak menulis kalau
database lokal ternyata server yang sama dengan server produksi. Baris yang
kamu buat sendiri di lokal tidak pernah dihapus.

[Kembali ke panduan](../)
