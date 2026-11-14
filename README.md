<div align="center">

# 🛰️ 9Router Controller Pro

**GUI manager untuk `9router`** — nyalakan &amp; matikan API AI lokal-mu dengan satu klik, tanpa pernah menyentuh terminal.

[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11%20%28x64%29-0078d6?style=flat-square&logo=windows&logoColor=white)](https://Maxodus126.github.io/9router-controller/)
[![Version](https://img.shields.io/badge/version-v1.1.0-c8ff4a?style=flat-square)]()
[![Node.js](https://img.shields.io/badge/node.js-bundled-339933?style=flat-square&logo=nodedotjs&logoColor=white)]()
[![Admin](https://img.shields.io/badge/admin-tidak%20diperlukan-success?style=flat-square)]()
[![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)]()
[![License](https://img.shields.io/badge/license-proprietary-lightgrey?style=flat-square)]()

[🌐 Situs produk](https://Maxodus126.github.io/9router-controller/) · [⬇️ Unduh](#-unduh) · [✨ Fitur](#-fitur) · [🚀 Mulai](#-cara-pakai) · [❓ FAQ](#-faq)

</div>

---

**9Router Controller Pro** adalah aplikasi desktop Windows yang membungkus `npx 9router` (server AI lokal) menjadi GUI yang sederhana *dan jujur*: satu tombol **START**, status kesehatan yang benar-benar dicek, **live console**, dan kontrol penuh atas proses yang berjalan.

Dibuat untuk orang yang ingin memakai AI lokal tanpa mau ribet dengan terminal, environment, atau proses yang berjalan diam-diam di background.

---

## 📦 Unduh

| Opsi | File | Ukuran | Catatan |
|------|------|--------|---------|
| 🤖 **Installer lengkap** (disarankan) | [`9Router_Setup.exe`](9Router_Setup.exe) | ~57 MB | Node.js dibundel · per-user · tanpa admin · membuat shortcut |

> 💡 **Kenapa hanya satu file?** Karena semuanya sudah termasuk — satu unduh, satu klik, langsung jalan.
>
> Alternatif: [GitHub Releases](https://github.com/Maxodus126/9router-controller/releases) · [situs produk](https://Maxodus126.github.io/9router-controller/).

---

## ✨ Fitur

- ⚡ **Start / Stop sekali klik** — menjalankan `npx 9router --tray` di background, tanpa jendela terminal.
- 🟢 **Status hidup jujur** — health check tiap 5 detik: `RUNNING`, `DEGRADED`, `EXTERNAL`, `STOPPED`. Bukan sekadar "proses ada".
- 🖥️ **Live Console** — seluruh stdout server mengalir real-time dengan timestamp dan tombol Clear.
- 📋 **Copy API URL** — port terdeteksi otomatis dari banner 9router, bukan angka mati.
- 🔄 **Restart cepat** &amp; 🩺 **Port Doctor** (selalu konfirmasi dulu, tak pernah membunuh diam-diam).
- 🛡️ **Auto-restart on crash** — maksimal 3× berturut-turut.
- 🪟 **System tray + Run on Windows Startup** — hilang ke tray, bisa menyala saat boot tanpa admin.
- 🔒 **Single-instance guard** &amp; hanya mengelola proses yang ia lahirkan sendiri — tidak pernah menyentuh server asing.
- 🔁 **Update otomatis** dari dalam app (self-update senyap).

---

## 🚀 Cara pakai

### Persyaratan
- **Windows 10 / 11, 64-bit**.
- Internet sekali saat pertama START (untuk mengunduh paket `9router` dari npm).
- Node.js **tidak wajib** — sudah dibundel di installer.

### Instalasi
```powershell
1. Unduh 9Router_Setup.exe
2. Klik dua kali → Install (per-user, tanpa admin)
3. Buka 9Router Controller Pro → tekan START
```

### Setelah START
App memanggil `npx 9router --tray --skip-update`, menunggu listener-nya, lalu menampilkan status `RUNNING` + URL API yang bisa disalin. Untuk menghentikan: tekan **STOP** — app membunuh seluruh pohon proses yang ia kelola (bukan sembarang proses).

---

## 🛠️ Pengembangan

```bash
# 1. Setup
git clone https://github.com/Maxodus126/9router-controller.git
cd 9router-controller
pip install -r requirements.txt        # customtkinter, pystray, psutil, pillow

# 2. Jalankan dari source
python app.py

# 3. Build exe (PyInstaller)
pyinstaller --onefile --windowed --collect-all customtkinter --icon=app.ico --name 9RouterControllerPro app.py

# 4. Build installer (NSIS)
makensis installer.nsi                    # → dist/9Router_Setup.exe
```

### Struktur proyek
```
.
├── app.py                 # Aplikasi utama (GUI + kontrol proses + updater)
├── installer.nsi          # Skrip NSIS (install/uninstall, bundle node)
├── 9RouterControllerPro.spec
├── EULA.txt
├── app.ico
├── _bundle/node/          # Node.js portable yang dibundel installer
├── dist/                  # Hasil build (exe + installer)
├── index.html             # Landing page (GitHub Pages)
└── 9Router_Setup.exe      # Installer rilis
```

---

## 🔁 Update otomatis

App menargetkan repositori ini (`Maxodus126/9router-controller`) dan mengunduh aset **`9Router_Setup.exe`** dari GitHub Releases. Flow:

1. Tombol **Update** di app mengunduh installer baru ke `%TEMP%\9router_setup_update.exe`.
2. App menghentikan router-nya secara rapi, lalu menjalankan installer dengan `/S`.
3. Installer mengganti file, membuat ulang uninstaller, dan meluncurkan app versi baru.

> Proses ini ditangani tanpa admin dan tanpa menutup sesi yang sedang berjalan dengan kasar.

---

## ❓ FAQ

**Apakah perlu menginstal Node.js?**
Tidak — installer membawa Node.js portable.

**Apakah butuh Administrator?**
Tidak. Aplikasi terpasang per-user di `%LOCALAPPDATA%\Programs\9Router`.

**Bagaimana cara menghapus?**
Settings → Apps → 9Router Controller Pro → **Uninstall** (atau Control Panel). Keluar dari aplikasi dulu agar pembersihan maksimal.

**Apa bedanya dengan `npx 9router` manual?**
App memberi kontrol penuh: Stop/Restart, live console, port doctor, auto-restart, startup saat boot, dan status kesehatan yang jujur.

**Apakah tersedia update otomatis?**
Ya — lihat bagian [Update otomatis](#-update-otomatis).

---

## 🤝 Kontribusi

PR, ide, dan laporan masalah sangat diterima.

- 🐞 Laporkan bug: [Github Issues](https://github.com/Maxodus126/9router-controller/issues)
- 🌐 Situs produk: <https://Maxodus126.github.io/9router-controller/>

**Panduan singkat:**
1. Fork &amp; buat branch dari `master`.
2. Pastikan `python app.py` berjalan baik.
3. Buka Pull Request dengan deskripsi yang jelas.

---

## 📄 Lisensi

© 2026 Maxodus126 · proyek pribadi. Hak cipta dilindungi.
