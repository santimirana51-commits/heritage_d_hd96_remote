# MIDAS Heritage D HD96 Android Remote (OSC UDP)

Aplikasi remote kontrol Android nirkabel untuk mixer audio digital **[MIDAS Heritage D HD96 Virtual Touring Console](https://github.com/santimirana51-commits/midas_heritage_d_hd96_virtual_touring_console)** melalui protokol **OSC UDP** (Port default: `53000`).

---

## 📱 Unduh & Pasang APK (Siap Pakai)
Anda dapat langsung mengunduh file APK yang sudah dikompilasi tanpa perlu build dari source:
👉 **[Unduh HeritageRemote-debug.apk](./HeritageRemote-debug.apk)** (~5.3 MB)

### Cara Install ke HP/Tablet Android:
1. Unduh `HeritageRemote-debug.apk` ke HP Android Anda.
2. Tap file untuk menginstal (aktifkan izin *Install from Unknown Sources / Sumber tidak dikenal*).
3. Atau pasang via ADB jika terhubung ke PC:
   ```bash
   adb install -r HeritageRemote-debug.apk
   ```

---

## 🎛️ Fitur Utama
- **Vertical Touch Faders**: Kontrol fader vertikal real-time responsif (-60 dB s/d +10 dB).
- **144 Channel Mixing (18 Bank × 8 Channel)**:
  - Fader Level (`/ch/{id}/mix/fader`)
  - Channel Mute (`/ch/{id}/mix/mute`)
  - Channel Solo (`/ch/{id}/mix/solo`)
- **Master L/R Stereo Fader**: Kendali fader stereo utama mixer PC (`/main/fader`).
- **Talkback Toggle**: Toggle mikrofon talkback panggung (`/talkback/on`).
- **One-Tap Ping & Autodiscover**: Verifikasi koneksi OSC UDP ke PC mixer.

---

## 🚀 Cara Menghubungkan ke PC Mixer
1. Jalankan aplikasi mixer di PC: **[midas_heritage_d_hd96_virtual_touring_console](https://github.com/santimirana51-commits/midas_heritage_d_hd96_virtual_touring_console)**.
2. Di PC, buka menu **`OSC SERVER`** lalu klik **`START SERVER`** pada port `53000`.
3. Buka aplikasi **Heritage HD96 Remote** di HP Android Anda.
4. Masukkan alamat IP lokal PC mixer (contoh: `192.168.100.8`), lalu tekan tombol hijau **`PING`**.
5. Fader di HP Anda siap mengendalikan konsol mixer secara real-time!

---

## 🛠️ Kompilasi dari Source Code
Proyek ini dibangun menggunakan **Android Studio** / Gradle:
```bash
./gradlew assembleDebug
```
Output APK berada di `app/build/outputs/apk/debug/app-debug.apk`.
