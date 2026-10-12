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
- **Dipublikasikan:** ulasan disetujui dan dapat dilihat pengguna lain.
- **Ditolak:** ulasan tidak disetujui dan perlu diperbaiki sebelum dikirim kembali.
