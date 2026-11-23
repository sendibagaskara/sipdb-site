---
title: Kalau ada masalah
lang: id
---

## Akun ditolak

"Akun … DITOLAK" berarti akun server bisa menulis, atau haknya tidak bisa
dipastikan. Buat akun khusus baca (lihat [akun read-only](../akun-read-only/)).
Tes koneksi di halaman Koneksi menampilkan hak yang bermasalah.

## Tidak bisa terhubung ke server

- Periksa host, port, dan apakah laptopmu boleh mengakses server (firewall,
  VPN, IP yang diizinkan).
- Kalau koneksi putus di tengah sync, Sipdb mencoba lagi tiga kali (setelah
  5, 15, dan 45 detik) lalu melanjutkan dari tempat terakhir. Data yang
  sudah tersalin aman.

## Kunci host SSH berubah

Sipdb menolak terhubung kalau kunci host server SSH berbeda dengan yang
dulu kamu percayai. Tanyakan ke admin servermu apakah servernya memang
diganti sebelum mempercayai kunci baru.

## "Database lokal … sedang disync oleh proses Sipdb lain"

Aplikasi dan perintah `sipdb` (misalnya dari Task Scheduler) tidak bisa
sync database lokal yang sama bersamaan. Tunggu sampai yang lain selesai.

## Tabel dilewati

- **Tidak punya PK maupun unique key:** Sipdb tidak bisa melacak barisnya.
  Tambahkan primary key di server kalau tabel itu perlu disalin.
- **Tabel lokal memakai engine selain InnoDB:** ubah ke InnoDB.

## Function tidak bisa dibuat (binary log)

MySQL lokal dengan binary log aktif menolak function dari pengguna biasa.
Jalankan sekali di MySQL lokal:

```sql
SET GLOBAL log_bin_trust_function_creators = 1;
```

## Support bundle

Kalau masalahnya tetap ada, buat **support bundle**: halaman **Riwayat** →
**Ekspor support bundle**, atau `sipdb support-bundle` di terminal.

Zip itu berisi log, profil tanpa password, status tabel, dan 20 run
terakhir. Isi baris data tidak ikut. Server tidak dihubungi saat membuatnya.
**Periksa dulu isinya sebelum mengirim:** pesan error dari database bisa
memuat nilai data.

Kirim ke {{ site.support_email }}.

[Kembali ke panduan](../)
