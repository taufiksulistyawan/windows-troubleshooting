## 🔧 Yuk kita rapikan

### 1. Hapus route default yang nyangkut

Jalankan:

```cmd
route delete 0.0.0.0
```

Lalu cek lagi:

```cmd
route print
```

Pastikan tidak ada lagi `0.0.0.0` di **Active Routes** maupun **Persistent Routes**.

---

### 2. Tambahkan ulang default route

Sekarang tambahkan manual:

```cmd
route add 0.0.0.0 mask 0.0.0.0 192.168.20.1 metric 1 if 20
```
> `if 20` sesuai dengan interface number UE200 kamu (lihat di atas: `Interface List` → `20...28 ee 52 05 31 8e` = nomor 20).

Kalau berhasil, cek lagi:

Kalau sudah beres, biar permanen:

```cmd
route -p add 0.0.0.0 mask 0.0.0.0 192.168.20.1 metric 1 if 20
```

---

### 3. Tes koneksi

```cmd
ping 192.168.20.1
ping 8.8.8.8
ping google.com
```
