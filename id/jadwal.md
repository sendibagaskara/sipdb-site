---
title: Jadwal otomatis dan notifikasi
lang: id
---

Di halaman **Jadwal**:

- **Sync cepat** setiap 15 menit, 30 menit, 1 jam, atau 4 jam;
- **Pemeriksaan penuh** sekali per malam di jendela waktu yang kamu pilih
  (default 01:00–05:00), dengan batas waktu per run.

Tekan **Simpan jadwal**. Sync cepat pertama berjalan satu interval kemudian;
membuka aplikasi tidak langsung menghubungi server.

## Tray

Selama ada jadwal yang aktif, menutup jendela **menyembunyikan Sipdb ke
tray** (ikon di pojok kanan bawah) dan jadwal tetap berjalan. Dari menu ikon
itu kamu bisa membuka Sipdb, sync sekarang, menjeda, menghentikan, atau
keluar.

Jadwal hanya berjalan selama Sipdb terbuka atau ada di tray. Kalau laptop
mati saat jendela pemeriksaan penuh, Dashboard mengingatkan dan menawarkan
**Periksa sekarang**.

## Sync otomatis tidak pernah bertanya

Kalau sync otomatis butuh jawaban (misalnya tabel lokal yang sudah berisi
data, atau kunci host SSH baru), sync itu berhenti tanpa menulis apa pun.
Buka Sipdb dan tekan **Sync sekarang** untuk menjawab.

## Notifikasi

Sipdb menampilkan notifikasi Windows kalau:

- sync otomatis gagal;
- sync otomatis butuh jawabanmu;
- jendela pemeriksaan penuh lewat tanpa pemeriksaan.

Setiap kejadian dinotifikasi sekali, bukan setiap interval. Matikan lewat
kotak **Notifikasi sistem untuk sync otomatis** di halaman Jadwal.

## Sync dari Task Scheduler

Kalau mau sync berjalan walau aplikasi tidak terbuka, jadwalkan perintah
`sipdb` di Windows Task Scheduler. Caranya ada di [CLI](../cli/).

[Kembali ke panduan](../)
