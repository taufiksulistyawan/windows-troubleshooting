Kalau maksudmu **Photoshop 2025 sering force close**, penyebab paling sering adalah **GPU/driver, preference Photoshop corrupt, plugin, font, atau bug versi Photoshop tertentu**. Adobe sendiri merekomendasikan pengecekan GPU, reset preference, plugin, dan update sebagai langkah utama. ([Adobe Help Center][1])

Coba urutkan seperti ini:

1. **Tes tanpa GPU**

   * Buka Photoshop
   * `Edit → Preferences → Performance`
   * Hilangkan centang **Use Graphics Processor**
   * Restart Photoshop
   * Coba pekerjaan yang biasanya menyebabkan force close.

   Kalau setelah GPU dimatikan Photoshop normal, kemungkinan besar masalah ada di **driver GPU atau kompatibilitas GPU**. ([Adobe Help Center][2])

2. **Reset Preferences**

   Tutup Photoshop → tahan **Ctrl + Alt + Shift** sambil membuka Photoshop → pilih **Yes** untuk menghapus pengaturan Photoshop. ([Adobe Help Center][2])

3. **Update driver VGA**

   Kalau PC-mu masih menggunakan **GTX 1050 Ti**, saya justru akan mengecek driver NVIDIA terlebih dahulu. Driver yang corrupt/tidak kompatibel dapat menyebabkan Photoshop crash. ([Adobe Help Center][2])

4. **Tes tanpa plugin**

   Tutup Photoshop → tahan **Shift** saat menjalankan Photoshop → pilih opsi untuk melewati plugin pihak ketiga. Kalau kemudian tidak crash, kemungkinan ada plugin yang bermasalah. ([Adobe Help Center][1])

5. **Cek font**

   Font yang rusak/bermasalah juga bisa menyebabkan Photoshop crash atau hang. Adobe menyarankan membersihkan **CT Font Cache** jika dicurigai masalah font. ([Adobe Help Center][1])

6. **Kalau mulai terjadi setelah update Photoshop 2025**

   Ada laporan komunitas Adobe mengenai beberapa versi Photoshop 2025 yang mengalami masalah launch/crash, sehingga **mencoba versi sebelumnya** bisa menjadi langkah diagnosis yang masuk akal. ([Adobe][3])

### Kalau mau kita cari penyebab pastinya

Kirim saya **screenshot saat Photoshop force close** atau **foto pesan/error yang muncul**. Kalau tidak ada pesan sama sekali, kirim screenshot **Reliability Monitor Windows** setelah crash.

Kalau kamu kirim itu, saya bisa bantu menentukan apakah lebih mengarah ke **GPU, RAM, driver NVIDIA, Photoshop, plugin, atau Windows**.

[1]: https://helpx.adobe.com/photoshop/kb/troubleshoot-crash-or-freeze.html?utm_source=chatgpt.com "Troubleshoot crash or freeze in Photoshop | Photoshop"
[2]: https://helpx-origin-ew1.aws116.adobeitc.com/il_en/photoshop/desktop/troubleshoot/performance-stability-issues/resolve-graphics-processor-gpu-and-graphics-driver-issues.html?utm_source=chatgpt.com "Resolve GPU and graphics driver issues in Photoshop | Photoshop"
[3]: https://community.adobe.com/t5/photoshop-ecosystem-discussions/photoshop-v26-7-is-now-available/m-p/15339595?utm_source=chatgpt.com "Unable to launch Photoshop 2025 version 26.7 - Adobe Product Community - 15339595"
