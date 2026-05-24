# 🌤️ Simple Weather Site (Jakarta)

Aplikasi web/mobile berbasis **Ionic Vue** dan **TypeScript** yang menampilkan data prakiraan cuaca per jam untuk wilayah Jakarta secara real-time. Aplikasi ini dirancang dengan pendekatan UI/UX yang **minimalis namun tetap elegan**, mengutamakan kemudahan membaca informasi secara cepat dan instan.

Data cuaca dikonsumsi langsung dari layanan online **Open-Meteo API**.

---

## ✨ Fitur Utama

* **Integrasi Open-Meteo API:** Mengambil data prakiraan suhu per jam secara real-time untuk koordinat Jakarta.
* **Desain Minimalis & Elegan:** Menggunakan komponen modern dari Ionic Framework dengan sudut melengkung halus (*rounded borders*) serta bayangan tipis (*subtle shadow*) untuk memisahkan baris data secara bersih.
* **Format Waktu Lokal:** Mengonversi data waktu mentah ISO standar dari API menjadi format lokal Indonesia yang familiar (contoh: `24 Mei, 14:00`).
* **State Handling:** Memiliki indikator visual yang intuitif saat data sedang dimuat (*Loading Spinner*) maupun ketika koneksi gagal (*Error Handling*).
* **Responsif:** Tampilan yang adaptif dan rapi saat dibuka melalui perangkat mobile (smartphone) maupun browser desktop.

## 🚀 Teknologi yang Digunakan

* **Framework:** [Vue 3 (Composition API)](https://vuejs.org/) & [Ionic Framework](https://ionicframework.com/)
* **Bahasa:** [TypeScript](https://www.typescriptlang.org/)
* **HTTP Client:** [Axios](https://axios-http.com/)
* **Build Tool:** [Vite](https://vitejs.dev/)

🛠️ Cara Menjalankan Proyek di Lokal
Pastikan Anda sudah menginstal Node.js di perangkat Anda.

1. Clone Repositori
Bash
git clone [https://github.com/username/simple-weather-site.git](https://github.com/username/simple-weather-site.git)
cd simple-weather-site
2. Instal Dependensi
Instal semua pustaka yang diperlukan (termasuk Axios dan Ionic Core):

Bash
npm install
3. Jalankan Server Pengembangan
Jalankan perintah berikut untuk membuka jalannya aplikasi di browser:

Bash
npm run dev
# atau jika Anda menggunakan Ionic CLI:
# ionic serve
Secara default, aplikasi akan berjalan di alamat http://localhost:5173/.

🌐 Endpoint API yang Digunakan
Aplikasi ini melakukan HTTP GET request ke alamat Open-Meteo berikut untuk mendapatkan data koordinat Jakarta:

Plaintext
[https://api.open-meteo.com/v1/forecast?latitude=-6.2&longitude=106.8&hourly=temperature_2m](https://api.open-meteo.com/v1/forecast?latitude=-6.2&longitude=106.8&hourly=temperature_2m)
Data atribut yang ditampilkan dari API meliputi:

time (Waktu pengukuran prakiraan)

temperature_2m (Suhu per jam dalam satuan °C)

📄 Lisensi
Proyek ini dibuat untuk keperluan demonstrasi/tugas pengembangan web dan bebas digunakan ataupun dikembangkan kembali.


### Poin Utama yang Dicakup dalam README ini:
1. **Penjelasan Konsep**: Memberi tahu pengunjung repositori bahwa aplikasi menggunakan desain *minimalist-elegant* sesuai permintaan Anda.
2. **Keterbacaan Struktur**: Menyertakan pemetaan atribut data penting (`time` dan `temperature_2m`) agar sesuai dengan ketentuan pengerjaan tugas proyek.
3. **Langkah Memulai (*Getting Started*)**: Panduan instalasi yang jelas (`npm install` dan `npm run dev`) sehingga orang lain atau dosen penguji dapat menjalankan kodingan Anda dengan mudah di komputer mereka.

## 📂 Struktur File Utama

Fokus utama logika pengambilan data (*fetching*) dan komponen antarmuka (*UI*) terletak pada file berikut:
```bash
simple-weather-site/
├── .vscode/
│   └── extensions.json          # Rekomendasi ekstensi VS Code untuk tim
├── public/
│   └── favicon.png              # Icon aplikasi yang muncul di tab browser
├── src/                         # Folder utama kode sumber aplikasi
│   ├── router/
│   │   └── index.ts             # Pengaturan rute halaman (routing) Ionic Vue
│   ├── theme/
│   │   └── variables.css        # Pengaturan warna global dan tema aplikasi
│   ├── views/
│   │   └── HomePage.vue         # Halaman utama (logika API cuaca & tampilan minimalis)
│   ├── App.vue                  # Komponen akar (root component) Vue
│   ├── main.ts                  # Entry point utama aplikasi untuk inisialisasi Ionic
│   └── vite-env.d.ts            # Deklarasi tipe data lingkungan untuk Vite
├── tests/                       # Folder pengujian kode (testing)
│   ├── e2e/                     # End-to-End testing menggunakan Cypress
│   │   ├── fixtures/
│   │   │   └── example.json
│   │   ├── specs/
│   │   │   └── test.cy.ts
│   │   └── support/
│   │       ├── commands.ts
│   │       └── e2e.ts
│   └── unit/                    # Unit testing untuk komponen terkecil
│       └── example.spec.ts
├── .browserslistrc              # Konfigurasi target kompatibilitas browser
├── .eslintignore                # Daftar file/folder yang diabaikan oleh linter
├── .eslintrc.cjs                # Konfigurasi aturan kualitas kode (ESLint)
├── .gitignore                   # Daftar file yang diabaikan oleh Git (seperti node_modules)
├── README.md                    # Dokumentasi utama proyek Anda
├── capacitor.config.ts          # Konfigurasi Capacitor untuk build ke Android/iOS
├── cypress.config.ts            # Konfigurasi untuk framework testing Cypress
├── index.html                   # File HTML utama tempat aplikasi Vue di-mount
├── ionic.config.json            # Konfigurasi proyek spesifik Ionic Framework
├── package-lock.json            # Catatan versi detail dari dependensi yang terinstal
├── package.json                 # Daftar dependensi pustaka (Axios, Ionic, Vue) dan script proyek
├── tsconfig.json                # Konfigurasi utama compiler TypeScript
├── tsconfig.node.json           # Konfigurasi TypeScript khusus untuk file node/vite
└── vite.config.ts               # Konfigurasi server dan bundler menggunakan Vite
