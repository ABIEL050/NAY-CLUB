## 1. Use Case Diagram

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

## 2. Sequence Diagram

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
- **Dipublikasikan:** ulasan disetujui dan dapat dilihat pengguna lain.
- **Ditolak:** ulasan tidak disetujui dan perlu diperbaiki sebelum dikirim kembali.
