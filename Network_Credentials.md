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

Oke, berarti kasusnya **bukan cuma soal password**, tapi kombinasi **policy + setting sharing Windows**. Kita bedah pelan-pelan ya 👍
Biasanya ini kejadian di **Windows 10/11 terbaru** karena guest access makin diketatkan.

---

## LANGKAH WAJIB (cek satu-satu, jangan lompat)

### 1️⃣ Pastikan Password Protected Sharing = OFF

Di **PC yang foldernya dishare**

1. Control Panel
2. Network and Sharing Center
3. Change advanced sharing settings
4. **All Networks**
5. Set:

   * ✅ Turn on sharing so anyone with network access can read/write
   * ❌ Turn off password protected sharing
6. Save changes

> Kalau ini masih ON → Windows **pasti minta credential**, walau registry sudah diubah.

---

### 2️⃣ Aktifkan Guest lewat Local Security Policy

(Ini sering jadi biang masalah)

1. Tekan **Win + R** → ketik:

```
secpol.msc
```

2. Masuk ke:

```
Local Policies → Security Options
```

3. Cari dan set:

| Policy                                                              | Value        |
| ------------------------------------------------------------------- | ------------ |
| Network access: Let Everyone permissions apply to anonymous users   | **Enabled**  |
| Network access: Shares that can be accessed anonymously             | **Enabled**  |
| Network access: Restrict anonymous access to Named Pipes and Shares | **Disabled** |

4. Restart PC

---

### 3️⃣ Paksa Guest Login via CMD (WAJIB)

Buka **CMD as Administrator**, jalankan:

```cmd
net user guest /active:yes
```

Lalu:

```cmd
net localgroup users guest /add
```

---

### 4️⃣ Izinkan SMB Guest Auth (Tambahan penting)

CMD (Admin):

```cmd
reg add "HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f
```

Lalu **restart**.

---

### 5️⃣ Cek SMB Version (INI SERING KELEWAT)

Kalau target sharing **Linux / NAS lama / Samba**, aktifkan SMB1:

1. Win + R → `optionalfeatures`
2. Centang:

   * ☑ SMB 1.0/CIFS File Sharing Support
3. OK → Restart

> ⚠️ Kalau sharing antar Windows modern → SMB1 **tidak wajib**

---

### 6️⃣ Permission Folder (PALING SERING SALAH)

Klik kanan folder → **Properties → Sharing → Advanced Sharing**

* Share this folder ✅
* Permissions:

  * **Everyone**

    * Read ✔
    * Change ✔
    * Full Control ✔ (untuk test)

Lalu ke tab **Security**:

* Tambahkan **Everyone**
* Allow Full Control (sementara untuk test)

> Kalau Sharing ✔ tapi Security ❌ → tetap **nggak bisa akses**

---

## TEST AKSES (jangan via klik dulu)

Dari PC client:

```cmd
\\IP_ADDRESS
```

Contoh:

```cmd
\\192.168.1.10
```

❌ Jangan pakai hostname dulu
✔ Pakai **IP address**

---

## KALAU MASIH MINTA USERNAME

Coba login manual pakai guest:

```cmd
net use \\192.168.1.10\sharename "" /user:guest
```

Kalau **berhasil**, berarti Windows client **masih paksa credential caching**.

Untuk reset credential cache:

```cmd
net use * /delete
```

---
