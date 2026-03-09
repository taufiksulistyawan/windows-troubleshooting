## Urutan troubleshooting paling efektif

Saya sarankan lakukan ini berurutan:

1️⃣ Jalankan

```
DISM /Online /Cleanup-Image /RestoreHealth
```
```
sfc /scannow
```

2️⃣ Install ulang **driver Intel HD**

3️⃣ Cek SSD dengan **CrystalDiskInfo**

4️⃣ Coba **lepas HDD 500GB sementara**

5️⃣ Jika masih BSOD → **install ulang Windows**

---

**membaca file crash Windows (`minidump`)**.

Kalau Anda kirim isi folder:

```
C:\Windows\Minidump
```

biasanya kita bisa tahu **driver atau hardware mana yang menyebabkan BSOD**. 🔧
