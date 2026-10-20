# SILAS — Premium Dashboard + Profil Direktur + Hapus Tahap

Pembaruan ini dibuat dari ZIP project SILAS yang kamu unggah. `supabase-config.js` sengaja tidak disertakan agar konfigurasi project milikmu tetap dipertahankan.

## Perubahan
- Dashboard mobile-first dengan card statistik lebih premium.
- Foto masjid menjadi latar hero dengan gerakan zoom lembut; foto santri tampil di kartu sambutan terpisah, bukan sebagai gambar kecil yang tidak cocok.
- Posisi logo Dayah dan placeholder logo Laundry dirapikan, termasuk tampilan HP.
- Kartu Direktur tampil di dashboard pada HP dan laptop. Urutannya: foto, nama, jabatan, lalu pesan/motto.
- Foto Direktur, nama, jabatan, dan pesan dapat diubah dari menu Pengaturan Laporan.
- Animasi ringan dan mendukung pengaturan `prefers-reduced-motion`.
- Tombol Hapus Tahap tersedia pada setiap tahap yang dibuat. Menghapus tahap juga menghapus semua catatan laundry pada tahap tersebut setelah konfirmasi.

## Cara menerapkan
1. Buat cadangan folder project SILAS yang sekarang.
2. Ekstrak ZIP pembaruan ini.
3. Salin `index.html`, `app.js`, `styles.css`, folder `assets`, dan folder `sql` ke folder project SILAS. Ganti file yang sama.
4. Jangan ganti `supabase-config.js`.
5. Di Supabase > SQL Editor, jalankan `sql/04_profil_direktur.sql`. Ini menambahkan kolom profil direktur ke tabel `pengaturan_laporan` yang sudah ada.
6. Jalankan `npx serve .` di terminal folder project dan uji login.

## Mengatur foto dan identitas Direktur
Buka menu **Pengaturan Laporan**. Di bagian **Profil Direktur di Dashboard**, unggah foto resmi direktur (PNG, JPG, atau WebP, maksimal 1 MB), isi nama, jabatan, dan pesan, lalu klik **Simpan pengaturan laporan**. Foto tidak akan tersimpan ke database sebelum tombol Simpan ditekan.

Karena foto disimpan sebagai data URL di `pengaturan_laporan`, gunakan file kecil maksimal 1 MB. Untuk aplikasi dengan banyak pengguna atau file besar, lebih baik pindahkan foto ke Supabase Storage.

## Hapus tahap
Pada menu **Periode & tahap**, setiap tahap yang dibuat memiliki tombol **Hapus tahap**. Sistem meminta konfirmasi karena semua catatan laundry pada tahap tersebut akan ikut dihapus. Unduh laporan terlebih dahulu jika catatan tersebut masih dibutuhkan.

## Catatan
- Kartu direktur menampilkan placeholder sampai foto resmi diunggah. Tidak ada foto orang palsu yang diperlakukan sebagai direktur sebenarnya.
- Uji di browser lokal dahulu, lalu commit/push ke GitHub agar GitHub Pages mendapatkan pembaruan.
- Jangan pernah menaruh Supabase secret/service_role key di frontend atau repository publik.
