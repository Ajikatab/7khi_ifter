# 📖 Tutorial Menjalankan Website 7KHI di Komputer Lokal

## Untuk Pemula (Step-by-Step dengan Gambar)

Tutorial ini akan memandu Anda langkah demi langkah untuk menjalankan website **7KHI (7 Kebiasaan Harian Islami)** di komputer Anda sendiri. Tidak perlu koneksi internet untuk mengakses website setelah di-install!

> 💡 **Apa itu localhost?**
> 
> Localhost adalah cara menjalankan website di komputer sendiri tanpa perlu upload ke internet. Website hanya bisa diakses dari komputer Anda saja.

---

# 🚀 LANGKAH-LANGKAH INSTALASI

## TAHAP 1: Install Software yang Dibutuhkan

Sebelum memulai, Anda perlu menginstall beberapa software. Ikuti langkah berikut:

---

### 1️⃣ Install XAMPP (Server Lokal)

XAMPP adalah software yang berisi Apache (web server), MySQL (database), dan PHP sekaligus.

**Cara Install:**

1. Buka browser (Chrome/Firefox/Edge)
2. Ketik di address bar: **https://www.apachefriends.org/**
3. Klik tombol **"Download"** (pilih versi Windows)
4. Tunggu sampai download selesai
5. Buka file yang sudah di-download (biasanya di folder **Downloads**)
6. Klik **Next** terus sampai selesai (gunakan pengaturan default)
7. Setelah selesai, klik **Finish**

✅ **XAMPP sudah terinstall!**

---

### 2️⃣ Install Composer (Package Manager PHP)

Composer adalah alat untuk mendownload library PHP yang dibutuhkan website.

**Cara Install:**

1. Buka browser
2. Ketik: **https://getcomposer.org/download/**
3. Scroll ke bawah, cari bagian **"Windows Installer"**
4. Klik **"Composer-Setup.exe"** untuk download
5. Buka file yang sudah di-download
6. Klik **Next** terus sampai selesai
7. Jika ada pilihan PHP, pilih: `C:\xampp\php\php.exe`

✅ **Composer sudah terinstall!**

---

### 3️⃣ Install Node.js (JavaScript Runtime)

Node.js dibutuhkan untuk menjalankan bagian tampilan website.

**Cara Install:**

1. Buka browser
2. Ketik: **https://nodejs.org/**
3. Klik tombol **LTS** (yang berwarna hijau, versi stabil)
4. Tunggu download selesai
5. Buka file installer yang sudah di-download
6. Klik **Next** terus sampai selesai

✅ **Node.js sudah terinstall!**

---

### ✅ Verifikasi Semua Software Terinstall

Untuk memastikan semua sudah terinstall dengan benar:

1. **Buka Command Prompt (CMD)**
   - Tekan tombol **Windows** di keyboard
   - Ketik: **cmd**
   - Klik **Command Prompt**

2. **Ketik perintah berikut satu per satu** (tekan Enter setelah setiap perintah):

```
php --version
```
Jika berhasil, akan muncul: `PHP 8.x.x...`

```
composer --version
```
Jika berhasil, akan muncul: `Composer version 2.x.x...`

```
node --version
```
Jika berhasil, akan muncul: `v18.x.x` atau lebih tinggi

```
npm --version
```
Jika berhasil, akan muncul: `9.x.x` atau lebih tinggi

> ⚠️ **Jika ada yang tidak muncul versinya**, coba restart komputer dulu, lalu cek lagi.

---

## TAHAP 2: Menyiapkan Database

### 1️⃣ Jalankan XAMPP

1. Klik tombol **Windows**
2. Ketik: **XAMPP**
3. Klik **XAMPP Control Panel**
4. Akan muncul jendela XAMPP

### 2️⃣ Aktifkan Apache dan MySQL

Pada jendela XAMPP Control Panel:

1. Cari baris **Apache** → Klik tombol **Start**
2. Cari baris **MySQL** → Klik tombol **Start**

Jika berhasil, akan muncul warna **HIJAU** pada kolom PID(s) dan Port(s).

> ⚠️ **Jika muncul error port 80 sudah digunakan:**
> Biasanya karena Skype atau program lain menggunakan port yang sama. Matikan Skype terlebih dahulu.

### 3️⃣ Buat Database

1. Buka browser
2. Ketik di address bar: **http://localhost/phpmyadmin**
3. Tekan Enter
4. Akan terbuka halaman phpMyAdmin (tampilan warna biru/abu-abu)
5. Di panel kiri, klik **"New"** atau **"Baru"**
6. Pada kolom **"Database name"** atau **"Nama database"**, ketik: **7khi_jurnal**
7. Pada dropdown di sebelahnya, pilih: **utf8mb4_unicode_ci**
8. Klik tombol **Create** atau **Buat**

✅ **Database sudah dibuat!**

---

## TAHAP 3: Menyiapkan Project

### 1️⃣ Buka Folder Project

