# Cara Remote Desktop Tanpa Password (RDP)

> ⚠️ **Peringatan Keamanan**
> Metode ini **menurunkan tingkat keamanan Windows**. Gunakan **hanya untuk kebutuhan lab, testing, atau jaringan internal yang aman**. Tidak disarankan untuk server/public-facing machine.

---

## Tujuan

Mengizinkan koneksi **Remote Desktop (RDP)** ke Windows **tanpa harus memasukkan password**, khususnya untuk akun lokal.

---

## Prasyarat

* Windows Pro / Education / Enterprise (karena membutuhkan **Group Policy Editor**)
* Akses **Administrator**

---

## Langkah-Langkah

### 1. Aktifkan Remote Desktop (RDP)

1. Tekan `Win + R`, ketik `sysdm.cpl`, lalu tekan **Enter**
2. Masuk ke tab **Remote**
3. Centang **Allow remote connections to this computer**
4. Klik **Apply** lalu **OK**

---

### 2. Buka Group Policy Editor

1. Tekan `Win + R`
2. Ketik `gpedit.msc`
3. Tekan **Enter**

---

### 3. Nonaktifkan Limit Login Akun Lokal Tanpa Password

Masuk ke path berikut:

```
Computer Configuration
 └─ Windows Settings
    └─ Security Settings
       └─ Local Policies
          └─ Security Options
```

Cari dan ubah setting berikut:

* **Accounts: Limit local account use of blank passwords to console logon only**

  * Set menjadi: **Disabled**

📌 *Fungsi:* Mengizinkan akun lokal tanpa password login melalui RDP.

---

### 4. Nonaktifkan Credential Delegation Restriction

Masuk ke path berikut:

```
Computer Configuration
 └─ Administrative Templates
    └─ System
       └─ Credential Delegation
```

Cari dan ubah setting berikut:

* **Restrict delegation of credentials to remote servers**

  * Set menjadi: **Disabled**

📌 *Fungsi:* Mengizinkan pengiriman credential kosong (blank password) saat RDP.

---

### 5. Update Group Policy

Setelah semua setting diubah, jalankan perintah berikut di **Command Prompt (Run as Administrator)**:

```cmd
gpupdate /force
```

Atau restart komputer agar kebijakan diterapkan sempurna.

---

## Catatan Tambahan

* Akun **tidak boleh menggunakan Microsoft Account**, harus **Local Account**
* Username **tidak boleh kosong**
* Jika tetap gagal, pastikan:

  * Firewall mengizinkan **Remote Desktop (TCP 3389)**
  * Service **Remote Desktop Services** berjalan

---

## Rekomendasi Keamanan

Jika RDP harus tanpa password:

* Batasi akses via **Firewall (IP tertentu saja)**
* Gunakan **VPN**
* Nonaktifkan kembali setting ini setelah selesai testing

---

## Referensi

* `gpedit.msc`
* Windows Local Security Policy
* Remote Desktop Services (RDP)

---

✍️ *Catatan ini cocok untuk dokumentasi GitHub / internal IT knowledge base*
