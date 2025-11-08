Nah, ini **penting banget** dan jadi petunjuk kuat 👇

Kalau **HDD untuk storage masih terdeteksi**, tapi **SSD (yang sistem) tidak**, berarti:
➡️ **port SATA motherboard dan power supply masih normal**,
➡️ tapi **ada masalah spesifik di komunikasi antara motherboard dan SSD itu.**

---

Berarti kemungkinan mengerucut ke 3 hal berikut:

---

## ⚙️ **1. Mode SATA di BIOS tidak cocok**

Ini **penyebab paling sering** setelah ganti baterai CMOS.
Karena setelah reset CMOS, mode SATA kembali ke default (misalnya **IDE** atau **RAID**), sedangkan Windows dan SSD kamu diset dengan mode **AHCI**.

### 🔧 Solusi:

1. Masuk BIOS (`DEL` atau `F2`).
2. Cari menu **Advanced > SATA Configuration** (atau “Integrated Peripherals”).
3. Pastikan:

   * **SATA Mode = AHCI**
   * Semua port SATA **Enabled**
4. Simpan (`F10`) dan reboot.

🧠 Kalau mode-nya salah, SSD tidak akan terdeteksi sama sekali, tapi HDD bisa (tergantung driver di BIOS).

---

## ⚡ **2. Perbedaan jalur port SATA**

Beberapa motherboard (terutama yang modern seperti MSI PRO H610M-S) memiliki port SATA yang:

* **Nonaktif otomatis jika NVMe slot digunakan**, atau
* **Berbagi jalur dengan port tertentu.**

Misalnya:

> SATA1 & M.2_1 tidak bisa digunakan bersamaan.
> Jadi kalau kamu pakai M.2 NVMe, port SATA1 bisa nonaktif — dan kebetulan SSD kamu terpasang di situ.

### 🔧 Solusi:

* Coba **pindahkan SSD ke port SATA lain** (misalnya dari SATA1 ke SATA3).
* Cek manual motherboard bagian “SATA Port Shared Bandwidth”.

---

## 🔌 **3. Power dari PSU ke SSD lemah / konektor SATA longgar**

Kadang konektor power dari PSU ke SSD **kurang rapat atau rusak di salah satu pin**.
Akibatnya SSD dapat listrik cukup untuk nyala di USB (yang stabil 5V), tapi **tidak stabil dari PSU**.

### 🔧 Solusi:

* Ganti kabel power SATA ke SSD dengan **kabel dari jalur lain PSU**.
* Pastikan konektor masuk rapat.

---

### 🧩 **Tambahan diagnosa cepat**

Kalau kamu bisa:

1. Pasang SSD dan HDD bersamaan.
2. Masuk BIOS → lihat apakah hanya HDD yang muncul.
3. Coba pindahkan SSD ke port SATA yang sama dengan HDD (setelah HDD dicabut).

   * Kalau SSD tetap tidak terdeteksi, tapi HDD bisa → berarti **motherboard tidak cocok dengan SSD-nya (kompatibilitas chipset)** atau mode SATA salah.

---

Kalau kamu kasih tahu:

* 🧠 **Tipe motherboard** (misalnya MSI PRO H610M-S, ASUS H410M, dll)
* 🔋 **SSD-nya** (V-GEN 256GB SATA, sudah terlihat dari gambar)
  Saya bisa kasih **pengaturan BIOS spesifik + port SATA mana yang aktif untuk SSD**.

Kamu mau kirim tipe motherboard-nya biar saya bantu arahkan di menu BIOS-nya?
