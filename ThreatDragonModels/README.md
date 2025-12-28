# 🛡️ Payment Security: Threat Model Sistem Pembayaran Online Shop

Dokumentasi ini berisi **analisis Threat Modeling** mendalam pada sistem pembayaran *E-Commerce*. Proyek ini bertujuan untuk mengidentifikasi, menganalisis, dan memitigasi potensi ancaman keamanan mulai dari proses pemesanan pengguna hingga validasi transaksi pada jaringan perbankan dengan menggunakan kerangka kerja **STRIDE**.

---

## 📝 Informasi Analisis

- **Model Version:** 2.4.1  
- **Metodologi:** STRIDE Threat Modeling  
- **Total Ancaman Teridentifikasi:** 21 Threats  

Ancaman yang dianalisis mencakup:
- Manipulasi data transaksi
- Kebocoran kredensial dan data sensitif
- Gangguan ketersediaan layanan (*Denial of Service*)

---

## 🏗️ Komponen Sistem & Alur Data

Analisis memetakan interaksi antar entitas utama dalam ekosistem pembayaran online sebagai berikut:

### 1. Entitas Luar (Actors)
- **Pengguna / Pembeli**  
  Inisiator pesanan dan pemilik data pembayaran.
- **Payment Gateway**  
  Perantara terenkripsi antara aplikasi web dan sistem perbankan.
- **Bank / Layanan Keuangan**  
  Otoritas yang melakukan validasi saldo dan penyelesaian transaksi.

### 2. Proses Inti (Pipeline)
- **Pemesanan Produk**  
  Penanganan input data keranjang belanja.
- **Manajemen Opsi Pembayaran**  
  Penyajian metode pembayaran yang tersedia.
- **Pemrosesan Transaksi**  
  Pengiriman data transaksi ke payment gateway.
- **Validasi & Konfirmasi**  
  Sinkronisasi status pembayaran secara real-time.

---

## 🚨 Analisis Ancaman (STRIDE)

Ringkasan ancaman prioritas tinggi dan mitigasi teknis yang diusulkan:

### A. Spoofing & Tampering (Integritas Data)
**Manipulasi Data Pesanan**  
Penyerang mengubah harga atau jumlah produk sebelum checkout.  
- *Mitigasi:* Validasi harga di sisi server dan hashing data pesanan.

**Fraud Identitas Pembayaran**  
Penggunaan akun palsu atau kredensial curian.  
- *Mitigasi:* Multi-Factor Authentication (MFA) dan Rate Limiting.

---

### B. Information Disclosure (Privasi)
**Kebocoran Data Kartu Kredit**  
Data sensitif bocor saat transit atau penyimpanan.  
- *Mitigasi:*  
  - Kepatuhan standar **PCI-DSS**  
  - Tokenisasi data pembayaran  
  - Enkripsi komunikasi menggunakan **TLS 1.3**

---

### C. Denial of Service (Ketersediaan)
**Transaction Flooding**  
API transaksi dibanjiri permintaan palsu.  
- *Mitigasi:*  
  - API Gateway dengan Throttling  
  - Web Application Firewall (WAF)

---

## 🧱 Trust Boundaries (Batasan Kepercayaan)

Sistem dibagi menjadi beberapa zona keamanan untuk membatasi dampak serangan:

- **User Input Boundary**  
  Validasi ketat terhadap seluruh input dari pengguna.
- **Secure Gateway Bridge**  
  Enkripsi end-to-end antara aplikasi dan payment gateway.
- **Financial Network Interface**  
  Jalur komunikasi terisolasi ke sistem perbankan.
- **Order Integrity Zone**  
  Proteksi database transaksi agar bersifat *immutable*.

---

## 🛠️ Cara Mengakses Model Threat

Model ancaman dibuat menggunakan **OWASP Threat Dragon**.

Langkah untuk melihat diagram interaktif:
1. Buka **OWASP Threat Dragon Web App**
2. Pilih **Open an existing model**
3. Unggah file model ancaman (`.json`) dari repository ini
4. Navigasi ke tab **Diagrams** untuk melihat visualisasi STRIDE

---

## 💡 Metodologi

Proyek ini menerapkan prinsip **Security by Design**, dengan melakukan identifikasi ancaman sejak tahap desain sistem menggunakan **Data Flow Diagram (DFD)**. Pendekatan ini membantu pengembang merancang kontrol keamanan yang tepat sebelum implementasi kode, sehingga mengurangi risiko dan biaya perbaikan di tahap akhir pengembangan.

---

## 👩‍💻 Analyst

**Wahyudlp**  
Threat Modeling & Security Analysis
