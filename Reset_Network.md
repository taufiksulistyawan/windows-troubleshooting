Kalau di **Windows**, biasanya dilakukan untuk mengatasi masalah koneksi internet yang error, WiFi tidak bisa connect, atau IP bentrok.
Berikut langkah-langkahnya:

---

### 1. Buka CMD sebagai Administrator

* Tekan tombol **Windows + R**, ketik `cmd`, lalu tekan **Ctrl + Shift + Enter** supaya terbuka dengan hak admin.

---

### 2. Reset TCP/IP stack

```cmd
netsh int ip reset
```

---

### 3. Reset Winsock (soket jaringan)

```cmd
netsh winsock reset
```

---

### 4. Release dan Renew IP

```cmd
ipconfig /release
ipconfig /renew
```

---

### 5. Flush DNS Cache

```cmd
ipconfig /flushdns
```

---

### 6. Restart Komputer

Supaya semua perubahan diterapkan, lakukan restart.

---

⚠️ Catatan: Setelah reset, kadang pengaturan manual (misalnya IP statis) akan hilang dan balik ke **DHCP (otomatis)**. Kalau sebelumnya pakai IP manual, harus diset ulang.
