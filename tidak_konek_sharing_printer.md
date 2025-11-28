Berikut langkah **paling ampuh dan lengkap** untuk mengatasi **tidak bisa konek sharing printer** di Windows (Windows 10/11). Ikuti dari atas ke bawah sampai berhasil.

---

# ✅ **1. Pastikan Komputer Pemilik Printer Sudah Aktif & Tersharing**

### A. Cek apakah printer sudah di-share

1. Buka **Control Panel → Devices and Printers**
2. Klik kanan printer → **Printer properties**
3. Tab **Sharing** → centang:

   * ✔ *Share this printer*
   * ✔ *Render print jobs on client computers*

---

# ✅ **2. Pastikan Kedua Komputer Dalam Satu Jaringan**

* Pastikan IP sama segmen, contoh:

  * Komputer A: **192.168.1.10**
  * Komputer B: **192.168.1.20**
* Cek dengan ping:

  ```
  ping 192.168.1.xxx
  ```

Jika *Request time out*, berarti jaringan bermasalah.

---

# ✅ **3. Nyalakan Fitur File & Printer Sharing**

Di komputer server & client lakukan:

**A. Control Panel → Network and Sharing Center → Advanced sharing settings**

* Turn on network discovery
* Turn on file and printer sharing
* Turn on sharing so anyone with network access…

**B. Matikan password protected sharing (agar mudah)**

* Pilih: **Turn off password protected sharing**

---

# ✅ **4. Cek Service Penting**

Tekan **Windows + R** → ketik:

```
services.msc
```

Pastikan statusnya **Running**:

* **Function Discovery Provider Host**
* **Function Discovery Resource Publication**
* **Print Spooler**
* **SSDP Discovery**
* **UPnP Device Host**

Kalau Stop → klik **Start**.

---

# ✅ **5. Coba Akses Printer Lewat IP (Cara Paling Work)**

### Di komputer klien:

Tekan **Windows + R** → ketik:

```
\\192.168.1.xx
```

Ganti dengan IP komputer yang terhubung printer.

Jika muncul folder + printer → klik kanan printer → **Connect**.

---

# ✅ **6. Tambah Printer Manual (Jika Tidak Terdeteksi)**

1. Settings → Bluetooth & devices → **Printers & scanners**
2. Klik **Add device**
3. Pilih: **The printer that I want isn’t listed**
4. Pilih:
   ✔ *Select a shared printer by name*

Masukkan format:

```
\\NAMA-KOMPUTER\NAMA-PRINTER
```

contoh:

```
\\PC-KASIR\EPSON-L3110
```

---

# ✅ **7. Matikan Firewall Sementara**

Untuk test:

Search: **Windows Defender Firewall** → **Turn Windows Defender Firewall on or off**

→ Turn off untuk **Private Network** dulu.
(Jika berhasil, nanti kita buat pengecualian firewall.)

---

# ✅ **8. Reset Networking** (Jika tetap gagal)

Buka CMD Run as Administrator:

```
netsh winsock reset
netsh int ip reset
ipconfig /flushdns
ipconfig /renew
```

Restart komputer.

---

# Jika Masih Error ❗

Kirimkan informasi berikut agar saya diagnosa:

1. Error yang muncul saat connect printer
2. IP komputer server & client
3. Hasil ping antara kedua komputer
4. Tipe printer yang dishare

Kirim screenshot juga boleh biar langsung saya analisa.
