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
