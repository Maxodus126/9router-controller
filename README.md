# 9Router Controller Pro

GUI Manager desktop untuk **9router** (`npx 9router`) — tombol ON/OFF tanpa perlu membuka terminal.

> Situs produk: <https://Maxodus126.github.io/9router-controller/>

## Fitur
- **Start / Stop sekali klik** — menjalankan `npx 9router --tray` di background.
- **Status hidup jujur** — health check tiap 5 detik: RUNNING / DEGRADED / EXTERNAL / STOPPED.
- **Uptime & RAM** — monitor sumber daya proses 9router.
- **Live Console** — stdout real-time dengan timestamp.
- **Copy API URL** — port otomatis terdeteksi dari output 9router.
- **Restart cepat** & **Port Doctor** (dengan konfirmasi).
- **Auto-restart on crash** (maks 3×) & **Run on Windows Startup**.
- **System tray** + ikon status, single-instance guard.

## Unduh
- **Installer lengkap:** [`9Router_Setup.exe`](site/9Router_Setup.exe) (54,8 MB) — Node.js dibundel, tanpa admin, Windows 10/11 64-bit.
- **Portable:** [`9RouterControllerPro.exe`](dist/9RouterControllerPro.exe) — butuh Node.js terpasang.

## Instalasi (installer)
1. Jalankan `9Router_Setup.exe`.
2. Klik Install (per-user, tanpa admin).
3. Buka app → klik **START**.

## Kebutuhan
- **Windows 10/11 64-bit**.
- Internet sekali saat pertama START (unduh paket `9router` dari npm) — atau gunakan versi dengan pre-seed.
- Node.js tidak wajib (dibundel).

## Pengembangan
```bash
pip install -r requirements.txt        # customtkinter, pystray, psutil, pillow
python app.py
```
Build exe (PyInstaller):
```bash
pyinstaller --onefile --windowed --collect-all customtkinter --icon=app.ico --name 9RouterControllerPro app.py
```
Build installer (NSIS):
```bash
makensis installer.nsi
```

## Lisensi
© 2026 · proyek pribadi.
