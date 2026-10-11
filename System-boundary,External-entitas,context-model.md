graph TB
    subgraph External Entities [Entitas Eksternal]
        A[Mahasiswa]
        B[Petugas Parkir]
        C[Admin Kampus]
    end

    subgraph System Boundary [Smart Parking Digital Twin Kampus]
        D[Tampilkan Denah Parkir]
        E[Pantau Ketersediaan Slot Parkir]
        F[Catat Kendaraan Masuk & Keluar]
        G[Kelola Data Parkir]
    end

    A -->|Melihat denah dan slot| D
    A -->|Melihat status slot| E
    B -->|Mencatat kendaraan| F
    C -->|Mengelola data slot| G
    C -->|Melihat laporan| F

    style System Boundary fill:#fff,stroke:#000,stroke-width:2px
    style External Entities fill:#f9f9f9,stroke:#333,stroke-dasharray: 5 5

    graph LR
    subgraph External Entities
        M[Mahasiswa]
        P[Petugas Parkir]
        AC[Admin Kampus]
    end

    subgraph System [Sistem Smart Parking Digital Twin]
        S((Smart Parking System))
    end

    M -->|Permintaan informasi slot| S
    S -->|Denah dan status slot| M

    P -->|Data kendaraan masuk/keluar| S
    S -->|Informasi slot & hasil pencatatan| P

    AC -->|Pengaturan data parkir| S
    S -->|Laporan dan statistik parkir| AC

    style System fill:#fff,stroke:#000,stroke-width:2px
