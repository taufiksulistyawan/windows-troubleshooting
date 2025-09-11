Langkah **step-by-step cepat** biar IP yang “nyangkut” bisa dipakai lagi:

---

## 🔧 Step 1 – Hapus ARP di Mikrotik

Masuk ke terminal Mikrotik lalu jalankan:

```bash
/ip arp remove [find address=<IP_bermasalah>]
```

---

## 🔧 Step 2 – Hapus DHCP Lease (kalau ada)

Cek dulu:

```bash
/ip dhcp-server lease print where address=<IP_bermasalah>
```

Kalau ada, hapus:

```bash
/ip dhcp-server lease remove [find address=<IP_bermasalah>]
```

---

## 🔧 Step 3 – Flush ARP di PC User

* **Windows:**

  ```cmd
  arp -d *
  ipconfig /release
  ipconfig /renew
  ```

  (atau restart adapter jaringan biar cepat)

* **Linux:**

  ```bash
  sudo ip neigh flush all
  ```

---

## 🔧 Step 4 – Assign Ulang IP

Set ulang manual IP user ke:

* IP: `<IP_bermasalah>`
* Subnet: sesuai jaringan
* Gateway: IP Mikrotik
* DNS: bisa pakai 8.8.8.8 atau IP Mikrotik

Lalu coba ping ke:

```bash
ping <gateway>
```

---

## 🔧 Step 5 – Cek Duplicate

Kalau masih gagal, cek apakah ada perangkat lain diam-diam pakai IP tersebut:

```bash
/tool arp-ping <IP_bermasalah>
```

* Kalau keluar MAC selain PC user → berarti ada **device lain bentrok**.
* Kalau kosong → berarti aman, tinggal pastikan konfigurasi PC user benar.

---

⚡ Biasanya setelah Step 1 & 3, IP sudah bisa dipakai lagi.
Kalau tetap bermasalah → hampir pasti ada **device lain** di jaringan yang pakai IP itu.
