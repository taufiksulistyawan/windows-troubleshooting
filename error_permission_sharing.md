Error **“Windows cannot access”** saat membuka **Network File Sharing** di Windows 10 biasanya disebabkan oleh masalah permission, network discovery, SMB, atau firewall. Berikut langkah-langkah yang bisa Anda cek satu per satu.

---

## 1. Pastikan Network Discovery dan File Sharing Aktif

1. Buka **Control Panel**
2. Pilih **Network and Internet**
3. Klik **Network and Sharing Center**
4. Pilih **Change advanced sharing settings**
5. Aktifkan:

   * **Turn on network discovery**
   * **Turn on file and printer sharing**

Kemudian **Save changes**.

---

## 2. Cek Apakah Komputer Bisa Diping

Untuk memastikan jaringan normal.

1. Tekan **Windows + R**
2. Ketik:

```
cmd
```

3. Ping komputer tujuan:

```
ping 192.168.1.xxx
```

Jika **Reply**, berarti jaringan terhubung.

---

## 3. Cek Permission Folder yang Dishare

1. Klik kanan folder yang di share
2. Pilih **Properties**
3. Masuk ke tab **Sharing**
4. Klik **Advanced Sharing**
5. Centang **Share this folder**
6. Klik **Permissions**
7. Tambahkan **Everyone**
8. Beri izin **Full Control** atau minimal **Read**

---

## 4. Cek Security Permission

Masih di **Properties**:

1. Buka tab **Security**
2. Klik **Edit**
3. Tambahkan **Everyone**
4. Beri izin **Read / Modify**

---

## 5. Aktifkan SMB 1.0 (Jika Komputer Lama)

Kadang error muncul karena SMB dimatikan.

1. Tekan **Windows + R**
2. Ketik:

```
optionalfeatures
```

3. Centang:

```
SMB 1.0/CIFS File Sharing Support
```

4. Restart komputer.

---

## 6. Matikan Password Protected Sharing (Jika Jaringan Lokal)

1. Masuk **Advanced sharing settings**
2. Scroll ke bawah
3. Pilih:

```
Turn off password protected sharing
```

---

## 7. Coba Akses dengan IP Address

Kadang hostname tidak terbaca.

Di **Run (Windows + R)** ketik:

```
\\192.168.1.xxx
```

bukan

```
\\namakomputer
```

---

## 8. Cek Service Sharing Windows

Tekan **Windows + R**

```
services.msc
```

Pastikan service ini **Running**:

* **Server**
* **Workstation**
* **Function Discovery Provider Host**
* **Function Discovery Resource Publication**

---

💡 **Tips tambahan (sering terjadi di kantor):**

Jika muncul error seperti:

* **0x80070035**
* **Windows cannot access \PC**

biasanya karena:

* Network profile masih **Public**
* Firewall Windows memblokir sharing
* Komputer beda **workgroup**

Cek juga **Workgroup**:

```
System Properties → Computer Name
```

Samakan misalnya:

```
WORKGROUP
```

---
