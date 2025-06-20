Proyek Web Server dengan Node.js dan NGINXRepositori ini berisi proyek akhir untuk kelas "Belajar Jaringan Komputer Untuk Pemula" di Dicoding. Proyek ini mendemonstrasikan implementasi web server Node.js yang aman dan efisien dengan menggunakan NGINX sebagai Reverse Proxy dan Rate Limiter.Fitur UtamaWeb Server Sederhana: Dibangun menggunakan Node.js dan framework Express.js.Reverse Proxy: Menggunakan NGINX untuk meneruskan permintaan dari port publik (3000) ke server aplikasi Node.js (8000), menyembunyikan arsitektur internal.Rate Limiting: Menerapkan batas permintaan (6 permintaan per menit) di level NGINX untuk melindungi server dari serangan brute-force atau Denial-of-Service (DoS).Endpoint Kustom: Menambahkan endpoint /me yang mengembalikan username sebagai bagian dari pemenuhan kriteria nilai tinggi.Struktur ProyekBerikut adalah struktur folder dalam repositori ini:.
├── aplikasi_nodejs/        # Berisi semua file terkait server Node.js
│   ├── app.js              # File utama server Express.js
│   ├── package.json        # Dependensi proyek Node.js
│   └── ...
│
├── konfigurasi_nginx/      # Berisi file konfigurasi NGINX
│   └── nginx.conf          # Konfigurasi untuk reverse proxy dan rate limiting
│
└── README.md               # File yang sedang Anda baca
Cara Menjalankan Proyek Secara LokalUntuk menjalankan proyek ini di mesin lokal Anda, ikuti langkah-langkah berikut.1. PrasyaratNode.js (v14.15.4 atau lebih tinggi)NGINXGit2. Instalasia. Clone repositori ini:Ganti NAMA_USERNAME_ANDA dan NAMA_REPO_ANDA dengan milik Anda.git clone [https://github.com/NAMA_USERNAME_ANDA/NAMA_REPO_ANDA.git](https://github.com/NAMA_USERNAME_ANDA/NAMA_REPO_ANDA.git)
cd NAMA_REPO_ANDA
b. Siapkan server Node.js:# Masuk ke folder aplikasi
cd aplikasi_nodejs

# Instal semua dependensi yang dibutuhkan
npm install
c. Konfigurasi NGINX:Salin file nginx.conf dari folder konfigurasi_nginx di proyek ini.Tempel dan ganti file nginx.conf yang ada di instalasi NGINX Anda (biasanya di C:\nginx\conf\nginx.conf untuk Windows atau /etc/nginx/ untuk Linux).3. Menjalankan Aplikasia. Jalankan server NGINX:Buka terminal/CMD baru, masuk ke direktori instalasi NGINX Anda.Jalankan NGINX.# Contoh untuk Windows
cd C:\nginx
start nginx.exe

# Muat ulang konfigurasi jika NGINX sudah berjalan
nginx.exe -s reload
b. Jalankan server Node.js:Kembali ke terminal pertama di direktori aplikasi_nodejs.Jalankan server.node app.js
Server akan berjalan di http://localhost:8000.4. PengujianBuka browser Anda dan akses alamat berikut:http://localhost:3000Ini akan mengakses NGINX, yang kemudian meneruskannya ke server Node.js. Anda akan melihat "Hello world!".http://localhost:3000/meAnda akan melihat username Dicoding Anda.Uji Rate Limit:Refresh halaman http://localhost:3000 berkali-kali dengan cepat. Setelah beberapa kali, Anda akan mendapatkan error 503 Service Temporarily Unavailable.
