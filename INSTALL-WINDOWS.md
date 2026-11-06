# Panduan pemasangan di Windows

Berlaku untuk **Windows 10 dan Windows 11 (64-bit)**.

---

## 1. Unduh installer

Buka halaman **[Releases](https://github.com/nashirfauzan/mosans-public/releases/latest)**
lalu unduh berkas:

```
MoSans-Setup-<versi>-win-x64.exe
```

Ukurannya sekitar **220 MB**. Contoh untuk versi 3.1.1:
`MoSans-Setup-3.1.1-win-x64.exe`.

Simpan ke folder **Downloads**.

---

## 2. Lewati peringatan SmartScreen

Saat installer dijalankan, Windows akan menampilkan layar biru
**"Windows protected your PC"**.

Ini **normal** dan **bukan tanda bahaya**. Penyebabnya: installer ini belum
ditandatangani dengan sertifikat digital berbayar, jadi Windows belum mengenal
penerbitnya.

Cara melewatinya:

1. Klik tulisan kecil **More info** di sisi kiri
2. Tombol **Run anyway** akan muncul di bawahnya
3. Klik **Run anyway**

> **Kenapa harus begini?** Sertifikat penandatangan (code signing) berbayar
> tahunan. Selama belum ada, setiap aplikasi baru akan melewati layar ini satu
> kali per berkas. Peringatannya hilang setelah kamu menekan *Run anyway*.

---

## 3. Jalankan pemasangan

Wizard akan terbuka:

1. **Folder tujuan** — biarkan apa adanya, atau pilih sendiri
2. Klik **Install**
3. Tunggu sampai selesai

Pemasangan bersifat **per pengguna** — **tidak perlu hak administrator**, dan
tidak mengubah apa pun untuk pengguna lain di komputer yang sama.

Aplikasi terpasang di:

```
%LOCALAPPDATA%\Programs\MoSans
```

---

## 4. Buka aplikasi

Cari **MoSans** di **Start Menu**, atau klik dua kali pintasannya di Desktop.

Saat pertama dibuka, akan muncul **layar aktivasi**. Ada dua pilihan:

**Mencoba dulu — uji coba 72 jam**

Klik **Mulai uji coba**. Semua fitur terbuka selama 3 hari. Uji coba dihitung
per perangkat dan tidak bisa diulang di perangkat yang sama.

**Sudah punya kunci lisensi**

Tempelkan kunci ke kolom yang tersedia, lalu klik **Aktifkan**:

```
MSNS-XXXXX-XXXXX-XXXXX-XXXXX
```

Butuh koneksi internet saat aktivasi. Setelah aktif, aplikasi tetap bekerja
tanpa internet.

---

## 5. Beri izin folder foto

Saat pertama memakai fitur pemantauan, MoSans akan meminta folder mana yang
mau dipantau. Pilih folder foto kamu, lalu biarkan aplikasi bekerja di latar
belakang.

---

## Kalau ada masalah

### Antivirus memblokir atau menghapus installer

Beberapa antivirus menandai installer yang belum ditandatangani sebagai
mencurigakan. Ini **positif palsu**.

Yang bisa dilakukan:

- Tambahkan pengecualian (exception) untuk berkas installernya di antivirus
- Kalau berkasnya sudah terhapus, unduh ulang lalu tambahkan pengecualian
  **sebelum** menjalankannya
- Cek juga folder karantina antivirus — berkasnya mungkin ada di sana

### "Windows protected your PC" muncul lagi

Itu terjadi kalau kamu mengunduh ulang berkasnya. Tekan **More info** →
**Run anyway** sekali lagi. Windows mengingat per berkas, bukan per aplikasi.

### Installer tidak mau jalan sama sekali

Pastikan:

- Windows kamu **64-bit** (Windows 10 atau 11)
- Berkasnya **selesai terunduh** — bandingkan ukurannya dengan yang tertulis di
  halaman Releases
- Coba klik kanan installer → **Run as administrator**

### Aplikasi terbuka tapi fiturnya terkunci

Berarti lisensinya belum aktif. Masukkan kunci lisensi, atau mulai uji coba
72 jam dari layar aktivasi.

---

## Cara menghapus

**Settings → Apps → Installed apps** → cari **MoSans** → **Uninstall**.

Di Windows 10 bisa juga lewat *Control Panel → Programs and Features*.

Data pengaturan tersimpan di `%APPDATA%\MoSans`. Hapus folder itu kalau ingin
membersihkan sisa datanya juga.

> ⚠️ Menghapus folder data **tidak** mengulang masa uji coba. Uji coba dicatat
> di server berdasarkan perangkat, bukan di komputermu.
