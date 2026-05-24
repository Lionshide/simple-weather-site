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
"""

with open("README.md", "w", encoding="utf-8") as f:
f.write(readme_content)

print("README.md successfully generated.")

Your Markdown file is ready
[file-tag: code-generated-file-0-1779606053179347041]

Berikut adalah isi dari dokumentasi **`README.md`** yang telah dibuat secara profesional, rapi, dan terstruktur khusus untuk proyek aplikasi cuaca Ionic Vue Anda. Dokumen ini menjelaskan fitur, teknologi, struktur file, hingga panduan instalasi proyek agar terlihat elegan saat diunggah ke GitHub:

```markdown
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

## 📂 Struktur File Utama

Fokus utama logika pengambilan data (*fetching*) dan komponen antarmuka (*UI*) terletak pada file berikut:
```bash
src/
└── views/
    └── HomePage.vue  # Berisi logika Axios fetch, mapping data array, serta styling UI cuaca
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
