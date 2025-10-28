## 🧰 Langkah-langkah Format & Gabung Partisi di CMD

1. **Buka CMD sebagai Administrator**

   * Tekan `Windows + S`, ketik `cmd`
   * Klik kanan “Command Prompt” → **Run as administrator**

2. **Masuk ke DiskPart**

   ```cmd
   diskpart
   ```

3. **Lihat daftar disk yang terdeteksi**

   ```cmd
   list disk
   ```

   * Akan muncul daftar seperti:

     ```
     Disk 0    465 GB
     Disk 1    931 GB
     ```
   * **Pastikan tahu mana harddisk bekas laptop kamu.**
     Misalnya ukuran 500GB, berarti `Disk 1`.

4. **Pilih disk yang ingin diformat**

   ```cmd
   select disk 1
   ```

   *(ganti “1” dengan nomor disk kamu)*

5. **Lihat partisi di dalamnya (opsional)**

   ```cmd
   list partition
   ```

   Ini hanya untuk memastikan isi disk yang akan kamu hapus.

6. **Hapus semua partisi di disk tersebut**

   ```cmd
   clean
   ```

   → Perintah ini akan **menghapus semua partisi dan data** di disk itu.

7. **Buat satu partisi baru yang menyatukan seluruh kapasitas**

   ```cmd
   create partition primary
   ```

8. **Format partisi dengan sistem file NTFS**

   ```cmd
   format fs=ntfs quick
   ```

9. **Beri huruf drive (misal D:)**

   ```cmd
   assign letter=D
   ```

10. **Selesai**

* Sekarang harddisk kamu sudah kosong, bersih, dan hanya memiliki satu partisi penuh.
* Keluar dari diskpart:

  ```cmd
  exit
  ```
