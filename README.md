# 🅿️ Smart Parking Digital Twin Kampus

![Animasi mobil memasuki slot C-03. Status berubah dari kosong menjadi terisi.](assets/smart-parking.gif)

Proyek mata kuliah **Rekayasa Perangkat Lunak** di Universitas Samudra, Langsa. Website ini membantu mahasiswa melihat petak parkir yang tersedia dan membantu admin memantau penggunaan area parkir melalui simulasi.

## 🗺️ Gambaran proyek

Denah 2D mewakili 20 petak parkir kampus, terdiri dari 10 slot motor (`M-01` hingga `M-10`) dan 10 slot mobil (`C-01` hingga `C-10`). Setiap slot memiliki kode dan status. Ketika kendaraan simulasi menempati atau meninggalkan petak, warna slot, jumlah kendaraan, dan persentase keterisian ikut berubah.

🟢 **Kosong**　🔴 **Terisi**

Pada prototipe ini, peristiwa parkir berasal dari simulator di browser. Data berlaku selama satu sesi dan kembali kosong ketika halaman dimuat ulang.

## 👥 Pengguna dan fitur

| Pengguna | Kebutuhan | Fitur |
| --- | --- | --- |
| Mahasiswa | Menemukan tempat parkir sesuai jenis kendaraan | Melihat jumlah slot tersisa dan memilih petak pada denah untuk memeriksa statusnya. Hijau berarti kosong, merah berarti terisi. |
| Admin | Memantau dan menguji penggunaan area parkir | Menjalankan atau menjeda simulasi, mengubah slot secara manual saat dijeda, mencari kendaraan berdasarkan pelat atau kode slot, serta mengekspor riwayat masuk dan keluar ke CSV. |

## 🚗 Contoh simulasi

Saat seluruh petak kosong, satu mobil masuk ke `C-03`. Petak itu berubah menjadi merah, tersisa 9 slot mobil dan 10 slot motor, dan tingkat keterisian menjadi **1 dari 20 slot (5%)**. Ketika mobil keluar, `C-03` kembali hijau. Admin dapat melihat kedua kejadian tersebut di riwayat sesi.

## ▶️ Menjalankan prototipe

1. Unduh atau klon repositori, lalu buka `index.html` di browser. Prototipe dibangun dengan HTML, CSS, dan JavaScript.
2. Pada mode **Admin**, klik **Mulai Simulasi** untuk melihat perubahan pada denah.
3. Untuk mencoba contoh di atas, mulai dengan denah kosong, klik **C-03**, lalu pilih **Isi Slot (Uji)** saat simulasi belum berjalan atau sedang dijeda.

## 🎓 Tim proyek

| Nama anggota | NIM | GitHub |
| --- | --- | --- |
| Muhammad Nabil | 240504087 | [@ABIEL050](https://github.com/ABIEL050) |
| Yana Putra Hamdalah | 240504079 | [@yanpha30](https://github.com/yanpha30) |
| Ariel Rizky Ardiansyah | 240504082 | [@arielrizky](https://github.com/arielrizky) |
