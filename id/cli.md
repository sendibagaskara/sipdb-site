---
title: Memakai Sipdb dari terminal
lang: id
---

Sipdb dari Microsoft Store juga memasang perintah **`sipdb`**. Buka
PowerShell atau Command Prompt baru, lalu:

```
sipdb version
```

Profil, password, dan riwayatnya sama dengan aplikasi: profil yang dibuat di
aplikasi bisa langsung dipakai di terminal, dan sebaliknya.

## Perintah utama

| Perintah | Fungsi |
|---|---|
| `sipdb init` | Buat profil koneksi (ditanya satu per satu) |
| `sipdb check --profile prod` | Tes koneksi, cek hak akun, tampilkan strategi per tabel |
| `sipdb pull --profile prod` | Sync pertama, lalu sync cepat |
| `sipdb verify --profile prod --max-time 30m` | Pemeriksaan penuh, berhenti rapi setelah 30 menit |
| `sipdb status --profile prod` | Status setiap tabel, tanpa menghubungi server |
| `sipdb log --profile prod` | Riwayat sync, tanpa menghubungi server |
| `sipdb support-bundle` | Buat zip untuk melaporkan masalah (lihat [kalau ada masalah](../masalah/)) |

`sipdb <perintah> --help` menampilkan semua pilihan.

## Kode keluar

| Kode | Arti |
|---|---|
| 0 | Selesai, semua tabel ok |
| 1 | Ada tabel yang gagal, run dihentikan, atau run tidak bisa jalan |
| 2 | Akun server ditolak karena punya hak tulis |
| 3 | Database lokal sedang disync proses Sipdb lain; tidak ada yang dikirim ke server |

## Task Scheduler

1. Buka **Task Scheduler** → **Create Basic Task**.
2. Pilih jadwal, misalnya setiap hari, ulangi setiap 30 menit.
3. Action **Start a program**:
   - Program: `%LOCALAPPDATA%\Microsoft\WindowsApps\sipdb.exe`
   - Arguments: `pull --profile prod`
4. Untuk pemeriksaan penuh malam hari, buat task kedua dengan arguments
   `verify --profile prod --max-time 3h`.

Kolom **Last Run Result** di Task Scheduler menunjukkan kode keluar di
atas (`0x0` = berhasil). Kalau aplikasi sedang sync database lokal yang
sama, task itu keluar dengan kode 3 dan mencoba lagi di jadwal berikutnya.

## Bahasa

`sipdb` mengikuti bahasa yang dipilih di aplikasi. Untuk memaksanya, set
variabel `SIPDB_LANG` ke `id` atau `en`.

[Kembali ke panduan](../)
