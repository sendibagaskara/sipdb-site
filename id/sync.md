---
title: Sync dan pemeriksaan penuh
lang: id
---

## Sync pertama

Di **Dashboard**, tekan **Sync sekarang**. Sipdb menyalin tabel, view,
routine, dan trigger (lihat di bawah) dari server ke database lokal, sedikit
demi sedikit supaya server tidak terbebani.

Sebelum menulis apa pun, Sipdb bisa bertanya:

- **Tabel lokal sudah berisi data** (misalnya sisa dump manual): anggap
  salinan server, atau anggap data milikmu yang tidak pernah disentuh.
- **Trigger lokal belum dibungkus:** bungkus supaya trigger tidak ikut
  berjalan saat Sipdb menulis, tapi tetap berjalan untuk aplikasimu.
- **Struktur kolom di server berubah** dan nilai lokal bisa ikut berubah:
  ubah kolom lokal, atau lewati tabel itu dulu.

Sync bisa dihentikan kapan saja (**Hentikan** atau **Jeda**). Sync berikutnya
melanjutkan dari tempat terakhir.

## Sync cepat

Setelah sync pertama, setiap sync hanya membaca baris yang **baru atau
berubah** di server, lewat index. Biasanya hanya beberapa detik.

- **Editanmu di lokal aman** selama server tidak mengubah baris yang sama.
  Kalau server mengubahnya, versi server yang dipakai, dan Riwayat mencatat
  editan yang tertimpa.
- **Yang tidak ditangkap sync cepat:** baris yang dihapus di server, dan
  tabel tanpa kolom waktu ber-index. Itu tugas pemeriksaan penuh.

## Pemeriksaan penuh

**Periksa penuh** membandingkan setiap tabel dengan server per blok, lalu
memperbaiki yang berbeda, termasuk menghapus baris yang sudah dihapus di
server.

- Baris yang kamu buat sendiri di lokal **tidak pernah dihapus**.
- Pemeriksaan penuh lebih berat untuk server. Jalankan saat server sepi,
  atau jadwalkan di malam hari (lihat [jadwal](../jadwal/)).
- Ada batas waktu per run; tabel yang belum selesai dilanjutkan di
  pemeriksaan berikutnya.

## Trigger

Akun read-only tidak bisa membaca trigger server. Kalau servermu punya
trigger, ekspor definisinya dengan akun admin di alatmu sendiri, lalu
impor di halaman **Objek** → **Import trigger**. Sipdb menampilkan perintah
`mysqldump` yang tepat.

[Kembali ke panduan](../)
