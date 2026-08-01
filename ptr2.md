Jika layanan Workstation tidak ada di dalam daftar services.msc, ini adalah akar masalah yang membuat komputer Anda kehilangan kemampuan dasar untuk berkomunikasi di jaringan LAN (termasuk memblokir Remote Desktop dan File Sharing). Layanan ini (nama sistemnya adalah LanmanWorkstation) kemungkinan terhapus karena korupsi sistem, infeksi virus/malware lama, atau kesalahan Registry. [1, 2] 
Berikut adalah langkah-langkah untuk memulihkan dan memasang kembali layanan Workstation yang hilang:
## 1. Periksa Apakah Komponen "Client for Microsoft Networks" Terpasang
Layanan Workstation secara fisik terikat dengan komponen kartu jaringan ini. Jika komponen ini terhapus, layanannya akan hilang. [2] 

* 
* Tekan Windows + R, ketik ncpa.cpl, lalu tekan Enter untuk membuka Network Connections.
* Klik kanan pada koneksi internet yang Anda gunakan (Wi-Fi atau Ethernet), lalu pilih Properties.
* Periksa daftarnya, apakah ada komponen bernama Client for Microsoft Networks?
* Jika TIDAK ADA: Klik tombol Install > pilih Client > klik Add > pilih Client for Microsoft Networks > klik OK. Setelah terpasang, restart komputer Anda. [2] 
* 

## 2. Lakukan Scan Perbaikan Berkas Sistem (SFC & DISM)
Jika komponen di atas sudah ada tetapi layanannya tetap hilang, sistem Windows Anda mendeteksi adanya kerusakan file inti dan perlu dipulihkan secara otomatis. [3, 4] 

* 
* Tekan tombol Windows, ketik cmd, lalu klik kanan pada Command Prompt dan pilih Run as administrator.
* Ketik perintah berikut lalu tekan Enter:

sfc /scannow

* Tunggu hingga proses verifikasi mencapai 100%. Jika tertulis ada file rusak yang berhasil diperbaiki, lakukan restart komputer.
* Jika belum berhasil, buka CMD sebagai administrator lagi, jalankan perintah ini untuk mengunduh ulang komponen sistem yang hilang langsung dari server Microsoft:

DISM /Online /Cleanup-Image /RestoreHealth

* Setelah selesai, restart komputer Anda kembali. [3, 4, 5] 
* 

## 3. Daftarkan Ulang Layanan Workstation lewat Command Prompt
Anda bisa mencoba memaksa Windows untuk membuat ulang entri layanan Workstation yang hilang tersebut.

* 
* Buka kembali Command Prompt (Admin).
* Ketik perintah di bawah ini secara presisi dan tekan Enter:

sc create LanmanWorkstation binpath= "C:\Windows\System32\svchost.exe -k NetworkService" DisplayName= "Workstation" start= auto

* Jika muncul tulisan [SC] CreateService SUCCESS, berarti layanan berhasil dibuat ulang. Silakan buka kembali services.msc untuk memastikannya sudah muncul. [3, 4] 
* 

## 4. Solusi Terakhir: Lakukan System Restore
Jika registri layanan tersebut rusak parah atau terhapus total karena virus, mengembalikan kondisi Windows ke tanggal sebelum masalah ini terjadi adalah jalan keluar paling aman. [4, 5] 

* 
* Tekan Windows + S, ketik Create a restore point, lalu buka menu tersebut.
* Klik tombol System Restore.
* Pilih tanggal atau poin waktu saat komputer Anda masih bisa melakukan sharing data dengan normal.
* Ikuti petunjuknya hingga komputer melakukan restart dan memulihkan pengaturan lama. [4, 5] 
* 

Silakan dicoba dari Langkah 1 terlebih dahulu. Apakah komponen Client for Microsoft Networks ditemukan di pengaturan kartu jaringan Anda? Jika Anda menemukannya namun memunculkan error tertentu, beri tahu saya.
