# SIMLOG PWA Shell

File utama: `on.html`.

## Upload ke GitHub Pages
1. Upload semua file dalam folder ini ke repository GitHub.
2. Aktifkan GitHub Pages dari Settings > Pages.
3. Buka URL GitHub Pages yang mengarah ke `on.html`.

## Logout kembali ke halaman awal/login
Karena aplikasi utama berjalan di iframe cross-origin Google Apps Script, shell luar tidak bisa membaca isi halaman atau URL iframe secara langsung. Agar tombol logout di aplikasi utama bisa memerintah shell kembali ke halaman login, tambahkan baris berikut pada fungsi logout di aplikasi Google Apps Script/client HTML:

```js
parent.postMessage('SIMLOG_LOGOUT', '*');
```

Atau:

```js
parent.postMessage({ type: 'SIMLOG_LOGOUT' }, '*');
```

Shell akan memuat ulang iframe dengan cache-buster sehingga kembali segar ke halaman awal/login.
