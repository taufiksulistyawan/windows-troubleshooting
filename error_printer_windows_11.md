## **Cara Memperbaiki Error Printer Windows 11 Kode 0x00000040 / 0x00000709**

## **Langkah-langkah pada PC Server (Server Printer)**

1. Buka **Windows Search**, kemudian ketik dan buka **Windows Features** atau **Turn Windows features on or off**.
2. Gulir ke bawah dan **aktifkan fitur SMB 1.0/CIFS File Sharing Support (SMB1)**.
3. Klik **OK**, kemudian **restart** PC server.

---

## **Langkah-langkah pada PC Client (Windows 11)**

1. Buka **Command Prompt** sebagai **Administrator**.

2. Jalankan perintah berikut untuk mengaktifkan protokol Named Pipe RPC:

   ```
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT\Printers\RPC" /v RpcUseNamedPipeProtocol /t REG_DWORD /d 1 /f
   ```

3. Setelah perintah berhasil dijalankan, restart PC dengan perintah:

   ```
   shutdown -r -f -t 00
   ```

   Link Video:
   https://youtu.be/nkm9adHeN-Y?si=2-t6DDpskbtjcW58

### 1. pc server
regedit
HLM\SYSTEM\CurentControlSet\control\Print
Dword 32bit
```
RpcAuthLevelPrivacyEnabeled
```
hexadecimal 0
restart pc
### 2. client
services.msc
stop print spooler
Exloler > C: > Windows > System32 > Spool> PRINTERS (hapus)
Copy abd replace file: https://drive.google.com/file/d/1bCQ78cLf-F2TIO_hAAJ3ZxEwPnri4vcp/view?usp=sharing
C: > Windows > System32

aktifkan print spool
restart
### 3. tidak bisa replace
klik kanan file 
properties
security
advance> change> tambahkan Administrator> cek name. oke apply
change permissions> trustet di ganti reade dan write saja> 
Administrator jadi full control
