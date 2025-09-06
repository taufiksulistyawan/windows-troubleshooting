# 🖨️ Mengatasi Tidak Bisa Konek Sharing Printer di Windows

Jika komputer klien tidak bisa konek ke printer sharing, ikuti langkah-langkah berikut dari sisi **server**.

---

## 🔧 Langkah-langkah Manual

1. **Buka Registry Editor**
   - Tekan `Windows + R`
   - Ketik `regedit` lalu tekan `Enter`

2. **Nonaktifkan RpcAuthnLevelPrivacyEnabled**
   - Pergi ke folder:
     ```
     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print
     ```
   - Klik kanan > **New > DWORD (32-bit) Value**
   - Ubah nama menjadi:
     ```
     RpcAuthnLevelPrivacyEnabled
     ```
   - Klik dua kali > ubah **Value data** = `0`  
     **Base** = `Hexadecimal`

3. **Buat CopyFilesPolicy**
   - Pergi ke folder:
     ```
     HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT
     ```
   - Klik kanan > **New > Key** > rename menjadi:
     ```
     Print
     ```
   - Di dalam key `Print` klik kanan > **New > DWORD (32-bit) Value**  
   - Ubah nama menjadi:
     ```
     CopyFilesPolicy
     ```
   - Klik dua kali > ubah **Value data** = `1`  
     **Base** = `Hexadecimal`

4. **Restart komputer server**

---

## ⚡ Cara Cepat

Jika tidak ingin melakukan langkah manual, cukup download file berikut ini:

👉 [Printer Fix Registry](https://drive.google.com/file/d/1wSzhT8iicThNqdz6CENBemkFAv-At1zI/view?usp=drive_link)

Setelah selesai diunduh, jalankan file tersebut, lalu **restart komputer**.

---

## ✅ Selesai

Sekarang printer sharing seharusnya sudah bisa diakses oleh komputer lain di jaringan.
