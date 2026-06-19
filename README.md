# 📦 E-Inventory — Sistem Manajemen Inventaris Barang

**UAS Pemrograman Web 2**
**Nama:** Wahyu Andika
**NIM:** 312410182

Aplikasi web berbasis **Decoupled Architecture** untuk mengelola data barang, kategori, supplier, dan histori stok masuk/keluar secara real-time.

---

## 🛠️ Teknologi yang Digunakan

| Layer | Teknologi |
|---|---|
| Backend | CodeIgniter 4.7.0 (REST API) |
| Frontend | Vue.js 3 (SPA via CDN) |
| UI Framework | TailwindCSS (CDN) |
| HTTP Client | Axios |
| Database | MySQL / MariaDB |
| Auth | Bearer Token (CI4 Filter) |

---

## 📁 Struktur Folder

```
UAS_WEB2/
├── ci4/                        # Backend CodeIgniter 4
│   └── app/
│       ├── Controllers/
│       │   ├── AuthController.php
│       │   ├── BarangController.php
│       │   ├── KategoriController.php
│       │   ├── SupplierController.php
│       │   ├── HistoriController.php
│       │   └── DashboardController.php
│       ├── Models/
│       │   ├── UserModel.php
│       │   ├── BarangModel.php
│       │   ├── KategoriModel.php
│       │   ├── SupplierModel.php
│       │   └── HistoriModel.php
│       ├── Filters/
│       │   ├── AuthFilter.php
│       │   └── CorsFilter.php
│       └── Config/
│           ├── Filters.php
│           └── Routes.php
└── frontend-spa/               # Frontend Vue 3 SPA
    ├── index.html
    └── components/
        ├── Home.js
        ├── Login.js
        ├── Dashboard.js
        ├── Barang.js
        ├── Kategori.js
        ├── Supplier.js
        └── Histori.js
```

---

## 🗃️ Skema Relasi Database

<img width="940" height="499" alt="image" src="https://github.com/user-attachments/assets/ad3ca026-3a3a-43a0-869c-b4ca8fb0e3a4" />

**Tabel:**
- `users` — data akun admin
- `kategori` — kategori barang
- `supplier` — data supplier
- `barang` — data barang (FK → kategori, supplier)
- `histori_stok` — log stok masuk/keluar (FK → barang)

---

## 🔐 Uji Coba Proteksi Token (401 Unauthorized)

> **GET** `/api/barang` tanpa Authorization Header → ditolak server dengan status **401 Unauthorized**

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/c296ff00-aef0-47e7-bfd8-c0ad066493e6" />

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/4212d2b9-613f-406a-9f6a-7411a106022f" />

---

## 🖥️ Screenshot Antarmuka

### Landing Page (Public)

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/3d71ec6a-53bf-492c-9599-83f6f66a3432" />

### Halaman Login

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/e8d00f40-7378-40f8-b364-9ab9ff94823d" />

### Dashboard Admin

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/0420a367-ac28-4afa-b173-b02cbc3b52ea" />

### Halaman Barang

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/64341060-916d-464f-bedf-17b9f1e31a3e" />

### Modal Tambah / Edit Data

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/1d0a4015-47af-4d0f-8143-204c3e759e76" />

### Halaman Histori Stok

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/1c6c4346-7334-4166-811e-ee06b84b65a8" />

---

## 🔗 API Endpoints

| Method | Endpoint | Auth | Keterangan |
|---|---|---|---|
| POST | `/api/login` | ❌ | Login admin |
| POST | `/api/logout` | ✅ | Logout |
| GET | `/api/summary` | ❌ | Total data (public) |
| GET/POST | `/api/barang` | ✅ | CRUD Barang |
| GET/POST | `/api/kategori` | ✅ | CRUD Kategori |
| GET/POST | `/api/supplier` | ✅ | CRUD Supplier |
| GET/POST | `/api/histori` | ✅ | CRUD Histori |

---

## ⚙️ Cara Menjalankan Proyek

### Prasyarat
- XAMPP (PHP 8.1+, MySQL)
- Browser modern

### Backend (CI4)

1. Clone/copy folder `ci4/` ke `htdocs/UAS_WEB2/ci4/`
2. Rename file `env` → `.env`, lalu edit:
```env
CI_ENVIRONMENT = development
database.default.hostname = localhost
database.default.database = db_inventory
database.default.username = root
database.default.password =
database.default.DBDriver = MySQLi
```
3. Import file SQL ke phpMyAdmin (database: `db_inventory`)
4. Akses backend: `http://localhost/UAS_WEB2/ci4/public/`

### Frontend (Vue 3 SPA)

1. Copy folder `frontend-spa/` ke `htdocs/UAS_WEB2/frontend-spa/`
2. Akses frontend: `http://localhost/UAS_WEB2/frontend-spa/`
3. Login dengan:
   - Username: `admin`
   - Password: `admin123`

---

## 🎯 Fitur Aplikasi

### Public (Tanpa Login)
- Landing page dengan ringkasan total data real-time

### Admin (Wajib Login)
- CRUD Barang (dengan relasi kategori & supplier)
- CRUD Kategori
- CRUD Supplier
- Histori stok masuk/keluar (auto-update stok barang)
- Dashboard statistik
- Logout

---

## 🔒 Fitur Keamanan

- **Bearer Token** — setiap request POST/PUT/DELETE wajib menyertakan token
- **Navigation Guard** — halaman admin redirect ke login jika belum autentikasi
- **Axios Interceptor** — auto-inject token + handle 401 global
- **CORS Filter** — konfigurasi global untuk request lintas origin

---

## 🎬 Demo & Presentasi

| | Link |
|---|---|
| 🎥 Video Presentasi | [Tonton di YouTube](#) |

---

## 👤 Author

**Wahyu Andika** — 312410182
Teknik Informatika — Universitas Pelita Bangsa
