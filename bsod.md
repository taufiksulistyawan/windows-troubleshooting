Berikut penjelasan **penyebab BSOD (Blue Screen of Death) di Windows 10**, khususnya **kasus yang diawali “Automatic Repair” lalu setelah Restart muncul layar :( (BSOD)**, beserta **langkah penanganannya dari yang paling aman sampai terakhir**.

---

## Apa yang Terjadi?

Urutannya biasanya seperti ini:

1. **Windows gagal boot normal**
2. Masuk ke **Automatic Repair**
3. Setelah pilih **Restart**
4. Muncul **layar biru :( (BSOD)**
   ➜ artinya **kerusakan cukup serius** (sistem, driver, atau hardware)

---

## Penyebab Umum BSOD (Paling Sering Terjadi)

### 1️⃣ Kerusakan File Sistem Windows

* Mati listrik mendadak
* Force shutdown
* Bad sector HDD / error SSD

**Ciri-ciri:**

* Loop Automatic Repair
* BSOD setelah restart
* Tidak bisa masuk Windows

---

### 2️⃣ Driver Bermasalah / Tidak Kompatibel

* Driver VGA, LAN, WiFi
* Update driver gagal
* Driver lama di Windows 10 baru

**Kode BSOD yang sering muncul:**

* `DRIVER_IRQL_NOT_LESS_OR_EQUAL`
* `SYSTEM_THREAD_EXCEPTION_NOT_HANDLED`

---

### 3️⃣ Update Windows Gagal

* Update terputus
* Konflik update terbaru

**Ciri:**

* BSOD setelah update
* Sebelumnya muncul “Configuring Windows Update”

---

### 4️⃣ Kerusakan Harddisk / SSD

* Bad sector
* HDD lemah
* SSD error firmware

**Ciri:**

* Lemot saat boot
* Bunyi HDD (klik)
* Sering corrupt

---

### 5️⃣ RAM Bermasalah

* RAM kotor
* Slot longgar
* RAM rusak

**Ciri:**

* BSOD acak
* Error berbeda-beda setiap restart

---

### 6️⃣ Virus / Malware

* Terutama virus file system
* Pernah colok flashdisk / sharing jaringan

---

## LANGKAH PERBAIKAN (Ikuti Berurutan)

### 🟢 LANGKAH 1 – Masuk Advanced Options

Saat BSOD / Automatic Repair:

```
Troubleshoot
→ Advanced options
```

---

### 🟢 LANGKAH 2 – Startup Repair

```
Advanced options
→ Startup Repair
```

✔ Cocok jika masalah file boot
❌ Jika gagal, lanjut

---

### 🟢 LANGKAH 3 – Uninstall Update (Paling Efektif)

```
Advanced options
→ Uninstall Updates
→ Uninstall latest quality update
```

Jika gagal ➜ coba **feature update**

---

### 🟢 LANGKAH 4 – Masuk Safe Mode

```
Advanced options
→ Startup Settings
→ Restart
→ Tekan 4 / F4 (Safe Mode)
```

Jika berhasil masuk Safe Mode:

* Uninstall driver VGA
* Uninstall software terakhir
* Scan virus (Windows Defender)

---

### 🟡 LANGKAH 5 – Perbaiki File Sistem (CMD)

Masuk:

```
Advanced options
→ Command Prompt
```

Ketik satu per satu:

```bat
sfc /scannow
```

Jika gagal:

```bat
chkdsk c: /f /r
```

Jika masih error:

```bat
dism /online /cleanup-image /restorehealth
```

⚠ Jika drive bukan C:, cek dulu:

```bat
diskpart
list volume
```

---

### 🟡 LANGKAH 6 – System Restore (Jika Pernah Aktif)

```
Advanced options
→ System Restore
```

Pilih tanggal sebelum error terjadi

---

## 🔴 LANGKAH TERAKHIR (Jika Semua Gagal)

### Opsi A – Reset Windows (Data Aman)

```
Troubleshoot
→ Reset this PC
→ Keep my files
```

### Opsi B – Install Ulang (Paling Bersih)

* Buat flashdisk installer Windows 10
* Format drive C
* Install ulang

---

## Cek Hardware (WAJIB Jika Sering BSOD)

1. **Cek RAM**

   * Cabut → bersihkan → pasang ulang
   * Coba 1 keping saja

2. **Cek HDD / SSD**

   * Jika HDD lama ➜ sangat sering jadi penyebab
   * SMART error = ganti

---

## Kesimpulan Singkat

| Penyebab     | Solusi Utama          |
| ------------ | --------------------- |
| Update gagal | Uninstall Update      |
| File rusak   | SFC / DISM            |
| Driver error | Safe Mode → uninstall |
| HDD rusak    | CHKDSK / ganti        |
| RAM          | Bersihkan / ganti     |
| Parah        | Reset / Install ulang |

---

Jika kamu bisa:

* **Kirim kode error BSOD** (misalnya `CRITICAL_PROCESS_DIED`)
* Atau **foto layar biru :(**

👉 saya bisa tentukan **penyebab pastinya + langkah paling cepat** tanpa reinstall.
