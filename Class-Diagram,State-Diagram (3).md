## 1. Class Diagram

```mermaid
classDiagram
    class Pengguna {
        +int idPengguna
        +string nama
        +string peran
        +login()
        +logout()
    }

    class Kendaraan {
        +string nomorPolisi
        +string jenis
        +dataKendaraan()
    }

    class SlotParkir {
        +string idSlot
        +string jenisKendaraan
        +string status
        +cekKetersediaan()
        +ubahStatus()
    }

    class TransaksiParkir {
        +int idTransaksi
        +datetime waktuMasuk
        +datetime waktuKeluar
        +catatMasuk()
        +catatKeluar()
    }

    Pengguna "1" --> "0..*" TransaksiParkir : mengelola
    Kendaraan "1" --> "0..*" TransaksiParkir : tercatat dalam
    SlotParkir "1" --> "0..*" TransaksiParkir : digunakan pada
```

### Keterangan Class
- **Pengguna:** menyimpan informasi pengguna sistem.
- **Kendaraan:** menyimpan nomor polisi dan jenis kendaraan.
- **SlotParkir:** menyimpan identitas slot dan status kosong atau terisi.
- **TransaksiParkir:** menyimpan waktu kendaraan masuk dan keluar.

## 2. State Diagram

State diagram berikut menggambarkan status **Review/Ulasan Parkir**.

```mermaid
stateDiagram-v2
    [*] --> BelumDikirim
    BelumDikirim --> MenungguModerasi: Pengguna mengirim ulasan
    MenungguModerasi --> Dipublikasikan: Admin menyetujui
    MenungguModerasi --> Ditolak: Admin menolak
    Ditolak --> BelumDikirim: Pengguna memperbaiki ulasan
    Dipublikasikan --> [*]
```

### Keterangan Status
- **Belum Dikirim:** pengguna belum mengirim ulasan.
- **Menunggu Moderasi:** ulasan menunggu pemeriksaan admin.
- **Dipublikasikan:** ulasan disetujui dan dapat dilihat pengguna lain.
- **Ditolak:** ulasan tidak disetujui dan perlu diperbaiki sebelum dikirim kembali.
