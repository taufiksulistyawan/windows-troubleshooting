Tentu. Dari proses troubleshooting yang sudah Anda lakukan, kasusnya ternyata **bukan karena file Defender hilang**, melainkan service **WinDefend** dalam keadaan **Disabled (Start=4)** sehingga Windows Defender tidak bisa aktif.

Berikut ringkasan yang bisa Anda terapkan di komputer lain yang mengalami gejala serupa.

# Memperbaiki Windows Defender Tidak Bisa Aktif

## Gejala

* Windows Defender tidak bisa diaktifkan.
* Muncul pesan perlindungan dimatikan.
* Service Defender tidak berjalan.
* Regedit mungkin pernah dinonaktifkan.
* SFC dan DISM tidak menemukan solusi.

---

## 1. Cek Status Service Defender

Buka Command Prompt sebagai Administrator:

```cmd
sc qc WinDefend
```

Perhatikan bagian:

```text
START_TYPE : 4 DISABLED
```

Jika nilainya **4 (DISABLED)** maka Defender memang dinonaktifkan.

---

## 2. Cek Nilai Registry Service

Jalankan:

```cmd
reg query "HKLM\SYSTEM\CurrentControlSet\Services\WinDefend"
```

Perhatikan nilai:

```text
Start    REG_DWORD    0x4
```

Arti nilai Start:

| Nilai | Keterangan |
| ----- | ---------- |
| 2     | Automatic  |
| 3     | Manual     |
| 4     | Disabled   |

---

## 3. Aktifkan Kembali Service Defender

Jalankan:

```cmd
reg add "HKLM\SYSTEM\CurrentControlSet\Services\WinDefend" /v Start /t REG_DWORD /d 2 /f
```

Jika berhasil akan muncul:

```text
The operation completed successfully.
```

---

## 4. Restart Komputer

Lakukan restart Windows.

---

## 5. Verifikasi Service Berjalan

Setelah boot kembali:

```cmd
sc query WinDefend
```

Hasil normal:

```text
STATE : 4 RUNNING
```

Catatan:

* Pada output `sc query`, angka **4** berarti **RUNNING**, bukan Disabled.
* Pada registry `Start=4`, angka **4** berarti **Disabled**.

Banyak teknisi yang sering tertukar pada bagian ini.

---

## 6. Cek Policy Defender

Pastikan policy tidak mematikan Defender:

```cmd
reg query "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender"
```

Nilai yang aman:

```text
DisableAntiSpyware = 0
DisableAntiVirus = 0
```

atau bahkan key tersebut tidak ada sama sekali.

---

## 7. Verifikasi Windows Security Service

```cmd
sc query SecurityHealthService
```

Hasil normal:

```text
STATE : 4 RUNNING
```

---

## 8. Jika Masih Tidak Aktif

Lakukan:

```cmd
sfc /scannow
```

Kemudian:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

Lalu restart.

---

## Kesimpulan Kasus Anda

Penyebab utama ternyata:

```text
HKLM\SYSTEM\CurrentControlSet\Services\WinDefend
Start = 4
```

yang berarti service Microsoft Defender Antivirus dinonaktifkan. Setelah diubah menjadi:

```text
Start = 2
```

dan komputer direstart, service Defender kembali berjalan normal.

Ini adalah langkah yang cukup berguna untuk teknisi ketika menemukan komputer Windows 10/11 yang Defender-nya tidak bisa aktif akibat perubahan service oleh malware, antivirus pihak ketiga, atau konfigurasi sistem yang tidak tepat.
