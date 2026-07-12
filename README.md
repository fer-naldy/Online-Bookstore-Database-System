# Database Toko Buku Online

Proyek Tugas Kelompok mata kuliah **Project Database** yang merancang dan mengimplementasikan basis data relasional untuk sistem **toko buku online**, mulai dari perancangan konseptual (ER-Diagram) hingga simulasi operasi database (CRUD & JOIN) menggunakan SQLite.

## Tentang Proyek

### Latar Belakang

**Permasalahan:** Pencatatan informasi transaksi pada toko buku online secara manual menyebabkan pekerjaan menjadi tidak efisien.

**Solusi:** Pembuatan basis data (database) sebagai sarana teknologi informasi untuk mempermudah sistem penjualan toko buku online. Dengan basis data, toko buku dapat memastikan catatan yang akurat mengenai pembelian, informasi buku, dan detail lain seperti penulis maupun ulasan, sehingga dapat melacak penjualan, pembelian, dan inventaris secara lebih efisien dan meningkatkan produktivitas.

## Anggota Kelompok 6

| Nama | NPM |
|---|---|
| Fernaldy | 2106706464 |
| Jihan Sandrina Halim | 2106708160 |
| Jovina Nareswari | 2106708223 |
| Niken Salsabila Helmelia | 2106724933 |

## Metode Penelitian

### A. Perancangan Database Level Konseptual
1. Pembuatan entitas dan atribut
2. Menentukan primary key dan foreign key pada tiap entitas
3. Merancang sistem database yang akan berlaku
4. Pembuatan ER-Diagram

### B. Perancangan Database Level Logikal
1. Konversi ERD ke dalam tabel relasional
2. Kebijakan akses admin
3. Penulisan *code*, simulasi, dan analisis

## Struktur Database

Database terdiri dari **8 entitas** yang saling berelasi: **Pembeli**, **Pesanan**, **Buku**, **Penulis**, **Pembayaran**, **Penjual**, **Pengiriman**, dan **Ulasan**.

### Alur Relasi Antar Entitas
- **Pembeli** login menggunakan username & password, lalu dapat membuat satu atau lebih **Pesanan**.
- **Pesanan** dapat berisi satu atau lebih **Buku**; setiap buku ditulis oleh satu **Penulis** (satu penulis dapat menulis banyak buku).
- Setiap **Pesanan** dilakukan satu **Pembayaran**, yang dikonfirmasi oleh satu **Penjual**.
- **Penjual** melakukan satu **Pengiriman**, yang dikirimkan ke satu **Pembeli**.
- Setelah barang sampai, **Pembeli** dapat memberikan satu **Ulasan** atas pembeliannya.

### Tabel & Atribut Utama

| Tabel | Primary Key | Atribut Lain |
|---|---|---|
| Pembeli | ID_Pembeli | Pass, Nama_Pembeli, Alamat, Kota, No_HP |
| Pesanan | Nomor | No_Pesanan, Jumlah_Pesanan, Waktu_Transaksi, ISBN (FK), ID_Pembeli (FK) |
| Buku | ISBN | Judul_Buku, Deskripsi, Kategori, Tanggal_Publikasi, Penerbit, Stok, Harga, ID_Penulis (FK) |
| Penulis | ID_Penulis | Nama_Penulis |
| Pembayaran | No_Pembayaran | Metode_Pembayaran, Total_Harga, No_Pesanan (FK), ID_Penjual (FK) |
| Penjual | ID_Penjual | Nama_Penjual |
| Pengiriman | ID_Pengiriman | Ongkos_Kirim, Waktu_Pengiriman, ID_Pembeli (FK), No_Pesanan (FK), ID_Penjual (FK) |
| Ulasan | — | Ulasan, Tanggal_Ulasan, ID_Pembeli (FK) |

## Penggunaan Software

Database dibuat dan dikelola menggunakan **SQLite (DB Browser for SQLite)**, dengan alasan:
1. Perangkat lunak **open source** dan gratis, sehingga dapat diakses siapa saja tanpa biaya tambahan.
2. Cukup mudah dipahami dalam pengaplikasiannya.

## Simulasi Sistem Database

Proyek ini mendemonstrasikan operasi dasar SQL pada database bernama **"Project Database Toko Buku Online"**:

1. **CREATE TABLE** — pembuatan seluruh tabel (Pembeli, Pesanan, Buku, Penulis, Pengiriman, Penjual, Pembayaran, Ulasan) lengkap dengan constraint `PRIMARY KEY` dan `FOREIGN KEY`.
2. **Data Dummy** — pengisian data contoh pada setiap tabel untuk keperluan simulasi.
3. **INSERT** — menambahkan baris pesanan baru untuk pembeli yang melakukan pemesanan ulang.
4. **UPDATE** — memperbarui data pembeli (contoh: mengubah nomor HP).
5. **DELETE** — menghapus akun pembeli beserta pengujian hasilnya melalui query `SELECT`.
6. **JOIN** — menggabungkan data antar tabel, misalnya:
   - Melihat jumlah pesanan per judul buku (`PESANAN` ⨝ `BUKU`).
   - Melihat ulasan untuk tiap pesanan (`ULASAN` ⨝ `PESANAN`).

## Analisis

Berdasarkan hasil simulasi:
- Akun pembeli yang telah tersimpan dapat diperbarui secara berkala sehingga pembeli bisa login dan memesan kembali dengan akun yang sama.
- Data pesanan dapat memberi informasi buku apa yang paling banyak terjual, berguna untuk personalisasi rekomendasi produk atau promosi.
- Data ulasan yang di-*join* dengan data pesanan dapat digunakan sebagai indikator untuk meningkatkan kualitas pelayanan.

## Kesimpulan

1. Pembuatan database dapat membantu penjual toko online menyimpan informasi mengenai produk dan transaksinya secara sistematis.
2. Pembuatan database mampu memberi *insight* lebih dalam kepada penjual toko online, contohnya melihat preferensi pembeli mengenai produk yang dijual.

## Struktur Presentasi

```
1. Latar Belakang
2. Metode Penelitian
3. ER-Diagram
4. Tabel Relasi
5. Penggunaan Software
6. Simulasi Sistem Database
   ├── Membuat Database & Tabel (CREATE TABLE)
   ├── Membuat Data Dummy
   ├── INSERT (ROW)
   ├── UPDATE
   ├── DELETE
   └── JOIN
7. Analisis
8. Kesimpulan
```

