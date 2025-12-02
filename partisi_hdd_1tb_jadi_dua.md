Berikut panduan **paling aman dan lengkap** untuk memformat harddisk 1TB yang awalnya punya **3 partisi** menjadi **2 partisi baru**. Kamu bisa lakukan di **Windows** atau **Disk Management** tanpa aplikasi tambahan.

---

# ✅ **LANGKAH-LANGKAH FORMAT & ATUR ULANG PARTISI**

> ⚠️ **PERINGATAN:** Semua data di harddisk tersebut akan HILANG setelah diformat. Pastikan sudah dibackup.

---

# **✔️ CARA 1: Menggunakan Disk Management (paling mudah)**

### **1. Buka Disk Management**

* Klik **Start**
* Ketik **diskmgmt.msc**
* Enter

### **2. Hapus 3 Partisi Lama**

Di bagian list disk:

* Cari **Disk 1 / Disk 2** (pastikan 1TB)
* Klik kanan setiap partisi → **Delete Volume**

  * Lakukan pada **semua 3 partisi** sampai menjadi **Unallocated Space** semuanya.

### **3. Buat 2 Partisi Baru**

Setelah seluruh disk kosong dan muncul “Unallocated”:

### **Partisi Pertama**

* Klik kanan pada area Unallocated → **New Simple Volume**
* Tentukan ukuran partisi pertama (misal: **500GB** = 500.000 MB)
* Pilih format: **NTFS**
* Pilih drive letter (misal: D)
* Finish

### **Partisi Kedua**

* Ruang Unallocated sisa → klik kanan → **New Simple Volume**
* Gunakan semua ruang tersisa
* Format NTFS juga
* Pilih drive letter (misal: E)
* Finish

---

# **✔️ CARA 2: Format & Partisi Lewat CMD (diskpart)**

Cocok kalau kamu mau cara cepat.

### **1. Buka CMD sebagai Administrator**

Ketikan:

```
diskpart
```

### **2. Tampilkan daftar disk**

```
list disk
```

Catat nomor disk 1TB kamu (misal Disk 1).

### **3. Select disk**

```
select disk 1
```

### **4. Hapus semua isi disk (bersihkan total)**

```
clean
```

### **5. Buat partisi pertama (misal 500GB)**

```
create partition primary size=500000
format fs=ntfs quick
assign letter=D
```

### **6. Buat partisi kedua (sisa semua)**

```
create partition primary
format fs=ntfs quick
assign letter=E
```

### **7. Keluar**

```
exit
```

---

# ✔️ Saran Pembagian Partisi untuk Harddisk 1TB

Beberapa pembagian umum:

### **Opsi A: 500GB + 500GB** (paling seimbang)

### **Opsi B: 300GB + 700GB** (untuk game & data besar)

### **Opsi C: 100GB + 900GB** (partisi kecil khusus backup/system)
