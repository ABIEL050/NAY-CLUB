# Tugas Kelompok Rekayasa Perangkat Lunak (RPL)

## 1. System Boundary dan External Entities

### System Boundary
Sistem yang dibahas adalah **Smart Parking Digital Twin Kampus**, yaitu sistem untuk menampilkan denah parkir, memantau ketersediaan slot, mencatat kendaraan masuk dan keluar, serta mengelola data parkir.

### External Entities
1. **Mahasiswa** — melihat denah dan ketersediaan slot parkir.
2. **Petugas Parkir** — mencatat kendaraan masuk dan keluar.
3. **Admin Kampus** — mengelola data slot dan melihat laporan parkir.

## 2. Context Model

```mermaid
flowchart TB
    M[Mahasiswa]
    P[Petugas Parkir]
    A[Admin Kampus]
    S((Sistem Smart Parking Digital Twin))

    M -->|Permintaan informasi slot| S
    S -->|Denah dan status slot| M

    P -->|Data kendaraan masuk/keluar| S
    S -->|Informasi slot dan hasil pencatatan| P

    A -->|Pengaturan data parkir| S
    S -->|Laporan dan statistik parkir| A
```

## 3. Use Case Diagram

Aktor: Mahasiswa, Petugas Parkir, dan Admin Kampus.

```mermaid
flowchart LR
    M[Mahasiswa]
    P[Petugas Parkir]
    A[Admin Kampus]

    subgraph SYS[Sistem Smart Parking]
        U1([Melihat Denah Parkir])
        U2([Melihat Slot Kosong])
        U3([Mencatat Kendaraan Masuk])
        U4([Mencatat Kendaraan Keluar])
        U5([Mengelola Data Slot])
        U6([Melihat Laporan Parkir])
    end

    M --- U1
    M --- U2
    P --- U3
    P --- U4
    A --- U5
    A --- U6
```

## 4. Sequence Diagram

Use case yang dipilih: **Mencatat Kendaraan Masuk**.

```mermaid
sequenceDiagram
    actor P as Petugas Parkir
    participant S as Sistem Smart Parking
    participant D as Data Slot Parkir

    P->>S: Masukkan jenis kendaraan
    S->>D: Cari slot yang sesuai
    D-->>S: Informasi ketersediaan slot

    alt Slot tersedia
        S->>D: Ubah status slot menjadi terisi
        D-->>S: Status berhasil diperbarui
        S-->>P: Kendaraan berhasil dicatat
    else Slot penuh
        S-->>P: Tidak ada slot tersedia
    end
```

## 5. Class Diagram

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

## 6. State Diagram

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
