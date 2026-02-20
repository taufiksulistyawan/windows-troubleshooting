Berikut beberapa cara **mematikan komputer yang nyala otomatis** (biasanya karena pengaturan BIOS, Windows, atau jadwal tertentu). Coba cek satu per satu:

---

# 1. Matikan **Wake Timers** di Windows

Fitur ini bisa membuat komputer menyala sendiri karena jadwal sistem.

1. Buka **Control Panel** → **Power Options**.
2. Klik **Change plan settings** pada power plan yang dipakai.
3. Klik **Change advanced power settings**.
4. Cari **Sleep** → **Allow wake timers**.
5. Ubah menjadi **Disable**.

---

# 2. Cek **Task Scheduler**

Kadang ada jadwal otomatis yang menyalakan PC.

1. Tekan **Windows + R**
2. Ketik:

   ```
   taskschd.msc
   ```
3. Buka **Task Scheduler Library**.
4. Cari task yang memiliki opsi **Wake the computer to run this task** lalu **Disable**.

---

# 3. Matikan **Fast Startup**

Kadang PC terlihat mati tapi sebenarnya hibernasi.

1. Buka **Control Panel** → **Power Options**.
2. Klik **Choose what the power buttons do**.
3. Klik **Change settings that are currently unavailable**.
4. Hilangkan centang **Turn on fast startup**.

---

# 4. Cek Pengaturan di **BIOS / UEFI**

Ini penyebab paling sering komputer menyala sendiri.

Masuk BIOS (biasanya tekan **Del / F2 / F10** saat boot), lalu cari dan **Disable**:

* **Power On By RTC Alarm**
* **Wake on LAN**
* **Power On After Power Loss**
* **Resume By Alarm**

---

# 5. Matikan Wake dari Perangkat (Mouse / Keyboard / LAN)

1. Klik kanan **Start** → **Device Manager**.
2. Buka:

   * Network Adapter
   * Keyboard
   * Mouse
3. Klik device → **Properties** → Tab **Power Management**.
4. Hilangkan centang:

   ```
   Allow this device to wake the computer
   ```

---

✅ Cara cepat cek penyebab komputer bangun sendiri:
Buka **Command Prompt (Run as Administrator)** lalu ketik:

```
powercfg -lastwake
```

Kalau mau, kirimkan hasilnya ke sini — saya bisa bantu analisis **kenapa komputer kamu nyala sendiri**.
