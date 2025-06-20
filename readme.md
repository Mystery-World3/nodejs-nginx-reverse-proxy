# Proyek Web Server dengan Node.js & NGINX

Repositori ini berisi seluruh file proyek untuk submission kelas "Belajar Jaringan Komputer Untuk Pemula" di Dicoding. Proyek ini berfokus pada pembangunan web server yang fungsional dan aman menggunakan Node.js, dengan NGINX yang berperan sebagai Reverse Proxy dan Rate Limiter.

---

## Deskripsi Proyek

Tujuan utama dari proyek ini adalah untuk mempraktikkan konsep-konsep kunci dalam administrasi jaringan dan server. Proyek ini mendemonstrasikan bagaimana sebuah server aplikasi (dibangun dengan Node.js) dapat dipublikasikan secara aman dengan meletakkannya di belakang NGINX. NGINX bertugas menerima semua trafik dari luar dan meneruskannya ke server aplikasi, sehingga arsitektur internal tetap tersembunyi.

Selain itu, proyek ini juga mengimplementasikan fitur keamanan penting yaitu **Rate Limiting** untuk membatasi jumlah permintaan yang dapat diterima dalam rentang waktu tertentu, guna mencegah serangan dasar seperti brute-force atau DoS (Denial-of-Service).

---

## Teknologi yang Digunakan

-   **Node.js:** Platform untuk membangun sisi server aplikasi.
-   **Express.js:** Kerangka kerja (framework) minimalis untuk Node.js yang mempermudah pembuatan web server dan API.
-   **NGINX:** Perangkat lunak server berperforma tinggi yang digunakan sebagai Reverse Proxy dan Web Server.
-   **Git & GitHub:** Sistem kontrol versi untuk manajemen kode dan hosting repositori.

---

## Isi Repositori

Repositori ini memiliki struktur folder sebagai berikut:

-   `/aplikasi_nodejs/`
    -   Berisi seluruh kode sumber untuk server aplikasi. File utamanya adalah `app.js`, yang mendefinisikan dua endpoint:
        -   `/` : Mengembalikan respons "Hello world!".
        -   `/me` : Mengembalikan username Dicoding sebagai pemenuhan kriteria nilai tinggi.

-   `/konfigurasi_nginx/`
    -   Berisi file `nginx.conf` yang telah dimodifikasi. Konfigurasi ini mencakup:
        -   Pengaturan Reverse Proxy untuk meneruskan trafik dari port `3000` ke port `8000`.
        -   Implementasi Rate Limiting sebanyak 6 permintaan per menit.

---

## Cara Menjalankan

Untuk menjalankan proyek ini secara lokal, ikuti langkah-langkah berikut:

1.  **Clone Repositori:**
    *(Ganti `NAMA_USERNAME_ANDA` dan `NAMA_REPO_ANDA` dengan milik Anda)*
    ```bash
    git clone [https://github.com/NAMA_USERNAME_ANDA/NAMA_REPO_ANDA.git](https://github.com/NAMA_USERNAME_ANDA/NAMA_REPO_ANDA.git)
    cd NAMA_REPO_ANDA
    ```

2.  **Siapkan Prasyarat:**
    -   Pastikan Anda sudah menginstal **Node.js** dan **NGINX** di komputer Anda.

3.  **Instal Dependensi Aplikasi:**
    -   Buka terminal, masuk ke folder `aplikasi_nodejs`, dan jalankan perintah:
        ```bash
        cd aplikasi_nodejs
        npm install
        ```

4.  **Terapkan Konfigurasi NGINX:**
    -   Salin file `nginx.conf` dari folder `/konfigurasi_nginx/`.
    -   Gunakan file tersebut untuk menggantikan file konfigurasi NGINX default di sistem Anda (misalnya di `C:\nginx\conf\nginx.conf` pada Windows atau `/etc/nginx/nginx.conf` pada Linux).

5.  **Jalankan Semua Server:**
    -   **Jalankan NGINX:** Buka terminal baru, masuk ke direktori instalasi NGINX, dan jalankan perintah yang sesuai.
        ```bash
        # Contoh untuk Windows
        cd C:\nginx
        start nginx.exe
        
        # Reload konfigurasi jika NGINX sudah berjalan
        nginx.exe -s reload 
        ```
    -   **Jalankan Server Node.js:** Kembali ke terminal di folder `aplikasi_nodejs` dan jalankan:
        ```bash
        node app.js
        ```
        Server akan berjalan di `http://localhost:8000`.

6.  **Lakukan Pengujian:**
    -   Buka browser dan akses **`http://localhost:3000`**. 
    -   Anda akan melihat respons dari server Node.js yang telah diteruskan oleh NGINX dari port `8000`. Coba juga akses endpoint `/me`.
