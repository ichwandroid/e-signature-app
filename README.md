# E-Signature System (Sekolah Anak Saleh)

Sistem tanda tangan digital berbasis web yang dirancang untuk mempermudah proses penandatanganan dokumen secara elektronik dengan fitur verifikasi keamanan menggunakan QR Code.

## 🚀 Fitur Utama

- **Autentikasi Pengguna**: Login aman menggunakan Firebase Authentication.
- **Canvas Tanda Tangan**: Input tanda tangan langsung menggunakan pointer atau sentuhan (berbasis `signature_pad`).
- **Watermarking Otomatis**: Setiap tanda tangan yang disimpan akan memiliki watermark berupa ID unik dan stempel waktu untuk mencegah penyalahgunaan.
- **Integrasi QR Code**: Pembuatan QR Code otomatis untuk setiap tanda tangan yang merujuk ke halaman validasi publik.
- **Halaman Validasi Publik**: Memungkinkan pihak ketiga untuk memverifikasi keaslian tanda tangan dengan memindai QR Code.
- **Keamanan Data**: Gambar tanda tangan di halaman validasi hanya ditampilkan selama 20 detik untuk menjaga privasi.
- **Custom Logo**: Penyesuaian logo otomatis berdasarkan akun pengguna (contoh: Logo PAUD vs Logo Sekolah Umum).

## 🛠️ Teknologi yang Digunakan

- **Frontend**: HTML5, Tailwind CSS, JavaScript (Vanilla ES6).
- **Library**:
  - [Signature Pad](https://github.com/szimek/signature_pad) - Untuk menangkap tanda tangan.
  - [QR Code Styling](https://github.com/SumiMakito/qr-code-styling) - Untuk menghasilkan QR Code yang estetik.
- **Backend (BaaS)**:
  - **Firebase Auth**: Manajemen pengguna.
  - **Firebase Firestore**: Penyimpanan data tanda tangan dan metadata.
  - **Firebase Hosting**: Untuk menayangkan aplikasi secara online.

## 🚀 Cara Menjalankan Proyek

### 1. Prasyarat
Pastikan Anda sudah menginstal [Node.js](https://nodejs.org/) di komputer Anda.

### 2. Instal Firebase Tools
Buka terminal dan jalankan perintah berikut untuk menginstal Firebase CLI secara global:
```bash
npm install -g firebase-tools
```

### 3. Login ke Firebase
Jalankan perintah berikut dan login menggunakan akun Google Anda:
```bash
firebase login
```

### 4. Menjalankan Server Lokal
Untuk mencoba aplikasi di komputer lokal (localhost), jalankan:
```bash
firebase serve
```
Setelah perintah dijalankan, buka browser dan akses alamat yang muncul (biasanya `http://localhost:5000`).

### 5. Deployment (Mengunggah ke Internet)
Jika ingin mengunggah perubahan ke Firebase Hosting agar bisa diakses publik:
```bash
firebase deploy
```


## 📂 Struktur Proyek

```text
├── index.html          # Halaman Login
├── dashboard.html      # Halaman Utama (Buat & List Tanda Tangan)
├── validasi.html       # Halaman Verifikasi Publik (via QR Code)
├── 404.html            # Halaman Error 404
├── firebase.json       # Konfigurasi Firebase Hosting
└── ico.png             # Ikon Aplikasi
```

## ⚙️ Cara Penggunaan

1.  **Login**: Gunakan akun yang telah terdaftar di Firebase Console.
2.  **Buat Tanda Tangan**:
    - Isi data penanda tangan (Nama, NIY, Jabatan, SK, Nama Dokumen).
    - Berikan tanda tangan pada area canvas yang tersedia.
    - Klik **Simpan**.
3.  **Manajemen Data**:
    - Lihat daftar tanda tangan yang telah dibuat di panel kanan.
    - Unduh QR Code untuk ditempelkan pada dokumen fisik atau digital.
    - Hapus data jika sudah tidak diperlukan.
4.  **Verifikasi**:
    - Pindai QR Code menggunakan kamera ponsel.
    - Anda akan diarahkan ke halaman `validasi.html` untuk melihat detail data asli yang tersimpan di database.

## 🔧 Konfigurasi Firebase

Pastikan Anda telah mengonfigurasi Firebase SDK di setiap file HTML (`index.html`, `dashboard.html`, `validasi.html`) dengan `firebaseConfig` milik proyek Anda:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

## 📝 Lisensi

Proyek ini dikembangkan untuk kebutuhan internal Sekolah Anak Saleh.
