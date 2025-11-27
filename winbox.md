Baik, saya buatkan **langkah-langkah lengkap di Winbox GUI** untuk konfigurasi ISP static dengan topologi berikut:

---

# 🔵 **TOPOLOGI**

* **WAN Static (ISP 2)**

  * Masuk ke **ether6**
  * IP dari modem: **20.30.40.28/24**
  * Gateway modem: **20.30.40.1**

* **LAN / Client**

  * Keluar di **ether3**
  * Network LAN: **192.168.30.0/24**
  * Gateway LAN (router): **192.168.30.254**

Dengan NAT + DHCP lengkap.

---

# 🟩 **LANGKAH-LANGKAH DETAIL DI WINBOX GUI**

---

# ✔ **1. Set IP Static WAN di ether6**

1. Buka Winbox
2. Masuk ke menu **IP → Addresses**
3. Klik **"+"**
4. Isi:

   * **Address:** `20.30.40.28/24`
   * **Interface:** `ether6`
5. Klik **Apply → OK**

---

# ✔ **2. Tambahkan Default Route (Gateway)**

1. Buka **IP → Routes**
2. Klik **"+"**
3. Isi:

   * **Gateway:** `20.30.40.1`
4. Klik **Apply → OK**

> Ini wajib supaya router tahu jalan ke internet.

---

# ✔ **3. Buat IP untuk LAN di ether3**

1. Buka **IP → Addresses**
2. Klik **"+"**
3. Isi:

   * **Address:** `192.168.30.254/24`
   * **Interface:** `ether3`
4. Klik **Apply → OK**

---

# ✔ **4. Buat IP Pool untuk DHCP**

1. Buka **IP → Pool**
2. Klik **"+"**
3. Isi:

   * **Name:** `pool-lan30`
   * **Addresses:** `192.168.30.2-192.168.30.253`
4. Klik **Apply → OK**

---

# ✔ **5. Buat DHCP Server**

1. Buka **IP → DHCP Server**
2. Pilih tab **DHCP**
3. Klik **DHCP Setup**
4. Pilih interface: **ether3**
5. Klik **Next**

Kemudian isi:

| Step                  | Isian                           |
| --------------------- | ------------------------------- |
| DHCP Address Space    | otomatis muncul 192.168.30.0/24 |
| Gateway               | **192.168.30.254**              |
| Addresses to Give Out | 192.168.30.2-192.168.30.253     |
| DNS Servers           | 192.168.30.254 atau 8.8.8.8     |
| Lease Time            | default                         |

Klik **Next** sampai selesai.

---

# ✔ **6. NAT Masquerade (Wajib untuk Internet)**

1. Buka **IP → Firewall**
2. Masuk tab **NAT**
3. Klik **"+"**
4. Tab **General**

   * **Chain:** `srcnat`
   * **Out. Interface:** `ether6`
5. Tab **Action**

   * **Action:** `masquerade`
6. Klik **Apply → OK**

---

# ✔ **7. Cek koneksi**

### Dari MikroTik:

1. Buka **New Terminal**
2. Jalankan:

```
ping 20.30.40.1
```

Jika reply = OK

3. Lalu:

```
ping 8.8.8.8
```

Jika reply = OK → internet WAN static sudah jalan.

### Dari Client:

* IP harus dapat dari DHCP (192.168.30.x)
* Gateway harus 192.168.30.254
* Coba browsing

---

# 🎉 **Konfigurasi ISP Static Selesai**

Kalau kamu ingin ISP 1 dan ISP 2 berjalan bersamaan (load balancing / failover), tinggal bilang → saya buatkan skrip + langkah GUI-nya.
