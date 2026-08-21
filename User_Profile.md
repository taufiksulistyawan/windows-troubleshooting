Pesan error "The User Profile Service service failed the sign-in. User profile cannot be loaded." pada layar komputer Anda menunjukkan adanya kerusakan (corrupt) pada file profil pengguna atau masalah registri di sistem operasi Windows. Masalah ini membuat sistem tidak dapat membaca data akun Anda saat proses sign-in. [1, 2, 3] 
Berikut adalah langkah-langkah terstruktur untuk mengatasi error tersebut tanpa perlu instal ulang: [4] 
## Langkah 1: Masuk ke Safe Mode
Karena Anda tidak bisa masuk ke Windows secara normal, Anda harus masuk ke Safe Mode terlebih dahulu untuk melakukan perbaikan. [5, 6] 

   1. Di layar sign-in tersebut, tekan dan tahan tombol Shift pada keyboard.
   2. Sambil tetap menahan tombol Shift, klik tombol Power di layar lalu pilih Restart.
   3. Komputer akan melakukan reboot dan masuk ke menu pemulihan biru (Choose an option).
   4. Pilih Troubleshoot > Advanced options > Startup Settings > Restart.
   5. Setelah komputer menyala kembali, tekan tombol angka 4 atau F4 untuk memilih Enable Safe Mode. [1, 6, 7] 

------------------------------
## Langkah 2: Memperbaiki Profil Lewat Registry Editor
Jika Anda berhasil masuk ke dalam Safe Mode, gunakan metode perbaikan registri berikut: [1, 3] 

   1. Tekan tombol Windows + R di keyboard, ketik regedit, lalu tekan Enter. [1] 
   2. Di jendela Registry Editor, arahkan ke folder berikut:
   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList [1, 3] 
   3. Di bawah folder ProfileList, cari dua subfolder yang memiliki nama berawalan S-1-5... dengan rangkaian angka yang sangat panjang dan nama yang sama, tetapi salah satunya diakhiri dengan ekstensi .bak. [1, 8] 
   4. Tukar nama kedua folder tersebut dengan cara berikut:
   * Klik kanan pada folder tanpa .bak, lalu pilih Rename dan tambahkan akhiran .old di belakangnya.
      * Klik kanan pada folder yang berakhiran .bak, pilih Rename, lalu hapus tulisan .bak sehingga folder tersebut kini menjadi tanpa ekstensi.
      * Terakhir, klik kanan pada folder yang tadi diberi nama .old, ganti namanya menjadi berakhiran .bak. [8, 9] 
   5. Klik pada folder yang kini tanpa akhiran .bak tersebut. Di panel sebelah kanan, cari file bernama RefCount dan State. [9, 10] 
   6. Klik dua kali pada masing-masing file tersebut, pastikan nilainya (Value data) diubah menjadi 0, lalu klik OK. [10] 
   7. Tutup Registry Editor dan restart komputer Anda untuk mencoba masuk kembali ke akun normal. [10, 11] 

------------------------------
## Langkah 3: Mengaktifkan Akun Administrator Cadangan (Alternatif)
Jika metode registri di atas terlalu rumit atau tidak berhasil, Anda bisa mengaktifkan akun administrator bawaan Windows untuk membuat akun pengguna baru: [6, 12] 

   1. Masuk kembali ke menu pemulihan biru menggunakan trik Shift + Restart (seperti pada Langkah 1).
   2. Pilih Troubleshoot > Advanced options > Command Prompt.
   3. Di jendela hitam Command Prompt, ketik perintah berikut lalu tekan Enter:
   net user administrator /active:yes
   4. Tutup Command Prompt dan restart komputer Anda.
   5. Di layar login, kini akan muncul akun baru bernama Administrator. Masuklah ke akun tersebut (biasanya tanpa password).
   6. Setelah masuk, buka Settings atau Control Panel untuk membuat akun pengguna lokal baru yang bersih. Anda dapat memindahkan data penting dari folder pengguna lama (C:\Users\NamaUserLama) ke profil yang baru dibentuk tersebut. [3, 6, 9, 10, 11, 12, 13, 14] 

Jika Anda ingin mencoba salah satu langkah di atas dan menemui kendala, beri tahu saya:

* 
* Versi sistem operasi Windows yang digunakan (Windows 10 atau Windows 11?)
* Apakah Anda berhasil masuk ke Safe Mode atau menu pemulihan biru?
* 

Saya dapat memandu Anda melewati setiap tahapan secara lebih detail.

[1] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/3889355/how-to-fix-the-user-profile-service-failed-the-sig)
[2] [https://blog.fokus.co.id](https://blog.fokus.co.id/2023/12/cara-mengatasi-kesalahan-user-profile.html)
[3] [https://www.justanswer.com](https://www.justanswer.com/computer/kk4v0-continue-user-profile-service-failed-not.html)
[4] [https://www.tiktok.com](https://www.tiktok.com/@imawatima/video/7622803523826240776)
[5] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/1635289/how-do-i-fix-the-user-profile-service-failed-the-s)
[6] [https://www.youtube.com](https://www.youtube.com/watch?v=iKvvx9zjlAc)
[7] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/3975975/failed-sign-in-user-profile-cannot-be-loaded)
[8] [https://www.youtube.com](https://www.youtube.com/watch?v=2V2xHTdEFAM)
[9] [https://theitbros.com](https://theitbros.com/user-profile-service-failed-the-sign-in/)
[10] [https://www.geeksforgeeks.org](https://www.geeksforgeeks.org/techtips/fix-user-profile-failed-logon-issues/)
[11] [https://www.tenforums.com](https://www.tenforums.com/tutorials/145678-fix-user-profile-service-failed-sign-error-windows-10-a.html)
[12] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/4340633/the-user-profile-service-service-failed-the-sign-i)
[13] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/4325915/user-profile-service-service-failed-the-logon-user)
[14] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/4161175/the-user-profile-service-service-failed-to-sign-in)
