# Arsitektur Proyek - SUPERMANS Mobile (Flutter)

Proyek ini menggunakan pola arsitektur **MVVM (Model-View-ViewModel)** untuk memisahkan logika bisnis, pengelolaan data, dan antarmuka pengguna secara modular.

## Struktur Direktori (`lib/`)
- **`app/`**: Menyimpan konfigurasi global, tema aplikasi (`AppTheme`), dan manajemen rute.
- **`data/`**: Menyimpan model data, service, dan repositori yang berinteraksi langsung dengan RESTful API Laravel.
- **`presentation/`**: Menyimpan komponen antarmuka pengguna (UI) berupa *screens* (layar) dan *widgets* pendukung.
- **`utils/`**: Menyimpan fungsi utilitas, konstanta, dan *helpers*.