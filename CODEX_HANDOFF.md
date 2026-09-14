# CODEX HANDOFF — Sistem Hitung Tukin dan Uang Makan Otomatis

## Tujuan
Lanjutkan pengembangan repository ini TANPA meminta user mengulang requirement. Fokus awal: rapikan dan finalkan frontend login/daftar sesuai desain yang sudah disetujui user, lalu pertahankan koneksi ke backend Supabase yang sudah aktif.

## Repository
- Repo: `ilhamronik-spec/PERHITUNGAN-OTOMATIS`
- Branch utama: `main`
- GitHub Pages: `https://ilhamronik-spec.github.io/PERHITUNGAN-OTOMATIS/`
- File frontend saat ini: `index.html`

## Backend yang SUDAH ADA
- Supabase project ref: `aplfcoksokhojieypsna`
- Supabase project: Portal Rekap Tunjangan Trial
- Edge API aktif: `https://aplfcoksokhojieypsna.supabase.co/functions/v1/portal-api`
- API mendukung action: `institutions`, `signup`, `login`, `reset`
- Jangan pernah menaruh service-role key di frontend.
- Login user memakai username + password. Backend mengubah username ke synthetic email internal; user tidak pernah melihat email.

## Requirement login yang SUDAH FIX
JANGAN ubah konsep/desain tanpa diminta user.

Nama aplikasi:
**Sistem Hitung Tukin dan Uang Makan Otomatis**

Identitas:
- Kementerian Agama Republik Indonesia
- Tema formal modern Kemenag
- Dominan putih + hijau tua + aksen emas
- `Created by Ilham Choiri`
- Lambang Kementerian Agama harus tampil benar dan lokal dari repo, jangan hotlink gambar yang rawan gagal.

Halaman awal hanya menampilkan login:
- Username
- Password
- Ingat saya
- Lupa Password?
- Masuk ke Sistem

Di bawah login hanya ada tombol/menu:
**Daftar Akun Baru**

Form pendaftaran TIDAK BOLEH tampil bersamaan dengan login. Form baru muncul sebagai modal/panel setelah tombol `Daftar Akun Baru` diklik.

Form pendaftaran hanya:
### Data Akun
- Username
- Password
- Satker / Instansi

### Biodata
- Nama Lengkap
- NIP (18 digit)
- No. Telepon

Tidak ada email di UI pendaftaran.

## Desain visual yang disetujui
User menyetujui layout referensi sebelumnya dengan karakter berikut:
- logo Kemenag di tengah atas
- judul utama di tengah
- card login tunggal di tengah
- nuansa putih terang
- tulisan/ornamen kiri atas `Ikhlas Melayani Umat`
- aksen teks formal kanan atas
- background gedung Kemenag samar di kiri dan siluet masjid samar di kanan
- ornamen gelombang hijau + emas di bawah
- card putih bersih, shadow lembut
- jangan berubah jadi tema biru, startup, atau layout split-screen
- jangan menambah feature card atau elemen baru yang tidak diminta

Masalah current live page:
- logo Kemenag tidak tampil karena memakai URL eksternal/hotlink
- ilustrasi gedung/background CSS sekarang tampak kasar dan tidak sama dengan referensi
- user menganggap tampilan live sekarang salah dibanding desain yang sudah disetujui

Prioritas pertama Codex:
1. Audit `index.html` saat ini.
2. Gunakan asset lokal untuk logo dan background/reference, bukan URL eksternal.
3. Rebuild login supaya visualnya sedekat mungkin dengan desain referensi yang sudah disetujui tanpa mengubah alur form.
4. Pastikan responsive desktop 1366x768 dan mobile.
5. Pastikan semua tombol login/register/reset tetap bekerja terhadap `portal-api`.
6. Commit langsung ke `main` setelah diuji karena GitHub Pages membaca branch `main` root.
7. Jangan menyentuh backend kecuali ada error integrasi yang nyata.

## Backend / akun
Aturan yang sudah diputuskan:
- User memilih satker dari daftar master, bukan free text.
- Akun pertama backend menjadi Super Admin trial.
- Akun berikutnya pending approval admin.
- Password tidak boleh diketahui admin dalam plaintext.
- Lupa password membuat permintaan reset untuk admin.

## Struktur produk setelah login
USER / SATKER:
- Dashboard
- Uang Makan
- Tukin
- Data Pegawai
- Riwayat Rekap
- Profil

ADMIN:
- Dashboard
- Statistik & Analitik
- Rekap Uang Makan
- Rekap Tukin
- Data Pegawai
- Permintaan Akun
- Reset Password
- Master Satker
- Pengguna
- Arsip Semua Rekap

Untuk sekarang jangan perlu menyelesaikan seluruh modul sekaligus. Setelah login page final, lanjut bertahap.

## Data Pegawai yang sudah disepakati
- Upload 1 atau lebih Excel.
- Header fleksibel, tidak wajib template kaku.
- NIP adalah merge key utama.
- Bisa menggabungkan biodata dari file 1 dan bank/rekening/SK dari file 2.
- Extra columns tidak boleh membuat import gagal.
- Jika field sama untuk NIP sama punya nilai berbeda, tandai konflik; jangan silent overwrite.
- Final master harus dapat disimpan dan diekspor kembali ke Excel.
- Field penting dapat mencakup NIP, Nama, Golongan, Jabatan, Kelas Jabatan/Grade, Gaji Pokok, Bank, No Rekening, Nama Rekening, NPWP, No SK, Satker, dll.

## Tukin / Grade
- Grade / kelas jabatan memang dibutuhkan untuk Tukin.
- Jika grade tersedia eksplisit di sumber, gunakan.
- Jika tidak tersedia, sistem dapat memakai pola lama fallback `nominal Tukin bruto -> grade` berdasarkan Master Tarif Tukin saat proses Tukin.
- Jangan menganggap grade boleh diabaikan sepenuhnya.

## Uang Makan / Tukin — prinsip
- Sistem adalah multi-tenant per satker.
- User hanya boleh melihat data satkernya sendiri.
- Super Admin dapat melihat seluruh satker.
- Hasil akhir nantinya menghasilkan Excel/TXT nyata, bukan simulasi UI.

## Instruksi kerja untuk Codex
- Jangan meminta user mengulang konteks di atas.
- Baca seluruh repo terlebih dahulu.
- Perlakukan `CODEX_HANDOFF.md` ini sebagai source of truth untuk requirement yang sudah fix.
- Jangan mengubah desain/flow yang sudah fix tanpa persetujuan user.
- Jika menemukan bug, perbaiki langsung dan jelaskan perubahan singkat.
- Prioritas saat ini: FIX frontend login di GitHub Pages dulu, baru lanjut modul berikutnya.
