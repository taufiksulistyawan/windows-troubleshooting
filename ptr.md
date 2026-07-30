Kalau **service Workstation tidak ada**, itu **tidak normal**. Hampir semua Windows (7/8/10/11) memiliki service **Workstation (LanmanWorkstation)**. Service ini bertanggung jawab agar Windows bisa mengakses folder sharing (SMB). Jika tidak ada, wajar muncul error seperti:

> **The network is not present or not started.**

Mari kita pastikan dulu.

### Langkah 1. Cek melalui Command Prompt (Run as Administrator)

Jalankan:

```cmd
sc query lanmanworkstation
```

Beritahu saya hasilnya.

Kemudian jalankan juga:

```cmd
sc qc lanmanworkstation
```

---

### Langkah 2. Cek versi Windows

Jalankan:

```cmd
winver
```

atau

```cmd
systeminfo | findstr /B /C:"OS Name"
```

---

### Langkah 3. Cek apakah fitur SMB Client terpasang

Buka PowerShell (Run as Administrator):

```powershell
Get-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
```

dan

```powershell
Get-SmbClientConfiguration
```

Jika perintah kedua menghasilkan error, itu juga merupakan petunjuk penting.

---

### Langkah 4. Cek registry service

Buka Command Prompt:

```cmd
reg query "HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation"
```

Kalau muncul:

```
ERROR: The system was unable to find the specified registry key
```

berarti service **Workstation benar-benar hilang**, kemungkinan karena:

* terkena virus atau malware,
* dihapus oleh software optimasi,
* registry Windows rusak,
* atau komponen Windows mengalami kerusakan.

---

## Saya juga ingin memastikan satu hal

Karena Anda sebelumnya pernah menangani komputer yang **Windows Defender dan Regedit dinonaktifkan oleh virus**, saya ingin memastikan apakah ini **komputer yang sama** atau komputer yang berbeda?

Tolong kirimkan hasil dari 4 perintah di atas, terutama:

```cmd
sc query lanmanworkstation
```

Dari hasil itu saya bisa menentukan apakah cukup mengaktifkan servicenya, memperbaiki komponen Windows, atau memang perlu melakukan repair system.
