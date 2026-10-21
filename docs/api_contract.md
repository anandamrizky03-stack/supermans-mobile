# API Contract - SUPERMANS Mobile

Dokumen ini mendefinisikan kontrak RESTful API untuk pengembangan aplikasi SUPERMANS Mobile.

## 1. Authentication Endpoints
### POST /auth/login
*   **Deskripsi:** Autentikasi pengguna dan mendapatkan JWT Token.
*   **Request Body:**
    ```json
    {
      "nim": "198812312023011001",
      "password": "secretpassword"
    }
    ```
*   **Response (200 OK):**
    ```json
    {
      "status": "success",
      "message": "Login berhasil",
      "data": {
        "token": "eyJhbGciOiJIUzI1Ni...",
        "user": { "id": 1, "name": "Dr. Fulan, M.T.", "role": "dosen" }
      }
    }
    ```

### POST /auth/logout
*   **Deskripsi:** Menghapus sesi token pengguna.
*   **Headers:** `Authorization: Bearer <token>`
*   **Response (200 OK):**
    ```json
    { "status": "success", "message": "Logout berhasil", "data": null }
    ```

### GET /auth/profile
*   **Deskripsi:** Mengambil data profil pengguna yang sedang login.
*   **Headers:** `Authorization: Bearer <token>`
*   **Response (200 OK):** *(Detail data user)*

---

## 2. Performance Reports Endpoints (Kinerja)
### GET /performances
*   **Deskripsi:** Mengambil daftar laporan kinerja pengguna.
*   **Query Params:** `page`, `limit`, `category_id`, `status`
*   **Response (200 OK):** *(List data laporan)*

### POST /performances
*   **Deskripsi:** Menambah laporan kinerja baru.
*   **Request Body (Multipart/Form-Data):**
    ```json
    {
      "category_id": 1,
      "title": "Mengajar Mata Kuliah Pemrograman Web",
      "activity_date": "2026-10-01",
      "description": "Melaksanakan perkuliahan pertemuan ke-4.",
      "file_url": " bukti_ajar.pdf"
    }
    ```

### GET /performances/{id}
*   **Deskripsi:** Menampilkan detail laporan kinerja berdasarkan ID.

### PUT /performances/{id}
*   **Deskripsi:** Memperbarui data laporan kinerja yang berstatus 'pending'.
*   **Request Body:** *(Sama seperti POST)*

### DELETE /performances/{id}
*   **Deskripsi:** Menghapus laporan kinerja tertentu.

### GET /performances/summary
*   **Deskripsi:** Mengambil ringkasan statistik poin kinerja dosen/pegawai.

---

## 3. Categories & Master Data Endpoints
### GET /categories
*   **Deskripsi:** Mengambil daftar kategori Tri Dharma / Kinerja.

### GET /categories/{id}
*   **Deskripsi:** Menampilkan detail kategori spesifik.

---

## 4. Evaluations Endpoints (Penilaian)
### GET /evaluations
*   **Deskripsi:** Mengambil daftar evaluasi kinerja yang masuk ke penilai.

### POST /evaluations
*   **Deskripsi:** Memberikan catatan atau skor penilaian oleh asesor/admin.
*   **Request Body:**
    ```json
    {
      "report_id": 12,
      "score": 95,
      "notes": "Dokumen lengkap dan valid.",
      "status": "approved"
    }
    ```

### GET /evaluations/{id}
*   **Deskripsi:** Melihat detail hasil evaluasi laporan.

### PUT /evaluations/{id}
*   **Deskripsi:** Memperbarui status evaluasi kinerja.

---

## 5. Error Handling & Status Codes
*   `400 Bad Request`: Format input atau parameter tidak valid.
*   `401 Unauthorized`: Token JWT tidak valid atau sudah kedaluwarsa.
*   `403 Forbidden`: Pengguna tidak memiliki hak akses (*role*) ke endpoint tersebut.
*   `404 Not Found`: Data yang dicari tidak ditemukan di database.
*   `500 Internal Server Error`: Terjadi kendala pada server / database.

---

## 6. Changelog
*   **v1.0.0 (02 Oktober 2026):** Inisialisasi awal 15 endpoint RESTful untuk SUPERMANS Mobile.
