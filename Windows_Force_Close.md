1. 🧩 **Aplikasi Settings (Pengaturan)** langsung menutup sendiri saat dibuka?
2. ⚙️ **Jendela pengaturan tertentu (misalnya Network, System, atau Personalization)** yang menutup tiba-tiba?
3. 💻 Atau **Windows-nya restart / sleep / shutdown sendiri** setelah buka Settings?

Tapi sementara itu, berikut beberapa **langkah umum untuk mengatasi masalah Settings yang menutup sendiri di Windows 11** (kasus paling sering adalah nomor 1).

---

### 🔧 1. Jalankan Troubleshooter dan System Scan

#### a. Jalankan SFC dan DISM

Buka **Command Prompt (Admin)**, lalu ketik perintah berikut satu per satu:

```cmd
sfc /scannow
```

Setelah selesai, lanjutkan:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

➡️ Ini memperbaiki file sistem Windows yang rusak, sering jadi penyebab Settings crash.

---

### 🧰 2. Reset Aplikasi Settings

1. Tekan `Win + I` → jika langsung tertutup, buka **Settings** lewat cara lain:

   * Tekan `Win + R` → ketik:

     ```
     ms-settings:
     ```
   * Jika tetap menutup sendiri, lanjut ke langkah berikut.

2. Buka **Windows PowerShell (Admin)**, lalu jalankan:

   ```powershell
   Get-AppxPackage *windows.immersivecontrolpanel* | Reset-AppxPackage
   ```

   > Ini akan me-reset aplikasi Settings ke kondisi awal.

---

### 🧼 3. Perbaiki dengan Reinstall Aplikasi Sistem

Masih di PowerShell (Admin), jalankan:

```powershell
Get-AppxPackage -AllUsers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

➡️ Ini mendaftarkan ulang semua aplikasi bawaan Windows termasuk **Settings**.

---

### 🧹 4. Buat Akun Windows Baru (tes)

Kadang profil user yang korup bisa bikin Settings crash.
Coba buat akun baru:

```cmd
net user test123 password123 /add
net localgroup administrators test123 /add
```

Login pakai akun baru → buka Settings → lihat apakah masih tertutup sendiri.

---

### 🪟 5. Update Windows

Tekan `Win + R` → ketik:

```
ms-settings:windowsupdate
```

Kalau terbuka, lakukan update penuh.
Kalau tidak bisa, jalankan update lewat PowerShell:

```powershell
Install-Module PSWindowsUpdate
Get-WindowsUpdate
Install-WindowsUpdate
```

---

### ⚠️ 6. Jika Semua Gagal

Langkah terakhir:

* Gunakan **Repair Install Windows 11** (melalui ISO resmi Microsoft, pilih “Keep my files”).
* Atau **buat System Restore Point / Reset PC** dengan opsi “Keep my files”.
