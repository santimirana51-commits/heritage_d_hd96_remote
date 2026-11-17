# MIDAS Heritage D HD96 Android Remote (OSC UDP)

Aplikasi remote kontrol Android nirkabel untuk mixer audio digital **[MIDAS Heritage D HD96-24 Virtual Touring Console](https://github.com/santimirana51-commits/midas_heritage_d_hd96_virtual_touring_console)** melalui protokol **OSC UDP** berkecepatan tinggi (Port default: `53000`).

---

## 📱 Unduh & Pasang APK (Siap Pakai)

Anda dapat langsung mengunduh file APK yang sudah dikompilasi tanpa perlu build dari source:
👉 **[Unduh HeritageRemote-debug.apk](https://github.com/santimirana51-commits/heritage_d_hd96_remote/raw/main/HeritageRemote-debug.apk)** (~5.3 MB)

### Cara Install ke HP/Tablet Android:
1. Unduh `HeritageRemote-debug.apk` langsung ke HP Android Anda.
2. Tap file hasil unduhan untuk menginstal (aktifkan izin *Install from Unknown Sources / Sumber tidak dikenal* pada pengaturan Android Anda).
3. Atau pasang via ADB jika HP terhubung kabel USB ke komputer:
   ```bash
   adb install -r HeritageRemote-debug.apk
   ```

---

## 🎛️ Fitur & Tampilan Antarmuka

- **Vertical Touch Faders (Sentuh Vertikal Asli)**:
  - Fader bereaksi natural terhadap gestur sentuh vertikal (usap ke **atas** untuk menaikkan volume, usap ke **bawah** untuk menurunkan volume).
  - Skala fader mencakup rentang `-60.0 dB` hingga `+10.0 dB` dengan indikator angka dB real-time.
  - Warna fader channel aksen cyan (`#38BDF8`) dan fader Master aksen gold (`#F59E0B`).
- **144 Channel Mixing (18 Bank × 8 Channel)**:
  - Navigasi cepat dengan tombol **`< BANK`** dan **`BANK >`** (Bank 1: Ch 1-8 s/d Bank 18: Ch 137-144).
  - Tombol **MUTE** independen per channel (lampu indikator merah menyala).
  - Tombol **SOLO** independen per channel (lampu indikator kuning menyala).
- **Master L/R Stereo Fader**: Kendali fader stereo utama mixer PC (`/main/fader`) dengan sinkronisasi dua arah.
- **Talkback Toggle**: Menyalakan / mematikan mikrofon komunikasi panggung (`/talkback/on`).
- **Verifikasi Koneksi Cepat (PING)**: Menguji sambungan UDP dan membaca nama sistem, versi, jumlah channel, serta sample rate mixer PC.

---

## 🚀 Panduan Menghubungkan ke PC Mixer

### 1. Di Komputer (PC Mixer):
1. Jalankan aplikasi mixer di PC: **[midas_heritage_d_hd96_virtual_touring_console](https://github.com/santimirana51-commits/midas_heritage_d_hd96_virtual_touring_console)**.
2. Di toolbar atas, klik tombol **`OSC SERVER`** (atau navigasi konsol: **`SYSTEM`** → **`OSC Protocol Server`**).
3. Pastikan kolom **UDP Port** bernilai `53000`, lalu klik tombol hijau **`START SERVER`** hingga status menyala hijau: `RUNNING (Port: 53000)`.

### 2. Di HP / Tablet Android:
1. Pastikan HP dan PC berada di **jaringan Wi-Fi yang sama**.
2. Buka aplikasi **Heritage HD96 Remote**.
3. Di bilah atas:
   - Masukkan alamat IP lokal PC mixer (misalnya: `192.168.100.8`).
   - Masukkan Port: `53000`.
   - Tekan tombol **`PING`**.
4. Status bar akan menampilkan konfirmasi balasan:
   > `CONNECTED: NOVA HD DIGITAL MIXING SYSTEM v1.7.0 (144 ch)`
5. Sekarang geser fader di HP Anda — fader di PC akan langsung bergerak seketika!

---

## ⚠️ Troubleshooting Jika Tidak Terhubung

Jika saat menekan tombol `PING` muncul tulisan `TIMEOUT / NO REPLY`:
1. **Windows Firewall di PC Memblokir Paket Masuk**:
   Buka PowerShell sebagai Administrator di PC, lalu jalankan perintah ini:
   ```powershell
   Set-NetFirewallRule -DisplayName "openlive hd digital mixing system.exe" -Action Allow
   New-NetFirewallRule -DisplayName "OPENLIVE OSC UDP 53000" -Direction Inbound -Protocol UDP -LocalPort 53000 -Action Allow
   ```
2. **Cek Alamat IP PC yang Benar**:
   Jalankan `ipconfig` di PC untuk memastikan Anda memasukkan alamat IPv4 Wi-Fi yang tepat (bukan IP adapter virtual/Ethernet yang tidak aktif).
3. **Fitur AP / Client Isolation di Router**:
   Pastikan router Wi-Fi tidak mengaktifkan fitur *Client Isolation* (mode tamu) yang mencegah perangkat saling berkomunikasi di jaringan lokal.

---

## 🛠️ Kompilasi dari Source Code

Proyek ini dibangun menggunakan **Android Studio** atau command-line Gradle:

- **Persyaratan**: JDK 17+ / JBR 25 dan Android SDK 34 (Build-Tools 34.0.0).
- **Perintah Build**:
  ```bash
  # Windows
  gradlew.bat assembleDebug

  # Linux / macOS
  ./gradlew assembleDebug
  ```
Output APK berada di `app/build/outputs/apk/debug/app-debug.apk`.
