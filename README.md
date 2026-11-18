# CBT Enterprise - Versi Google Apps Script + Siap GitHub Pages

Paket ZIP ini mendukung **2 cara penggunaan sekaligus**:
1. **Dijalankan langsung lewat link Apps Script (`/exec`)**, ATAU
2. **Ditaruh & dijalankan dari GitHub Pages (`https://username.github.io/nama-repo/`)** sambil tetap memakai Google Spreadsheet & Google Form di Apps Script sebagai server/database!

---

## Isi File di Dalam ZIP
- `Code.gs` — Backend Google Apps Script + Spreadsheet + API Bridge (`doGet` & `doPost`).
- `appsscript.json` — Manifes izin OAuth lengkap (Spreadsheet, Forms, Drive, Docs, Mail, UrlFetch).
- `index.html` — Halaman **CBT Siswa** (huruf kecil `index.html` agar otomatis terbaca oleh GitHub Pages).
- `Index.html` — Halaman **CBT Siswa** (format nama Apps Script).
- `Admin.html` — Panel Admin (Upload soal, kelola siswa, link Google Form per mapel, pengaturan).
- `Proktor.html` — Panel Proktor / Pengawas ujian.
- `gas-config.js` — Pengaturan URL Web App Apps Script (`/exec`) untuk GitHub Pages.
- `gas-bridge.js` — Penghubung otomatis `google.script.run` agar jalan di GitHub Pages.

---

## Langkah Memasang CBT Versi Apps Script di GitHub Pages

### Langkah 1 — Perbarui & Deploy Google Apps Script (Wajib!)
1. Buka Google Spreadsheet Anda &rarr; klik **Ekstensi > Apps Script**.
2. Ganti isi **`Code.gs`** dengan file `Code.gs` dari ZIP ini (pastikan `SPREADSHEET_ID` diisi jika perlu, atau kosongkan `''` bila dibuka dari Ekstensi Spreadsheet).
3. Tempel juga `Index.html`, `Admin.html`, `Proktor.html`, dan `appsscript.json` di editor Apps Script.
4. Klik **Deploy > Kelola Deployment** &rarr; klik ikon **Pensil (Edit)** &rarr; pilih **Versi: Versi Baru** &rarr; pastikan:
   - **Jalankan sebagai**: *Saya (email Anda)*
   - **Yang memiliki akses**: *Siapa saja (Anyone)*
5. Klik **Terapkan** dan salin URL Web App (`/exec`) Anda.

### Langkah 2 — Atur Link `/exec` di `gas-config.js`
1. Buka file `gas-config.js` menggunakan Notepad / editor teks.
2. Pastikan `window.CBT_GAS_EXEC_URL` sudah sesuai dengan link Web App (`/exec`) Anda:
   ```js
   window.CBT_GAS_EXEC_URL = 'https://script.google.com/macros/s/.../exec';
   ```

### Langkah 3 — Upload ke GitHub & Aktifkan GitHub Pages
1. Buka repository GitHub Anda (contoh: `https://github.com/username/Cbtnesaka`).
2. Klik **Add file > Upload files**, lalu seret seluruh file hasil ekstrak ZIP ini (**terutama `index.html`, `Admin.html`, `Proktor.html`, `gas-config.js`, `gas-bridge.js`**) ke branch `main`, lalu klik **Commit changes**.
3. Buka menu **Settings > Pages** di repository GitHub Anda:
   - **Source**: *Deploy from a branch*
   - **Branch**: `main` / `/ (root)` &rarr; klik **Save**.
4. Tunggu 1–2 menit hingga link GitHub Pages muncul:
   - **CBT Siswa**: `https://username.github.io/nama-repo/`
   - **CBT Admin**: `https://username.github.io/nama-repo/Admin.html`
   - **CBT Proktor**: `https://username.github.io/nama-repo/Proktor.html`

> **Tips:** Jika ingin menguji link `/exec` berbeda tanpa edit file, cukup buka `https://username.github.io/nama-repo/?gasUrl=LINK_EXEC_ANDA`.
