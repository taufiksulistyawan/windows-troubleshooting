> **“A policy is in effect on your computer which prevents you from connecting to this print queue.”**

menunjukkan bahwa **kebijakan keamanan Windows terhadap shared printer/Point and Print sedang memblokir instalasi driver printer dari komputer lain**.

### 🔎 Analisa kondisi

Alurnya terlihat seperti ini:

```text
PC Client
   │
   │ akses \\DESKTOP-BLFBREV
   ▼
Shared Printer
Canon MF3010 sari
   │
   │ printer ditemukan ✓
   ▼
Windows mencoba install driver
   │
   ✕
Policy Windows memblokir
   │
   ▼
"Connect to Printer"
```

Jadi **sharing printer sebenarnya sudah berjalan**. Yang bermasalah adalah **permission/policy instalasi driver**.

Ini sering terjadi pada Windows 10/11 setelah update keamanan Print Spooler/PrintNightmare.

---

# Solusi 1 — Cara paling cepat

Di komputer **client yang mengalami error**, tekan:

**Win + R**

ketik:

```text
gpedit.msc
```

Kemudian masuk:

```text
Computer Configuration
└── Administrative Templates
    └── Printers
```

Cari:

**Point and Print Restrictions**

Buka → pilih:

**Disabled**

Klik:

**Apply → OK**

Kemudian cari juga:

**Package Point and Print - Approved servers**

Jika policy tersebut aktif, sementara bisa dibuat:

**Disabled**

---

### Kemudian restart Print Spooler

Buka **CMD sebagai Administrator**:

```cmd
net stop spooler
net start spooler
```

Atau langsung:

```cmd
gpupdate /force
```

Kemudian restart komputer.

Setelah itu coba lagi:

```text
\\DESKTOP-BLFBREV
```

lalu klik:

**Canon MF3010 sari → Connect**

---

# Solusi 2 — Jika Windows Home / gpedit.msc tidak ada

Kalau ketika menjalankan:

```text
gpedit.msc
```

muncul:

> Windows cannot find 'gpedit.msc'

gunakan Registry.

Tekan:

**Win + R → regedit**

Masuk ke:

```text
HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\Printers\PointAndPrint
```

Cari DWORD:

```text
RestrictDriverInstallationToAdministrators
```

Jika ada, ubah:

```text
Value = 0
```

Jika belum ada, buat:

**DWORD (32-bit) Value**

dengan nama:

```text
RestrictDriverInstallationToAdministrators
```

dan nilai:

```text
0
```

Setelah itu restart spooler:

```cmd
net stop spooler
net start spooler
```

Kemudian coba konek kembali ke printer.

---

# ⚠️ Tetapi saya lebih menyarankan cara yang lebih aman

Jangan langsung mematikan seluruh keamanan Point and Print jika komputer berada di jaringan perusahaan.

Karena kebijakan tersebut memang dibuat untuk mencegah **driver printer berbahaya dipasang dari print server yang tidak dipercaya**.

Kalau ini jaringan kantor dan Anda mengontrol semua PC, konfigurasi yang lebih baik adalah:

```text
Print Server
    │
    ├── Canon MF3010 driver
    │
    └── Shared Printer
             │
             ▼
        Client Windows
             │
             └── Driver terpercaya
```

Bahkan untuk **Canon MF3010**, saya lebih merekomendasikan **install driver Canon terlebih dahulu di komputer client**, kemudian baru koneksikan ke shared printer.

---

# Solusi 3 — Install driver printer di Client terlebih dahulu

Ini sering menjadi solusi yang paling stabil.

Di PC client:

1. Hapus koneksi printer yang gagal.
2. Install **driver Canon MF3010** sesuai versi Windows.
3. Restart Print Spooler.
4. Setelah driver terpasang, buka:

```text
Control Panel
→ Devices and Printers
→ Add a printer
```

5. Pilih:

**The printer that I want isn't listed**

6. Pilih:

**Select a shared printer by name**

7. Masukkan:

```text
\\DESKTOP-BLFBREV\Canon MF3010 sari
```

atau jika nama share sebenarnya berbeda, gunakan nama share tersebut.

---

# Ada satu hal penting yang perlu kita cek

Karena dari screenshot komputer sudah bisa melihat:

```text
Network
└── DESKTOP-BLFBREV
     ├── Canon MF3010 sari
     └── Users
```

berarti **akses SMB/network ke komputer server sudah berhasil**.

Jadi untuk kasus Anda, **jangan fokus dulu ke firewall, SMB, atau sharing folder**.

Fokus kita adalah:

```text
✓ Network              → OK
✓ DESKTOP-BLFBREV      → OK
✓ Printer terlihat     → OK
✓ Shared printer       → OK
✕ Driver installation  → BLOCKED
✕ Point and Print      → kemungkinan besar penyebab
```

---

## Saya sarankan kita lakukan diagnosis bertahap

Di **PC yang muncul error tersebut**, buka **CMD as Administrator**, lalu jalankan:

```cmd
whoami
```

kemudian:

```cmd
winver
```

kemudian:

```cmd
reg query "HKLM\Software\Policies\Microsoft\Windows NT\Printers\PointAndPrint"
```

dan:

```cmd
reg query "HKLM\Software\Policies\Microsoft\Windows NT\Printers" /s
```
