Error **“The User Profile Service service failed the sign-in. User profile cannot be loaded”** di Windows 10 biasanya terjadi karena **profil user Windows rusak (corrupt)**, terutama registry profil atau folder `C:\Users\NamaUser`.

Kalau ini komputer kantor, saya sarankan **jangan langsung menghapus profil**, karena data Desktop, Documents, Downloads, dan AppData bisa masih diperlukan.

### Cara 1 — Masuk Safe Mode

1. Di layar login, tahan **Shift** lalu klik **Power → Restart**.
2. Pilih:
   **Troubleshoot → Advanced options → Startup Settings → Restart**
3. Tekan **4 / F4** untuk **Safe Mode**.
4. Coba login menggunakan akun yang bermasalah.

Kalau bisa masuk Safe Mode, lanjutkan pemeriksaan.

---

### Cara 2 — Perbaiki ProfileList di Registry

Ini salah satu penyebab paling umum.

1. Login menggunakan **administrator lain**.
2. Tekan `Win + R`.
3. Ketik:

```text
regedit
```

4. Masuk ke:

```text
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList
```

5. Di dalamnya akan ada folder seperti:

```text
S-1-5-21-xxxxxxxxxx-xxxxxxxxxx-xxxxxxxxxx-1001
```

Cari SID yang berkaitan dengan user bermasalah.

Biasanya kasusnya terlihat seperti:

```text
S-1-5-21-xxxx-1001
S-1-5-21-xxxx-1001.bak
```

Jika ada **SID yang sama, tetapi salah satunya memiliki `.bak`**, kemungkinan besar inilah penyebabnya.

Misalnya:

```text
S-1-5-21-xxxx-1001
S-1-5-21-xxxx-1001.bak
```

Yang perlu dilakukan:

* Rename yang **tanpa `.bak`** menjadi misalnya `.old`
* Rename yang **`.bak`** menjadi tanpa `.bak`
* Klik SID tersebut.
* Pastikan:

```text
ProfileImagePath
```

mengarah ke folder user yang benar, misalnya:

```text
C:\Users\taufik
```

Kemudian cek:

```text
State
```

dan:

```text
RefCount
```

Jika ada, ubah nilainya menjadi:

```text
0
```

Setelah itu restart Windows dan coba login.

> **Sebelum mengubah Registry, sebaiknya export key `ProfileList` terlebih dahulu sebagai backup.**

---

### Cara 3 — Kalau tidak ada `.bak`

Kalau struktur registry tidak menunjukkan `.bak`, cek dulu apakah folder profil masih ada.

Misalnya user:

```text
C:\Users\andi
```

Periksa apakah folder tersebut masih berisi:

```text
Desktop
Documents
Downloads
Pictures
AppData
NTUSER.DAT
```

Kalau folder masih ada, **jangan langsung hapus**.

Buat user administrator sementara, lalu login menggunakan administrator tersebut.

Kemudian bisa dibuat profil baru untuk user tersebut dan **data dari profil lama dipindahkan**.

Contohnya:

```text
C:\Users\andi
```

menjadi:

```text
C:\Users\andi.old
```

Setelah user login kembali, Windows akan membuat:

```text
C:\Users\andi
```

yang baru.

Data seperti:

```text
Desktop
Documents
Downloads
Pictures
```

bisa dipindahkan dari:

```text
C:\Users\andi.old
```

ke profil baru.

---

### Cara 4 — Cek file sistem Windows

Kalau masalah bukan hanya satu user, tetapi beberapa user mengalami masalah login, saya akan mengecek sistem Windows juga.

Buka **Command Prompt as Administrator**, kemudian:

```cmd
sfc /scannow
```

Setelah selesai:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

Kemudian restart:

```cmd
shutdown /r /t 0
```

---

### Cara menentukan penyebabnya

Untuk troubleshooting IT Support, saya biasanya membaginya seperti ini:

| Kondisi                                  | Kemungkinan                           |
| ---------------------------------------- | ------------------------------------- |
| Hanya 1 user gagal login                 | Profile user corrupt                  |
| Semua user gagal login                   | Windows/System Service bermasalah     |
| Ada SID `.bak`                           | Registry profile bermasalah           |
| `C:\Users\user` masih ada                | Data kemungkinan masih aman           |
| Folder user hilang                       | Perlu cek backup/recovery             |
| Setelah update Windows                   | Bisa terkait update/profile           |
| Disk hampir penuh                        | Bisa menyebabkan profile gagal dibuat |
| HDD/SSD bermasalah                       | Bisa menyebabkan profile corrupt      |
| User bisa login setelah dibuat akun baru | Hampir pasti profile lama bermasalah  |

### ⚠️ Yang paling penting

**Jangan langsung melakukan:**

```text
del C:\Users\username
```

atau menghapus SID dari Registry.

Karena kalau ternyata data profil masih dibutuhkan, kita bisa kehilangan data user.

Kalau ini komputer kantor dan **data user masih penting**, urutan yang paling aman adalah:

**Backup profil → cek Registry ProfileList → perbaiki `.bak` jika ada → SFC/DISM → jika gagal, buat profil baru → migrasikan data.**

Kalau Anda kirim **foto isi `ProfileList` di Registry** (bagian `S-1-5-21...`) dan beri tahu **nama user yang gagal login**, saya bisa bantu tunjukkan **SID mana yang harus diperbaiki dan nilai mana yang perlu diubah**, langkah demi langkah.
