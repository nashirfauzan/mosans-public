# Panduan pemasangan di macOS

Berlaku untuk **macOS 10.15 (Catalina)** dan yang lebih baru.

---

## 1. Tentukan jenis Mac kamu

Ini menentukan berkas mana yang harus diunduh.

Klik **logo Apple** di pojok kiri atas → **About This Mac**, lalu lihat:

| Yang tertulis | Jenis Mac | Berkas yang dipakai |
|---|---|---|
| **Chip: Apple M1 / M2 / M3 / M4** | Apple Silicon | `MoSans-<versi>-mac-arm64.dmg` |
| **Processor: Intel** | Intel | `MoSans-<versi>-mac-x64.dmg` |

**Belum yakin?** Buka **Terminal** (⇧⌘U di Finder → Utilities → Terminal) lalu
jalankan:

```bash
uname -m
```

- keluar `arm64` → pakai `mac-arm64`
- keluar `x86_64` → pakai `mac-x64`

> ⚠️ **Jangan tertukar.** Berkas `arm64` hanya untuk Apple Silicon, dan `x64`
> hanya untuk Intel. Kalau salah pilih, aplikasinya tidak akan terbuka.
> Ukuran keduanya berbeda (~220 MB vs ~247 MB), jadi bisa dibedakan dari ukuran.

---

## 2. Unduh

Buka halaman **[Releases](https://github.com/nashirfauzan/mosans-public/releases/latest)**
lalu unduh berkas sesuai tabel di atas. Simpan ke folder **Downloads**.

---

## 3. Pasang

1. Klik dua kali berkas `.dmg` yang sudah diunduh
2. Sebuah jendela akan terbuka, berisi ikon **MoSans** dan folder **Applications**
3. **Seret** ikon MoSans ke folder Applications
4. Tutup jendelanya
5. Keluarkan (eject) DMG-nya: klik ikon ⏏ di sebelah namanya pada sidebar Finder

---

## 4. Buka pertama kali — lewati Gatekeeper

Saat pertama dibuka, macOS akan menolak dengan pesan:

> **"MoSans" cannot be opened because the developer cannot be verified.**

Ini **normal** dan **bukan tanda bahaya**. Penyebabnya: aplikasi ini belum
ditandatangani dan dinotarisasi oleh Apple, karena keduanya butuh akun
Apple Developer berbayar (99 USD/tahun).

### Cara 1 — lewat Finder (disarankan)

1. Buka **Applications** di Finder
2. **Klik kanan** (atau Control-klik) ikon **MoSans**
3. Pilih **Open** dari menu yang muncul
4. Akan muncul dialog peringatan lagi → klik **Open** sekali lagi

Setelah sekali dibuka dengan cara ini, macOS mengingatnya. Seterusnya cukup klik
dua kali seperti biasa.

### Cara 2 — lewat Terminal

Kalau Cara 1 tidak berhasil (biasanya karena macOS versi lama), jalankan:

```bash
xattr -cr /Applications/MoSans.app
```

Perintah itu menghapus penanda "karantina" yang macOS pasang pada setiap berkas
unduhan. Setelah itu aplikasi bisa dibuka normal.

### Cara 3 — lewat System Settings

1. Coba buka aplikasinya sekali (akan ditolak)
2. Buka **System Settings → Privacy & Security**
3. Di bagian bawah akan ada tulisan tentang **MoSans** yang diblokir
4. Klik **Open Anyway** → masukkan sandi Mac kamu

---

## 5. Aktivasi

Saat pertama dibuka, muncul **layar aktivasi**. Ada dua pilihan:

**Mencoba dulu — uji coba 72 jam**

Klik **Mulai uji coba**. Semua fitur terbuka selama 3 hari. Dihitung per
perangkat dan tidak bisa diulang di perangkat yang sama.

**Sudah punya kunci lisensi**

Tempelkan kunci ke kolom yang tersedia, lalu klik **Aktifkan**:

```
MSNS-XXXXX-XXXXX-XXXXX-XXXXX
```

Butuh koneksi internet saat aktivasi.

---

## 6. Izin yang akan diminta macOS

Saat memakai fitur tertentu, macOS akan meminta izin. Ini wajar — aplikasi
memang perlu akses itu supaya bisa bekerja.

| Fitur | Izin yang diminta |
|---|---|
| Memantau folder foto | **Files and Folders** — pilih folder yang mau dipantau |
| Membaca kartu SD / kamera | **Removable Volumes** |
| Notifikasi selesai unggah | **Notifications** |

Kalau pernah menolak izinnya tanpa sengaja, bisa diubah di
**System Settings → Privacy & Security**.

---

## Kalau ada masalah

### "App is damaged and can't be opened"

Pesan ini menyesatkan — aplikasinya tidak rusak. Penyebabnya Gatekeeper.

Jalankan lewat Terminal:

```bash
xattr -cr /Applications/MoSans.app
```

Lalu buka lagi. Kalau masih gagal:

```bash
sudo xattr -rd com.apple.quarantine /Applications/MoSans.app
```

### "You do not have permission to open the application"

Seret MoSans **keluar** dari folder Applications (misalnya ke Desktop), lalu
seret masuk lagi. Cara ini memperbarui izin berkasnya.

### Aplikasi langsung tertutup sendiri setelah dibuka

Kemungkinan besar **berkasnya salah arch**:

- Mac Apple Silicon tapi yang diunduh `mac-x64` → unduh `mac-arm64`
- Mac Intel tapi yang diunduh `mac-arm64` → unduh `mac-x64`

Cek dengan `uname -m` seperti di langkah 1.

### macOS-nya terlalu lama

Aplikasi ini butuh **macOS 10.15 (Catalina)** atau lebih baru. Cek di
**logo Apple → About This Mac**.

---

## Cara menghapus

Seret **MoSans** dari folder **Applications** ke **Trash**.

Untuk membersihkan sisa data pengaturannya juga, jalankan:

```bash
rm -rf ~/Library/Application\ Support/MoSans
```

> ⚠️ Menghapus data itu **tidak** mengulang masa uji coba. Uji coba dicatat di
> server berdasarkan perangkat, bukan di Mac kamu.
