Kalau **file hilang sendiri saat komputer tidak dipakai**, biasanya penyebabnya:

* corrupt di drive C
* Windows Update mereset folder user
* index rusak
* aplikasi sinkronisasi (OneDrive) memindahkan file
* antivirus mengkarantina

👉 **Kasus seperti ini sangat cocok memakai Windows File Recovery mode EXTENSIVE**, karena file kemungkinan sudah tidak tercatat di index NTFS.

Di bawah ini saya berikan **perintah yang paling tepat** untuk recovery folder kamu.

---

# ✅ **LANGKAH RECOVERY PALING EFEKTIF**

## **1. Buat folder hasil recovery di drive lain (wajib!):**

Misal:

📁 **D:\HASIL-RECOVERY**

---

## **2. Buka Command Prompt sebagai Administrator**

Start → ketik **cmd** → **Run as Administrator**

---

## **3. Jalankan Windows File Recovery dengan mode EXTENSIVE**

### 🔥 **Recovery semua file dari folder 2025 milik kamu**

Copy-paste perintah berikut:

```
winfr C: D:\HASIL-RECOVERY /extensive /n \Users\LENOVO\Documents\PEMASARAN MITA\2025\
```

---

## **4. Kalau mau, sekalian recovery semua file dokumen seperti docx, pdf, excel:**

```
winfr C: D:\HASIL-RECOVERY /extensive /n \Users\LENOVO\Documents\PEMASARAN MITA\2025\*.docx /n \Users\LENOVO\Documents\PEMASARAN MITA\2025\*.xlsx /n \Users\LENOVO\Documents\PEMASARAN MITA\2025\*.pdf
```

---

# 📌 **Setelah proses selesai**

Cek hasilnya di:

📁 **D:\HASIL-RECOVERY\Recovery_XXXXXXXX**

Nama file biasanya berubah, tapi isi tetap.

---

# 📣 **Pertanyaan penting (supaya saya bisa kasih perintah lanjutan kalau belum ketemu):**

1. Kamu pakai **OneDrive aktif** tidak? (kadang file pindah otomatis)
2. Folder **PEMASARAN MITA** hilang seluruhnya atau hanya di dalamnya?
3. Drive C kamu SSD atau HDD?

Kalau kamu jawab itu, saya bisa bantu langkah lanjutan yang lebih kuat (termasuk cek Shadow Copy & OneDrive restore).
