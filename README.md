# Website Galeri Sekolah (Laravel 11/12)

File-file di folder ini adalah "overlay": salin ke atas project Laravel baru.

## Instalasi
```bash
composer create-project laravel/laravel galeri-sekolah
cd galeri-sekolah
# salin seluruh isi zip ini ke folder project (timpa routes/web.php & AppServiceProvider.php)
# atur database di .env (MySQL: DB_CONNECTION=mysql, DB_DATABASE=galeri_sekolah, dst.)
php artisan migrate --seed
php artisan storage:link
php artisan serve
```
Ekstensi PHP **GD** harus aktif (untuk kompres gambar). Naikkan `upload_max_filesize` & `post_max_size` di php.ini bila perlu.

## Akun contoh (password: `password`)
- superadmin@sekolah.test (Super Admin) — semua menu
- admin@sekolah.test (Admin) — galeri, berita, album, kategori, banner, pengaturan
- editor@sekolah.test (Editor) — foto, video, berita (tanpa hapus)

Login di `/login`, dashboard di `/admin`. **Ganti password sebelum produksi.**

## Struktur
- `config/admin.php` — definisi modul admin (kolom, field, role). Tambah modul baru cukup di sini.
- `app/Http/Controllers/Admin/CrudController.php` — CRUD generik + upload & kompres gambar + activity log.
- `app/Http/Controllers/FrontController.php` — halaman pengunjung.
- `resources/views/` — Blade (Bootstrap 5 via CDN).
