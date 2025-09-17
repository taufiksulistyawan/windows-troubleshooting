```markdown
# Mengatasi Network Credentials pada Folder Sharing di Windows

Ketika melakukan **folder sharing** di Windows, terkadang muncul kendala berupa permintaan **Network Credentials** yang menyulitkan akses antar komputer.  
Salah satu cara mengatasinya adalah dengan mengubah pengaturan di **Registry Editor** agar mengizinkan *guest access*.

## Langkah-langkah

1. Tekan tombol **Windows + R** pada keyboard.  
2. Ketikkan `regedit`, lalu tekan **Enter** untuk membuka **Registry Editor**.  
3. Arahkan ke lokasi berikut:  

```

HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters

```

4. Klik kanan pada area kosong di panel kanan → pilih **New** → **DWORD (32-bit) Value**.  
5. Masukkan nama berikut:  

```

AllowInsecureGuestAuth

```

6. Klik dua kali pada nilai yang baru dibuat, lalu isi **Value data** dengan `1` dan pastikan **Base** adalah `Hexadecimal`.  
7. Klik **OK** lalu tutup Registry Editor.  
8. Restart komputer agar perubahan diterapkan.

## Catatan
- Metode ini akan mengizinkan akses *insecure guest*, sehingga pastikan hanya digunakan pada jaringan yang aman.  
- Sebaiknya hanya diterapkan pada **jaringan lokal terpercaya** (LAN/WiFi internal).
