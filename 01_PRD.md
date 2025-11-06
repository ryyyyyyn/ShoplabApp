PRODUCT REQUIREMENT DOCUMENT (PRD) - ShopLabApp
Nama Produk: Kalkulator HPP + Laba Otomatis
Versi Dokumen: 1.0
Tanggal Efektif: 7 November 2025
Disusun oleh:ryan -221240001281
             niam -221240001241
Platform: Mobile (Flutter – Android & iOS)

1. 🎯 Executive Summary
Aplikasi Kalkulator HPP + Laba Otomatis dirancang sebagai solusi digital ringan, cepat, dan akurat untuk membantu pelaku UMKM dan seller online menghitung Harga Pokok Penjualan (HPP) serta menentukan harga jual ideal dan laba bersih — tanpa memerlukan keahlian akuntansi. Aplikasi ini bersifat offline-first, user-friendly, dan dapat diakses oleh siapa saja dalam hitungan detik.

Tagline:
“Hitung HPP & Laba dalam 10 Detik — Tanpa Ribet, Tanpa Salah Hitung.” 

2. 🎯 Tujuan Produk
2.1. Primary Objective
Mempermudah proses penetapan harga produk dengan cara otomatis berbasis input sederhana, sehingga:

Seller tidak lagi mengandalkan perhitungan manual di kalkulator atau Excel.
Pengambilan keputusan harga lebih objektif dan profit-oriented.
Mengurangi kesalahan margin dan kerugian tak sadar.
2.2. Success Criteria (SMART)
Specific
: Pengguna dapat menghitung HPP + laba dalam 1 halaman utama
✅
Measurable
: Rata-rata waktu perhitungan ≤ 15 detik
✅
Achievable
: Tidak perlu koneksi internet / akun
✅
Relevant
: Menjawab kebutuhan riil UMKM & seller online
✅
Time-bound
: Peluncuran V1.0 dalam 60 hari
✅

3. 👥 Target Pengguna (User Personas)
Pak Budi – Penjual UMKM
Pemilik toko online di Shopee (kuliner & kerajinan). Usia 40an, tidak kuliah ekonomi.
Bingung hitung ongkir + packing + fee marketplace. Sering rugi karena harga jual terlalu rendah.
Solusi satu-klik untuk harga jual yang menguntungkan.
Siska – Dropshipper Pemula
Mahasiswa semester 4, jualan skincare via Instagram.
Takut salah ambil margin. Tidak tahu komponen biaya tersembunyi.
Edukasi ringan + kalkulator instan.
Andi – Reseller Elektronik
Reseller gadget, beli grosir, jual eceran.
Banyak variabel biaya (admin, garansi, pengembalian).
Simpan & bandingkan perhitungan produk berbeda.
Rina – Mahasiswa Bisnis
Sedang mengerjakan tugas akuntansi biaya.
Rumus HPP terlalu abstrak.
Visualisasi komponen biaya & simulasi praktis.

4. 💡 Value Proposition
❌ Perhitungan HPP manual rentan error
✅ Hitung otomatis dengan formula valid
Akurasi 100%
via validasi matematis
❌ Tidak paham komponen biaya tersembunyi
✅ Input terstruktur: ongkir, admin (%), packing
Edukasi implisit
melalui antarmuka
❌ Tidak ada alat khusus UMKM
✅ Aplikasi mobile ringan (<10 MB), tanpa login
Zero friction
— buka & langsung hitung
❌ Hasil tidak bisa disimpan/direview
✅ Riwayat lokal + detail perhitungan
Reusability
— edit & hitung ulang kapan saja

✅ USP Utama: Aplikasi satu-satunya di Indonesia yang fokus khusus pada kalkulasi HPP & laba untuk seller online — bukan kalkulator biasa. 

5. 🛠️ Fitur Utama & Spesifikasi
5.1. 🧮 Kalkulator HPP (Core Feature)
Input Fields (Validated & Formatted)
Harga Produk
Numeric
Rp 10.000
(otomatis format)
Min: Rp 1
Ongkir
Numeric
Rp 12.500
≥ 0
Biaya Admin
Numeric +
%
5%
Min: 0%, Max: 50%*
Biaya Packing
Numeric
Rp 2.000
≥ 0
Margin Keuntungan
Numeric +
%
25%
Min: 0%, Max: 200%

*Catatan: Biaya admin >50% akan muncul warning: “Biaya admin sangat tinggi. Pastikan ini benar?” 

Output (Real-time Preview)
Total HPP
Harga_Produk + Ongkir + Biaya_Packing + (Harga_Produk × Biaya_Admin / 100)
Harga Jual Ideal
Total_HPP × (1 + Margin / 100)
Laba Bersih
Harga_Jual – Total_HPP

✅ Bonus UX:

Warna output berubah berdasarkan profitabilitas:
🟢 Laba > 0 → hijau
🟡 Laba = 0 → kuning
🔴 Laba < 0 → merah + warning icon (⚠️)
Animasi ringan saat hasil muncul (fade-in + slide-up).
5.2. 📜 Riwayat Perhitungan
Penyimpanan: Lokal (Hive DB), tanpa sinkronisasi cloud (V1.0).
Data tersimpan per entri:
json


1
2
3
4
5
6
7
8
9
10
11
12
13
⌄
{
  "id": "hpp_20251107_001",
  "timestamp": "2025-11-07T14:30:00Z",
  "product_name": "Masker Kain Premium",
  "harga_produk": 15000,
  "ongkir": 9000,
  "biaya_admin": 5,
  "biaya_packing": 2000,
  "margin": 30,
  "total_hpp": 27250,
  "harga_jual": 35425,
  "laba_bersih": 8175
}
UI: List card dengan:
Nama produk (default: “Produk #1” jika kosong)
Harga jual & laba (highlight)
Tanggal & jam
Tombol: 🗑️ Hapus | 👁️ Lihat Detail
5.3. 📋 Detail Perhitungan
Diakses dari riwayat atau hasil kalkulasi langsung.
Menampilkan:
Semua input (editable)
Formula per baris (dengan breakdown)
Tombol:
✏️ Edit & Hitung Ulang → kembali ke halaman kalkulator dengan prefill
💾 Simpan ke Riwayat (jika belum tersimpan)
📤 Bagikan Hasil (opsi: teks biasa / screenshot) → V1.1
5.4. 🧭 Onboarding Flow
1
Ilustrasi seller kebingungan hitung harga
“Bingung menentukan harga jual yang menguntungkan?”
2
Demo UI kalkulator (input → hasil)
“Cukup isi modal, ongkir, dan margin — biar kami yang hitung!”
3
Screenshot riwayat + tema gelap
“Semua hasil tersimpan. Gampang, cepat, 100% offline.”

✅ Skip button di pojok kanan atas
✅ “Mulai Sekarang” → pindah ke halaman kalkulator utama
✅ Hanya tampil pertama kali (dilacak via SharedPreferences)
5.5. ⚙️ Pengaturan (Settings)
Tema
Toggle: Light / Dark / Auto (mengikuti sistem)
Warna Utama
Pilihan: Oranye (default), Biru, Hijau, Ungu
(brand customization)
Hapus Semua Riwayat
Konfirmasi modal: “Yakin hapus semua data? Tidak bisa dikembalikan.”
Versi Aplikasi
v1.0.0 (Build 20251107)
Rate Aplikasi
Link ke Play Store / App Store

5.6. ℹ️ Tentang Aplikasi
Logo aplikasi (SVG/PNG)
Deskripsi:
“Kalkulator HPP + Laba Otomatis adalah aplikasi open-source ringan untuk membantu UMKM dan seller online menentukan harga jual ideal — akurat, cepat, dan tanpa iklan.” 
Kredit:
Dibuat dengan ❤️ oleh Ryan (@PopOfficialStore)
Kontak: ryan.popofficial@gmail.com
GitHub: github.com/PopOfficial/kalkulator-hpp (opsional, untuk transparansi) 
6. 🔄 User Flow (End-to-End)
graph TD
  A[Splash Screen<br>(2 detik)] --> B{Pertama kali buka?}
  B -->|Ya| C[Onboarding 3 Slide]
  B -->|Tidak| D[Kalkulator HPP]
  C --> D
  D --> E[Pengguna isi form]
  E --> F[Tekan “Hitung HPP”]
  F --> G{Tampil hasil}
  G --> H1[Simpan ke Riwayat]
  G --> H2[Reset Form]
  G --> H3[Lihat Detail]
  H1 --> I[Riwayat]
  H3 --> J[Detail Perhitungan]
  J --> K1[Edit & Hitung Ulang]
  J --> K2[Bagikan]
  D & I & J --> L[Menu Sidebar: Pengaturan, Tentang]
7. 🎨 UI/UX Requirements
7.1. Design System
Warna Primer
Oranye:
#FF6F00
(Material Orange 800)
Warna Sekunder
Abu-abu:
#F5F5F5
(Light BG),
#2D2D2D
(Dark Text)
Font
Poppins
(Headline),
Inter
(Body) — Google Fonts
Ikon
Material Icons
atau
Fluent UI
versi Flutter
Spacing
8px baseline grid (padding: 16, margin: 8/16/24)
Elevation
Card:
elevation: 2
, Shadow lembut

7.2. UX Principles
✅ Single-hand usability: Tombol utama di bawah (bottom sheet atau floating button).
✅ Input masking: Otomatis format Rupiah (contoh: ketik 15000 → Rp 15.000).
✅ Error prevention: Non-numeric input diblokir.
✅ Micro-interactions:
Hover effect tombol
Loading spinner saat “Hitung”
Toast sukses saat simpan riwayat
✅ Accessibility: Kontras tinggi, teks minimum 12pt.
8. ⚙️ Spesifikasi Teknis
Framework
Flutter 3.24+ (Stable Channel)
Bahasa
Dart (Null Safety enabled)
State Management
Riverpod 2.5+ (Provider alternatif jika tim lebih familiar)
Database Lokal
Hive (enkripsi opsional via
hive_flutter
)
Persistent Storage
SharedPreferences
untuk onboarding flag, tema, warna
UI Kit
flutter_screenutil
(responsive),
flutter_riverpod
,
go_router
(navigation)
Formatting
intl
package (Rupiah:
NumberFormat.currency(locale: 'id', symbol: 'Rp ')
)
Testing
Unit test (
test
), Widget test (
flutter test
), Integration test (
integration_test
)
Build Target
Android (min SDK 21), iOS (min 13.0)
Build Size Target
≤ 8 MB (APK), ≤ 12 MB (IPA)

9. 🔐 Keamanan & Privasi
Tidak ada data dikirim ke server — 100% offline.
Data lokal tidak dienkripsi (V1.0), tetapi:
Tidak menyimpan data sensitif (no KTP, rekening, dll).
Riwayat hanya berisi angka & nama produk.
GDPR/PP No. 27/2020 Compliance:
Privacy Policy tersedia di menu “Tentang” (template dasar).
Opsi hapus semua data.
Tidak menggunakan tracking (Analytics/Ads di V1.0).
📝 Catatan: Jika nanti ada integrasi cloud (V1.2), enkripsi end-to-end akan diterapkan. 

10. 🗓️ Roadmap Pengembangan
v1.0
Kalkulator HPP + Riwayat Lokal + Onboarding + Pengaturan
Nov–Des 2025
🔴 High
v1.1
- Ekspor hasil ke PDF/CSV
- Bagikan hasil (text/screenshot)
- Notifikasi margin terlalu rendah
Jan 2026
🟠 Medium
v1.2
- Sinkronisasi cloud (Firebase Auth + Firestore opsional)
- Backup/restore via Google Drive/iCloud
Feb 2026
🟢 Low
v2.0
- Integrasi AI Pricing:
• Analisis harga kompetitor (scrape publik)
• Rekomendasi margin berdasarkan kategori produk
Q2 2026
🟢 Future

11. 📊 KPI & Metrik Keberhasilan
Unduhan
≥ 1.000 (Play Store + App Store)
Firebase Analytics / App Store Connect
Retensi Mingguan (WAU)
≥ 80%
Mixpanel (opsional) / Local event logging
Rata-rata Waktu Sesuai
≤ 3 menit
Event:
session_start
→
session_end
Conversion: Simpan ke Riwayat
≥ 60% pengguna aktif
Event:
calculation_saved
Rating Rata-rata
≥ 4.5/5
Store review scraping
Crash Rate
≤ 0.5%
Firebase Crashlytics

12. 👥 Tim & Peran
Product Owner
Ryan (@PopOfficialStore)
PRD, Prioritisasi fitur, UAT, Release Management
UI/UX Designer
Stitch.ai (AI-assisted) + Validasi Manual
Wireframe → High-Fidelity Mockup (Figma)
Flutter Developer
Ryan / Freelance
Implementasi, Testing, Build APK/IPA
QA Tester
Komunitas Beta (5–10 UMKM)
Usability test, bug reporting, feedback loop
Legal & Compliance
Ryan (self-review)
Privacy policy, terms of use draft

Catatan: Tim lean — 1–2 orang inti. Mengoptimalkan tools otomatis (AI design, code generation). 

13. 📦 Deliverables
PRD
PDF / Google Doc
Dokumen ini
Desain UI/UX
Figma (link shareable)
Termasuk prototipe interaktif
Source Code
GitHub Private Repo
Branch:
main
,
dev
,
release/v1.0
Aset Grafis
ZIP (logo, icon, splash)
512x512, 1024x1024, adaptive icon, App Store assets
Build APK (Beta)
.apk
+
release-notes.txt
Untuk tester internal
Dokumentasi Teknis
README.md
Setup, build, run, test

14. 🏁 Kesimpulan & Next Steps
Kalkulator HPP + Laba Otomatis bukan sekadar kalkulator — melainkan business enabler untuk jutaan UMKM Indonesia yang ingin tumbuh dengan fondasi keuangan yang sehat.

Dengan pendekatan simplicity first, aplikasi ini menjawab kebutuhan nyata:
✅ Cepat — hitung dalam 10 detik
✅ Akurat — formula valid, zero error
✅ Bebas — tanpa iklan, tanpa login, 100% offline

✅ Next Steps:
Finalisasi desain Figma (3 hari)
Kickoff development (60 hari → target rilis: 7 Januari 2026)
Closed beta test dengan 20 seller UMKM
Rilis publik di Play Store & App Store
Dibuat oleh:
Muhamad Arianto - 221240001281
Rifqy niam fadhil - 221240001241


“Bisnis kecil layak punya tools besar.”

📥 Lampiran:

Template Privacy Policy (draft)
Mockup Figma (link)
Formula HPP Validation (spreadsheet audit)