Buka **File Explorer** dan masuk ke folder project 7KHI:
```
D:\Aji Katab\KULIAH\SEMESTER 7\INFORMATIKA TERAPAN\PROYEK\7khi_ifter
```

(Sesuaikan dengan lokasi folder project Anda)

### 2️⃣ Buka Terminal di Folder Project

**Cara Cepat:**
1. Buka folder project di File Explorer
2. Klik pada **address bar** di atas (yang menunjukkan path folder)
3. Ketik: **cmd**
4. Tekan **Enter**

Akan muncul jendela Command Prompt dengan path folder project.

### 3️⃣ Copy File Environment

Ketik perintah ini di Command Prompt, lalu tekan Enter:

```
copy .env.example .env
```

Jika berhasil, akan muncul: `1 file(s) copied.`

### 4️⃣ Edit File .env

1. Buka folder project di File Explorer
2. Cari file bernama **.env** (mungkin hidden, jika tidak terlihat lihat bagian troubleshooting)
3. Klik kanan pada file → **Open with** → **Notepad**
4. Cari bagian ini:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=7khi_jurnal
DB_USERNAME=root
DB_PASSWORD=
```

5. **Pastikan** `DB_DATABASE=7khi_jurnal` (nama database yang tadi dibuat)
6. **Pastikan** `DB_PASSWORD=` kosong (jika menggunakan XAMPP default)
7. Tekan **Ctrl + S** untuk menyimpan
8. Tutup Notepad

---

## TAHAP 4: Install Dependencies

Masih di Command Prompt yang sama (pastikan path-nya di folder project), ketik perintah berikut **SATU PER SATU** dan tunggu sampai selesai:

### 1️⃣ Install PHP Libraries

```
composer install
```

⏳ **Tunggu** sampai proses selesai (bisa 2-5 menit tergantung koneksi internet)

Abaikan warning berwarna kuning, yang penting tidak ada error berwarna merah.

### 2️⃣ Generate Application Key

```
php artisan key:generate
```

Jika berhasil, akan muncul: `Application key set successfully.`

### 3️⃣ Install JavaScript Libraries

```
npm install
```

⏳ **Tunggu** sampai proses selesai (bisa 3-10 menit tergantung koneksi internet)

### 4️⃣ Buat Tabel Database

```
php artisan migrate
```

Jika muncul pertanyaan: `Would you like to create it?`
Ketik: **yes** lalu tekan Enter

⏳ Tunggu sampai muncul daftar tabel yang dibuat.

### 5️⃣ Isi Data Contoh (Opsional tapi Direkomendasikan)

```
php artisan db:seed
```

Perintah ini akan membuat akun admin, guru, siswa, dan data contoh lainnya.

✅ **Semua dependencies sudah terinstall!**

---

## TAHAP 5: Menjalankan Website

### 🚀 Jalankan dengan SATU Perintah

Di Command Prompt, ketik:

```
composer run dev
```

Tekan Enter dan **BIARKAN** jendela ini TETAP TERBUKA!

Jika berhasil, akan muncul tampilan seperti ini:
```
[server] Laravel development server started: http://127.0.0.1:8000
[vite] VITE v7.x.x ready in xxx ms
[queue] ...processing...
```

> ⚠️ **PENTING:** 
> - JANGAN tutup jendela Command Prompt ini!
> - Biarkan tetap terbuka selama menggunakan website

---

## TAHAP 6: Buka Website

### 🌐 Akses Website

1. Buka browser (Chrome/Firefox/Edge)
2. Ketik di address bar: **http://localhost:8000**
3. Tekan Enter

🎉 **Selamat! Website 7KHI sudah berjalan!**

---

## 👤 Cara Login

### Akun yang Tersedia (setelah menjalankan `db:seed`):

| Tipe Akun | Username | Password |
|-----------|----------|----------|
| **Admin** | admin | password |
| **Guru** | gurutest | password |
| **Orangtua** | orangtuatest | password |
| **Siswa Muslim** | siswamuslim | password |
| **Siswa Kristen** | siswakristen | password |
| **Siswa Katolik** | siswakatoli | password |
| **Siswa Hindu** | siswahindu | password |
| **Siswa Buddha** | siswabuddha | password |
| **Siswa Konghucu** | siswakonghucu | password |

**Cara Login:**
1. Di halaman login, masukkan **Username** (bukan email!)
2. Masukkan **Password**: `password`
3. Klik tombol **Login**

---

## 🛑 Cara Mematikan Website

Jika sudah selesai menggunakan website:

1. Klik pada jendela Command Prompt yang menjalankan `composer run dev`
2. Tekan **Ctrl + C** di keyboard
3. Jika muncul pertanyaan `Terminate batch job (Y/N)?`, ketik **Y** lalu Enter
4. Buka XAMPP Control Panel → Klik **Stop** pada Apache dan MySQL

---

## 🔄 Cara Menjalankan Website Lagi (Setelah Komputer Dimatikan)

Setiap kali ingin menggunakan website lagi:

1. **Buka XAMPP** → Start **Apache** dan **MySQL**
2. **Buka Command Prompt** di folder project
3. Ketik: `composer run dev`
4. Buka browser, ketik: **http://localhost:8000**

---

# ❓ TROUBLESHOOTING (Solusi Masalah)

## 🔴 "File .env tidak terlihat di folder"

File .env adalah file tersembunyi (hidden). Untuk menampilkannya:

1. Buka File Explorer
2. Klik tab **View** di bagian atas
3. Centang **Hidden items** atau **Item tersembunyi**
4. Sekarang file .env akan terlihat

---

## 🔴 "php is not recognized..."

PHP belum terdaftar di PATH sistem. Solusi:

1. Buka **XAMPP Control Panel**
2. Pastikan Apache sudah **Start**
3. Atau, tambahkan PHP ke PATH:
   - Klik Windows → ketik "Environment Variables"
   - Klik **Edit the system environment variables**
   - Klik **Environment Variables**
   - Di System variables, cari **Path** → klik **Edit**
   - Klik **New** → tambahkan: `C:\xampp\php`
   - Klik **OK** sampai semua jendela tertutup
   - **Restart Command Prompt**

---

## 🔴 "Cannot connect to database" atau "Connection refused"

1. Pastikan XAMPP sudah running:
   - Buka XAMPP Control Panel
   - Apache dan MySQL harus berwarna **HIJAU**

2. Cek file .env:
   - `DB_HOST=127.0.0.1`
   - `DB_PORT=3306`
   - `DB_DATABASE=7khi_jurnal`
   - `DB_USERNAME=root`
   - `DB_PASSWORD=` (kosong)

---

## 🔴 "Port 8000 already in use"

Port 8000 sedang digunakan program lain. Solusi:

1. Gunakan port lain:
   ```
   php artisan serve --port=8080
   ```
2. Lalu akses: **http://localhost:8080**

---

## 🔴 "npm ERR!" atau "node not found"

Node.js belum terinstall atau belum terdaftar di PATH:

1. Coba restart komputer
2. Jika masih error, install ulang Node.js dari https://nodejs.org/

---

## 🔴 "Vite manifest not found"

Ini terjadi jika Vite belum berjalan. Solusi:

1. Pastikan menjalankan `composer run dev` (bukan `php artisan serve` saja)
2. Atau jalankan terpisah: `npm run dev` di terminal lain

---

## 🔴 Halaman website blank/kosong

1. Buka Developer Tools di browser (tekan **F12**)
2. Lihat tab **Console** untuk melihat error
3. Pastikan `npm run dev` atau `composer run dev` sudah berjalan

---

# 📋 RINGKASAN PERINTAH

Berikut urutan perintah yang perlu dijalankan (untuk copy-paste):

```bash
# Jalankan di Command Prompt, di folder project

