---
title: Kebijakan privasi
lang: id
---

Berlaku sejak 23 November 2026.

**Sipdb tidak mengirim data ke kami atau ke pihak lain.** Tidak ada akun
Sipdb, telemetry, statistik pemakaian, laporan crash, atau iklan.

## Siapa yang dihubungi Sipdb

Hanya yang kamu atur di profil:

- server database produksimu (hanya dibaca);
- server SSH, kalau kamu memakai SSH;
- database lokal di laptopmu.

Sipdb sendiri tidak memeriksa update; Microsoft Store yang mengurusnya.
Tautan Bantuan dan Privasi dibuka di browsermu.

## Yang disimpan di laptopmu

| Apa | Di mana |
|---|---|
| Profil koneksi (host, port, user, nama database, jadwal) | Folder data aplikasi Sipdb |
| Password dan passphrase kunci SSH | Windows Credential Manager |
| Log sync: nama tabel, jumlah baris, dan pesan error, tanpa password. Pesan error dari database bisa memuat nilai data (misalnya `Duplicate entry '…'`) | Folder data aplikasi Sipdb; file berotasi di 5 MB, paling banyak enam file per log (aplikasi dan CLI masing-masing satu log) |
| Salinan data dan catatan sync (schema `_sipdb`) | Database lokalmu |

Semua tetap di laptopmu. Mencopot Sipdb menghapus profil, pengaturan, dan
log; password di Credential Manager dan database lokalmu tidak ikut dihapus
(lihat [pasang](../pasang/)).

## Support bundle

File support bundle hanya dibuat kalau kamu memintanya, dan hanya terkirim kalau
**kamu sendiri** mengirimkannya. Isinya log, profil tanpa password, status
tabel, dan riwayat run; isi baris data tidak ikut. Periksa dulu sebelum
mengirim, karena pesan error dari database bisa memuat nilai data. Bundle
yang kami terima hanya dipakai untuk membantumu dan dihapus setelah
masalahnya selesai.

## Kontak

Pertanyaan tentang privasi: {{ site.support_email }}.

[Kembali ke panduan](../)
