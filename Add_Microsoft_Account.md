Ada beberapa cara supaya Windows tidak selalu meminta untuk **menambahkan akun Microsoft** saat login atau setup. Pilih sesuai kebutuhanmu:

---

### 1. **Gunakan akun lokal saat setup awal**

* Saat instalasi Windows, biasanya tidak ada pilihan akun lokal kalau PC terhubung ke internet.
* Triknya:

  1. Putuskan koneksi internet (cabut kabel LAN atau matikan Wi-Fi).
  2. Saat diminta login Microsoft, akan muncul opsi **“Offline account”** atau **“Limited experience”** → pilih itu.
  3. Buat username & password lokal.

---

### 2. **Ubah dari akun Microsoft ke akun lokal**

Kalau sudah terlanjur login dengan akun Microsoft:

1. Buka **Settings** → **Accounts** → **Your info**.
2. Klik **Sign in with a local account instead**.
3. Ikuti langkah untuk buat akun lokal (username & password).
4. Setelah itu, Windows tidak akan minta login Microsoft lagi.

---

### 3. **Nonaktifkan prompt sinkronisasi Microsoft account**

* Buka **Settings** → **Accounts** → **Email & accounts**.
* Hapus akun Microsoft dari bagian **Accounts used by other apps**.

---

### 4. **Gunakan Registry Editor (opsional, untuk advance user)**

Kalau Windows masih suka menampilkan notifikasi "Add a Microsoft account":

1. Tekan `Win + R`, ketik `regedit`.
2. Arahkan ke:

   ```
   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\Accounts
   ```
3. Cari `EnableMicrosoftAccount` → ubah nilai jadi `0`.
   (Kalau tidak ada, buat DWORD baru dengan nama itu).

---

### 5. **Gunakan Local Group Policy (Windows Pro/Enterprise)**

1. Tekan `Win + R`, ketik `gpedit.msc`.
2. Masuk ke:

   ```
   Computer Configuration → Windows Settings → Security Settings → Local Policies → Security Options
   ```
3. Cari **Accounts: Block Microsoft accounts**.
4. Atur ke **Users can’t add Microsoft accounts**.

---

👉 Pertanyaannya: kamu mau **hapus total integrasi akun Microsoft** (supaya hanya akun lokal yang bisa dipakai), atau cukup supaya **tidak dipaksa login/sync Microsoft Account saat setup dan penggunaan**?

Saya lihat di layar laptopmu sekarang Windows sedang **memaksa login akun Microsoft** (fase setup).
Kalau kamu **tidak mau pakai akun Microsoft** dan hanya ingin akun lokal, ada beberapa trik yang bisa langsung dipakai:

---

### 🔹 Cara Bypass Login Microsoft Account

1. **Putuskan internet dulu**

   * Cabut kabel LAN / matikan Wi-Fi (kalau laptop tanpa tombol Wi-Fi, tekan `Shift + F10` untuk buka Command Prompt → ketik `taskmgr` → matikan proses `Network Connection Flow` atau langsung ketik `oobe\bypassnro`).
   * Setelah itu Windows akan restart setup → muncul opsi untuk **“Offline account”** atau **“Limited experience”**.

2. **Gunakan email palsu**

   * Masukkan email acak (contoh: `no@thankyou.com`) + password sembarang.
   * Windows akan gagal verifikasi → biasanya otomatis menampilkan opsi **akun lokal**.

3. **Shortcut langsung**

   * Tekan `Shift + F10` → buka Command Prompt.
   * Ketik perintah berikut lalu tekan Enter:

     ```
     oobe\bypassnro
     ```
   * Laptop akan restart → saat masuk ke setup lagi, kamu akan menemukan opsi **buat akun lokal** tanpa Microsoft account.

---

### 🔹 Setelah Setup

Kalau sudah masuk desktop dan Windows masih nagih akun Microsoft:

* Masuk ke **Settings → Accounts → Your Info → Sign in with a local account instead**.

---

👉 Mau saya bikinkan step-by-step khusus untuk **cara ketik `oobe\bypassnro` di CMD (Shift+F10)** biar kamu langsung bisa bikin akun lokal?
