# LMS MAN 19 (Aplikasi Android)

Aplikasi Android berbasis WebView yang membuka website
https://man19.assessment.web.id/login

Data (akun, soal, ujian, nilai) tetap ada di server website. Aplikasi hanya
menampilkan website tersebut, jadi perubahan di website otomatis tampil di aplikasi.

Syarat HP: Android 10 atau lebih baru, dan koneksi internet.

---

## Cara membuat APK (lewat GitHub, tanpa install apa pun di komputer)

1. Buat akun GitHub di https://github.com jika belum punya.
2. Klik tombol **+** di kanan atas, pilih **New repository**.
   Beri nama, misalnya `lms-man19`, lalu klik **Create repository**.
3. Ekstrak file zip ini di komputer.
4. Di halaman repository, klik **uploading an existing file**.
   Seret SEMUA isi folder hasil ekstrak, termasuk folder `.github`, `app`,
   dan file `build.gradle`, `settings.gradle`, `gradle.properties`.
   Catatan: folder `.github` bersifat tersembunyi di sebagian komputer.
   Pastikan folder itu ikut terunggah (di dalamnya ada `workflows/build.yml`).
5. Klik **Commit changes**.
6. Buka tab **Actions**. Build **Build APK** akan berjalan otomatis
   (jika tidak, pilih **Build APK** lalu klik **Run workflow**).
7. Tunggu sampai ada tanda centang hijau (sekitar 3 sampai 6 menit).
8. Klik build yang selesai, lalu di bagian **Artifacts** unduh **LMS-MAN19-apk**.
9. Ekstrak zip hasil unduhan. Di dalamnya ada `app-debug.apk`.

## Cara memasang di HP

1. Kirim `app-debug.apk` ke HP (WhatsApp, Drive, kabel USB, dll).
2. Buka file APK di HP.
3. Jika diminta, izinkan **Install dari sumber tidak dikenal** untuk aplikasi
   yang Anda pakai membuka file tersebut.
4. Tekan **Install**, lalu buka aplikasi **LMS MAN 19**.

---

## Mengubah alamat website

Buka `app/src/main/java/id/sch/man19lms/MainActivity.java`, ubah dua baris ini:

    private static final String HOME = "https://man19.assessment.web.id/login";
    private static final String HOST = "man19.assessment.web.id";

`HOME` adalah halaman awal, `HOST` adalah domain yang boleh dibuka di dalam
aplikasi. Tautan ke domain lain dibuka di browser HP.

## Mengubah nama aplikasi

Ubah `app/src/main/res/values/strings.xml` (nilai `app_name`).

## Jika build gagal

- Buka tab **Actions**, klik build yang gagal, lalu lihat langkah yang bertanda merah.
- Pastikan folder `.github/workflows/build.yml` ikut terunggah.
- Pastikan `app/build.gradle` dan `build.gradle` ada di lokasi aslinya
  (jangan ada folder tambahan di atasnya setelah diunggah).

## Catatan

- APK yang dihasilkan adalah versi debug dan cukup untuk dipasang langsung di HP.
- Untuk dipublikasikan ke Play Store diperlukan APK/AAB yang ditandatangani (release).
