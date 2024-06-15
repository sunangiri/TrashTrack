## Dokumentasi Instalasi dan Konfigurasi Aplikasi Trashtrack

### Daftar Isi

- [Penjelasan](#penjelasan)
- [Persyaratan Sistem](#persyaratan-sistem)
- [Instalasi](#instalasi)
  - [Langkah 1: Clone Repository](#langkah-1-clone-repository)
  - [Langkah 2: Instal Dependensi](#langkah-2-instal-dependensi)
  - [Langkah 3: Konfigurasi Environment](#langkah-3-konfigurasi-environment)
  - [Langkah 4: Jalankan Server](#langkah-4-jalankan-server)
- [API Endpoints](#api-endpoints)
  - [/api/register](#apiregister)
  - [/api/login](#apilogin)
  - [/api/reportTrash](#apireporttrash)
  - [/api/reports](#apireports)

---

## Penjelasan

Aplikasi Trashtrack adalah platform untuk melaporkan dan melacak sampah di berbagai lokasi. Pengguna dapat mendaftarkan diri, login, dan membuat laporan sampah dengan mengunggah gambar serta detail lokasi dan jenis sampah. Laporan ini kemudian dapat diakses oleh semua pengguna terdaftar.

## Persyaratan Sistem

Pastikan sistem Anda memenuhi persyaratan berikut:
- Node.js (versi terbaru)
- npm (Node Package Manager)
- Git

## Instalasi

### Langkah 1: Clone Repository

Pertama, clone repository aplikasi Trashtrack dari GitHub.

```bash
git clone https://github.com/sunangiri/trashtrack.git
cd trashtrack
```

### Langkah 2: Instal Dependensi

Setelah masuk ke direktori proyek, instal semua dependensi yang diperlukan.

```bash
npm install
```

### Langkah 3: Konfigurasi Environment

Buat file `.env` di direktori root proyek Anda dan tambahkan variabel lingkungan yang diperlukan. Contoh isi file `.env`:

```
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASS=password
DB_NAME=trashtrack
JWT_SECRET=your_secret_key
```

### Langkah 4: Jalankan Server

Setelah instalasi dependensi dan konfigurasi environment, jalankan server aplikasi.

```bash
node server.js
```

Server akan berjalan di `http://localhost:3000`.

---

## API Endpoints

### `/api/register`

**Endpoint ini digunakan untuk mendaftarkan pengguna baru.**

**Request:**
```bash
curl -X POST \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "username=farid&password=123" \
http://localhost:3000/api/register
```

**Response:**
```json
{
  "status": true,
  "message": "User registered successfully"
}
```

---

### `/api/login`

**Endpoint ini digunakan untuk login pengguna.**

**Request:**
```bash
curl -X POST \
-H "Content-Type: application/json" \
-d '{"username":"farid","password":"123"}' \
http://localhost:3000/api/login
```

**Response:**
```json
{
  "status": true,
  "user": {
    "id": 2,
    "username": "farid",
    "password": "123"
  }
}
```

---

### `/api/reportTrash`

**Endpoint ini digunakan untuk melaporkan sampah.**

**Request:**
```bash
curl -X POST \
-F "username=yulfi" \
-F "location=ngumpak" \
-F "type=plastik" \
-F "image=@bah.png" \
http://localhost:3000/api/reportTrash
```

**Response:**
```json
{
  "status": true,
  "message": "Report submitted successfully"
}
```

---

### `/api/reports`

**Endpoint ini digunakan untuk mendapatkan laporan sampah.**

**Request:**
```bash
curl -X GET \
http://localhost:3000/api/reports
```

**Response:**
```json
{
  "status": true,
  "reports": [
    {
      "id": 3,
      "username": "yulfi",
      "location": "ngumpak",
      "type": "plastik",
      "image": "1718200965110-bah.png",
      "created_at": "2024-06-12T14:02:45.000Z"
    },
    {
      "id": 2,
      "username": "yulfi",
      "location": "ngumpak",
      "type": "plastik",
      "image": "1718200775600-bah.png",
      "created_at": "2024-06-12T13:59:35.000Z"
    }
  ]
}
```

---
