# 🚀 Laravel x SvelteKit Headless Web App

Website ini dibangun menggunakan arsitektur **Headless/Decoupled**, di mana backend dan frontend dipisah secara penuh dalam direktori yang berbeda. Pendekatan ini memberikan fleksibilitas tinggi, performa maksimal, dan kemudahan saat tahap *deployment*.

## 🛠️ Tech Stack

### Backend (API)
*   **Framework:** Laravel (PHP)
*   **Fungsi:** Menangani logika bisnis, manajemen database, autentikasi, dan menyediakan RESTful API.
*   **Local Server:** Laragon

### Frontend (UI/UX)
*   **Framework:** SvelteKit (JavaScript/Svelte)
*   **Fungsi:** Mengkonsumsi API dari Laravel, menangani *routing* sisi klien, dan menampilkan antarmuka yang interaktif.
*   **Styling:** Tailwind CSS
*   **Animasi:** GSAP (GreenSock Animation Platform)

---

## 📁 Struktur Direktori

```text
/
├── backend/    # Berisi full source code Laravel
└── frontend/   # Berisi full source code SvelteKit
```

---

## ⚙️ Panduan Instalasi & Menjalankan (Local Development)

Pastikan kamu sudah menginstal **PHP, Composer, Node.js**, dan menggunakan **Laragon** untuk mempermudah konfigurasi database dan virtual host.

### 1. Menjalankan Backend (Laravel)

1. Buka terminal dan arahkan ke direktori backend:
   ```bash
   cd backend
   ```
2. Salin konfigurasi environment:
   ```bash
   cp .env.example .env
   ```
3. Sesuaikan konfigurasi database di file `.env` sesuai dengan MySQL di Laragon.
4. Install *dependencies* PHP dan *generate key*:
   ```bash
   composer install
   php artisan key:generate
   ```
5. (Opsional) Jalankan migrasi database:
   ```bash
   php artisan migrate
   ```
6. **Akses API:**
   Jika menggunakan Laragon *Auto Virtual Hosts*, API langsung tersedia di domain lokal (contoh: `http://namaproject.test`). 
   Atau jalankan server manual dengan:
   ```bash
   php artisan serve
   ```
   *(Backend berjalan di `http://127.0.0.1:8000`)*

### 2. Menjalankan Frontend (SvelteKit)

1. Buka terminal baru (biarkan terminal backend tetap berjalan) dan arahkan ke direktori frontend:
   ```bash
   cd frontend
   ```
2. Install *dependencies* Node.js:
   ```bash
   npm install
   ```
3. Pastikan URL API Laravel (*endpoint*) sudah diatur dengan benar saat melakukan `fetch` data (misalnya mengarah ke domain `.test` Laragon atau `localhost:8000`).
4. Jalankan server *development*:
   ```bash
   npm run dev
   ```
5. Buka `http://localhost:5173` di browser.

---

## 🚀 Persiapan Deployment

Aplikasi ini menggunakan arsitektur terpisah, sehingga proses deployment dilakukan di dua *environment* berbeda:
*   **Frontend (SvelteKit):** Direkomendasikan deploy ke *static/serverless platform* seperti **Vercel** atau **Netlify**.
*   **Backend (Laravel):** Direkomendasikan deploy ke **VPS (Ubuntu Server)** atau **Shared Hosting**, kemudian hubungkan koneksi API-nya melalui konfigurasi `.env` di frontend dan buka akses origin Vercel di setelan CORS Laravel.

---

## 🧑‍💻 Author
**Seandjs**