# 1. Copy file environment
copy .env.example .env

# 2. Install PHP libraries
composer install

# 3. Generate key
php artisan key:generate

# 4. Install JavaScript libraries
npm install

# 5. Buat tabel database
php artisan migrate

# 6. Isi data contoh (opsional)
php artisan db:seed

# 7. Jalankan website
composer run dev
```

Setelah perintah ke-7, buka browser dan akses: **http://localhost:8000**

---

# 🎓 GLOSARIUM (Istilah-Istilah)

| Istilah | Penjelasan |
|---------|------------|
| **Localhost** | Komputer Anda sendiri sebagai server |
| **Terminal/CMD** | Program untuk mengetik perintah ke komputer |
| **npm** | Package manager untuk JavaScript (seperti Play Store untuk library JS) |
| **Composer** | Package manager untuk PHP (seperti Play Store untuk library PHP) |
| **Database** | Tempat menyimpan semua data website (user, aktivitas, dll) |
| **Migration** | Perintah untuk membuat struktur tabel di database |
| **Seeder** | Perintah untuk mengisi database dengan data contoh |
| **Port** | Seperti "pintu" untuk mengakses server (contoh: 8000, 80, 3306) |

---

# ✅ CHECKLIST INSTALASI

Gunakan checklist ini untuk memastikan semua langkah sudah dilakukan:

- [ ] XAMPP terinstall
- [ ] Composer terinstall  
- [ ] Node.js & npm terinstall
- [ ] Apache dan MySQL sudah Start di XAMPP
- [ ] Database `7khi_jurnal` sudah dibuat di phpMyAdmin
- [ ] File `.env` sudah di-copy dan diedit
- [ ] `composer install` sudah dijalankan
- [ ] `php artisan key:generate` sudah dijalankan
- [ ] `npm install` sudah dijalankan
- [ ] `php artisan migrate` sudah dijalankan
- [ ] `php artisan db:seed` sudah dijalankan (opsional)
- [ ] `composer run dev` sudah dijalankan
- [ ] Website bisa diakses di http://localhost:8000

---

> 📝 **Tutorial dibuat untuk:** Proyek Informatika Terapan - Semester 7
>
> 📅 **Terakhir diperbarui:** Januari 2026
>
> 💬 **Butuh bantuan?** Hubungi developer atau buka issue di repository project
