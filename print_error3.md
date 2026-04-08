Nah ini sudah mulai jelas 👍
Kalau **setiap pagi error, tapi normal setelah cabut–pasang kabel LAN**, berarti masalahnya hampir pasti di **jaringan / koneksi printer**, bukan di Microsoft Word.

---

## 🔍 Analisa Penyebab

Dari gejala kamu:

* ❌ Pagi hari → tidak bisa print (Word error printer)
* ✅ Setelah cabut LAN → langsung normal

👉 Ini biasanya karena:

1. **IP printer berubah (DHCP)**
2. **ARP / cache jaringan nyangkut**
3. **Switch / port LAN sleep / delay**
4. **PC tidak bisa resolve printer saat awal nyala**

---

## ✅ Solusi Paling Direkomendasikan (WAJIB)

### 🔧 1. Set IP Printer Jadi Static

Ini solusi paling penting.

Masuk ke:

* Setting printer (via panel / web printer)
* Ubah dari **DHCP → Static IP**

Contoh:

```
IP: 192.168.1.100
Gateway: 192.168.1.1
Subnet: 255.255.255.0
```

👉 Tujuannya:
Supaya PC tidak kehilangan koneksi saat IP berubah tiap pagi

---

## 🔧 2. Tambahkan Printer via IP (bukan via sharing)

Kalau sekarang pakai:

```
\\PC-SERVER\Printer
```

👉 Lebih stabil pakai:

* **Add printer → TCP/IP**
* Masukkan IP printer langsung

---

## 🔧 3. Disable Power Saving LAN (PC)

Kadang LAN mati saat idle malam.

1. Device Manager
2. Network Adapter
3. Properties → Power Management
4. Hilangkan centang:

   ```
   Allow the computer to turn off this device
   ```

---

## 🔧 4. Cek DHCP Router

Kalau tetap mau DHCP:

* Set **DHCP Reservation (binding IP ke MAC printer)**

---

## 🔧 5. Restart Otomatis Print Spooler (opsional)

Bisa bantu kalau jaringan delay:

```
net stop spooler
net start spooler
```

---

## 🔧 6. Cek Switch / Kabel LAN

Kemungkinan juga:

* Port switch delay aktif
* Kabel LAN longgar
* Switch “green ethernet” (hemat daya)

👉 Coba pindah port switch

---

## 💡 Kesimpulan

Masalah kamu bukan di Word, tapi:
👉 **koneksi printer hilang saat idle (malam)**
👉 dan “refresh” saat kabel dicabut

---

Kalau mau lebih dalam, kasih info:

* Printer merk & tipe
* Pakai sharing dari PC atau langsung ke jaringan?
* IP sekarang statik atau DHCP?

Nanti saya bantu buatkan setting paling stabil untuk kantor kamu 👍
