Berikut **tahapan lengkap, runtut, dan praktis** untuk menganalisa serta memperbaiki **komputer yang mati total atau tidak mau hidup sama sekali**. Ini adalah metode teknisi untuk mencari sumber masalah dari yang paling mudah sampai yang paling kompleks.

---

# ✅ **TAHAP 1 — Periksa Sumber Listrik Paling Dasar**

1. **Pastikan kabel power terpasang benar**

   * Coba cabut dan pasang ulang kabel power PSU.
   * Pastikan stop kontak berfungsi (tes pakai charger HP/lampu).

2. **Matikan lalu hidupkan kembali switch PSU**

   * Switch di PSU (belakang casing) harus di posisi **ON (I)**.

3. **Gunakan kabel power lain**
   Kabel sering putus di dalam tanpa terlihat.

---

# ✅ **TAHAP 2 — Tes PSU (Power Supply Unit)**

Masalah paling sering: **PSU mati atau error**.

### ✔ Cara pengecekan cepat:

1. Lepas semua kabel PSU dari motherboard.
2. Tes metode **jumper paperclip**:

   * Hubungkan pin **hijau + hitam** pada konektor 24-pin.
   * Jika kipas PSU tidak berputar = PSU mati.
   * Jika berputar tapi komputer tetap tidak nyala = PSU lemah.

> **Catatan**: PSU lemah sering membuat **lampu motherboard nyala** tetapi **komputer tidak start**.

---

# ✅ **TAHAP 3 — Periksa Tombol Power**

1. Coba hidupkan dengan **short** pin PW_Switch pada motherboard secara manual (menggunakan obeng).

   * Jika menyala = tombol casing rusak.
   * Jika tidak menyala = lanjut ke cek motherboard/PSU.

---

# ✅ **TAHAP 4 — Periksa Motherboard**

1. **Perhatikan tanda-tanda board rusak**

   * Tidak ada reaksi sama sekali.
   * Ada lampu standby tapi tidak start.
   * Komponen VRM/bagian chipset panas berlebih.
   * Elco (kapasitor) menggembung.

2. **Reset BIOS / Clear CMOS**

   * Cabut baterai CMOS 10–15 menit.
   * Atau pakai jumper CLR_CMOS.

---

# ✅ **TAHAP 5 — Cek RAM (Penyebab layar mati & no display)**

1. Cabut RAM → bersihkan pin dengan penghapus → pasang kembali.
2. Coba hidupkan hanya dengan **1 keping RAM**.
3. Pindahkan ke slot RAM lain.

> Jika komputer hidup tetapi **tidak tampil** → RAM/HDD/GPU bisa penyebabnya.

---

# ✅ **TAHAP 6 — Cek GPU (jika memakai VGA Card)**

1. Lepas GPU, coba hidupkan menggunakan VGA onboard.
2. Pastikan kabel power GPU 6/8 pin terpasang.

---

# ✅ **TAHAP 7 — Cek Prosesor & Pendingin**

1. Pastikan **kipas CPU** berputar.
   Jika tidak, biasanya komputer tidak akan POST.
2. Cek thermal paste kering berlebihan.
3. Coba hidupkan tanpa CPU (untuk lihat respon error):
   Jika tidak ada bunyi/beep → motherboard kemungkinan rusak.

---

# ✅ **TAHAP 8 — Cek Storage (SSD/HDD)**

Storage tidak berpengaruh ke komputer hidup atau tidak, tapi berpengaruh ke **booting layar hitam / no OS**.

Tapi jika SSD **short**, komputer bisa:

* langsung mati
* tidak bisa start
* PSU protek

---

# ✅ **TAHAP 9 — Test dengan Minimal Hardware (Barebone)**

Lepas semua hardware, tes hanya dengan:

✔ Motherboard
✔ PSU
✔ 1 RAM
✔ CPU + HSF

Jika kondisi minimal ini **tidak mau hidup**, maka kerusakan hanya 2 kemungkinan:

### ➤ **PSU rusak**

### ➤ **Motherboard rusak**

---

# ✅ **TAHAP 10 — Analisa Berdasarkan Gejala**

### 🔵 **Gejala 1: Lampu motherboard nyala, tapi tidak mau start**

Penyebab:

* PSU lemah → paling sering
* Motherboard short
* Tombol casing rusak
* RAM tidak terbaca

---

### 🔵 **Gejala 2: Kipas muter sebentar lalu mati**

Penyebab:

* CPU overheat (kipas tidak terpasang sempurna)
* PSU protek
* Motherboard rusak

---

### 🔵 **Gejala 3: Mati total (tidak ada tanda kehidupan)**

Penyebab:

* PSU mati total
* Kabel power tidak masuk
* Motherboard short
* Heatsink tidak terpasang → CPU tidak start

---

### 🔵 **Gejala 4: Hidup tapi tidak tampil (no display)**

Penyebab:

* RAM rusak / kotor → paling sering
* GPU bermasalah
* Motherboard masalah slot
* BIOS korup
* CPU pin rusak
