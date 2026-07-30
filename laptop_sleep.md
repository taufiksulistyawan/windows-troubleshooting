Berdasarkan dokumen System Power Report dari laptop HP 240 G6 Anda, sistem Anda sebenarnya tidak masuk ke mode Sleep, melainkan mengalami Shutdown (Hybrid).
Fitur Hybrid Shutdown (bagian dari Fast Startup Windows) bertugas menyimpan sesi kerja terakhir ke dalam harddisk sebelum mati. Hal inilah yang membuat pekerjaan Anda kembali utuh saat laptop dinyalakan kembali, sehingga perilakunya mirip seperti mode sleep.
Berikut analisis log aktivitas fatal yang terjadi pada hari ini (30 Juli 2026):
## Kronologi Masalah pada Log Anda

   1. 08:13:14 - Laptop menyala dan Anda gunakan secara aktif selama 7 menit.
   2. 08:20:44 - Laptop tiba-tiba mati paksa secara instan masuk ke mode Shutdown (Hybrid). Log mencatat pemicunya adalah Application API. Ini berarti ada aplikasi atau driver sistem pihak ketiga yang mengirim perintah mati darurat ke Windows.
   3. 08:25:17 - Anda menyalakan kembali laptop Anda. Terlihat status daya berubah karena adanya pasokan listrik masuk (Power Source Changed).

------------------------------
## Solusi dan Langkah Perbaikan
Melihat spesifikasi laptop HP Anda yang menggunakan BIOS versi lama tahun 2018, serta pemicu Application API, berikut adalah langkah-langkah penanganan yang harus Anda lakukan:
## 1. Matikan Fitur Fast Startup (Solusi Utama)
Sering kali Fast Startup mengalami eror komunikasi driver yang membuat laptop mati sendiri saat mendeteksi lonjakan daya minor.

* Buka Control Panel > Power Options.
* Klik Choose what the power buttons do di bilah kiri.
* Klik Change settings that are currently unavailable.
* Hilangkan tanda centang pada opsi Turn on fast startup.
* Klik Save changes dan restart laptop Anda.

## 2. Copot Sementara Aplikasi Antivirus Pihak Ketiga
Pada log penggunaan daya hari sebelumnya, sistem mendeteksi aktivitas pemindaian intensif dari aplikasi Smadav.exe. Beberapa antivirus lokal atau pihak ketiga yang tidak kompatibel dengan pembaruan Windows terbaru dapat salah mengirim perintah Application API (mengira ada ancaman fatal atau mengalami crash internal yang memicu proteksi sistem). Cobalah hapus instalasi antivirus tersebut sementara waktu dan andalkan Windows Defender bawaan untuk melihat apakah masalahnya selesai.
## 3. Kalibrasi Perangkat Keras dan Driver Baterai
Log Anda menunjukkan status kapasitas baterai Anda tertulis NaN% (tidak terbaca oleh sistem). Windows kemungkinan besar mematikan paksa laptop karena mengira sisa baterai Anda mendadak 0% (critical battery level).

* Klik kanan tombol Start > pilih Device Manager.
* Bentangkan menu Batteries.
* Klik kanan pada Microsoft ACPI-Compliant Control Method Battery, lalu pilih Uninstall device.
* Jangan khawatir, cukup lakukan Restart laptop Anda. Windows akan otomatis memasang kembali driver baterai yang bersih dan segar setelah menyala.

Bila setelah mematikan Fast Startup laptop masih tiba-tiba mati saat tengah bekerja, beri tahu saya apakah saat kejadian laptop Anda sedang dicolok ke charger atau murni menggunakan baterai.
