# Laporan UTS Web Software Tools

**Nama:** [Muhammad Enda Mora]
**Nomor Induk Mahasiswa:** [12523034]
**Kelas:** [TI-B]
**Tanggal:** 13 November 2026

## A. Bukti pemeriksaan masalah

| Masalah | Alat yang digunakan | Bukti pemeriksaan | Perkiraan penyebab | Perbaikan | Hasil setelah perbaikan |
|---|---|---|---|---|---|
| Produk | Chrome DevTools (Network dan Console), pemeriksaan kode | Permintaan GET ke `/api/barang` menghasilkan status 404. Console menampilkan pesan gagal memuat produk. | Alamat API yang dipanggil pada app.js tidak sesuai dengan alamat yang disediakan server.mjs. | Mengubah alamat fetch dari `/api/barang` menjadi `/api/products`. | Produk berhasil ditampilkan sebanyak 4 produk. Network menunjukkan status 200 OK. |
| Tombol keranjang | Pemeriksaan kode dan pengujian langsung melalui browser | Tombol terlihat pada halaman, tetapi ketika diklik produk tidak masuk ke keranjang. | Nama class pada tombol adalah `add-button`, sedangkan JavaScript mencari elemen dengan class `add-to-cart`. | Mengubah selector JavaScript menjadi `.add-button`. | Tombol berhasil menambahkan produk ke keranjang dan jumlah barang berubah. |
| Total belanja | Pemeriksaan kode dan pengujian otomatis Node.js | Dua pengujian gagal. Hasil aktual Rp75.000 seharusnya Rp150.000, serta Rp225.000 seharusnya Rp600.000. | Fungsi calculateTotal hanya menjumlahkan harga barang tanpa memperhitungkan quantity. | Mengubah perhitungan menjadi `item.price * item.quantity` dan menghapus variabel discount yang tidak digunakan. | Perhitungan sesuai jumlah barang. Simulasi pembelian 2 mouse dan 3 keyboard menghasilkan total Rp600.000. |

## B. Hasil pengujian

- Jumlah pengujian sebelum perbaikan: 5 berhasil dan 2 gagal.
- Jumlah pengujian berhasil setelah perbaikan: 7 berhasil dan 0 gagal.
- Catatan perubahan pada fungsi yang diperiksa:
  - Perbaikan alamat API untuk mengambil data produk.
  - Perbaikan selector tombol tambah ke keranjang.
  - Perbaikan fungsi calculateTotal agar menghitung harga berdasarkan jumlah barang.
  - Seluruh pengujian bawaan pada folder tests dipertahankan tanpa perubahan.

## C. Kualitas kode

- Temuan sebelum perbaikan:
  - Pemeriksaan lint tidak menemukan masalah.
  - Format check menemukan ketidaksesuaian format pada public/app.js dan src/cart.js.
  - Quality check juga menemukan masalah format yang sama.
- Perbaikan yang dilakukan:
  - Menggunakan Biome formatter untuk merapikan format kode pada public/app.js dan src/cart.js.
- Hasil pemeriksaan ulang:
  - Lint: berhasil.
  - Format check: berhasil.
  - Quality check: berhasil.
  - Tidak ditemukan error pada pemeriksaan ulang.

## D. Git

- Branch: master.
- Ringkasan commit:
  - `1c4268c` — chore: initial exam project.
  - `71c4fd0` — fix: repair shop behavior.
- Hasil pemeriksaan `git status`:
  - Pada saat pemeriksaan setelah commit kedua, working tree dalam kondisi bersih.
  - Seluruh perubahan perbaikan sudah tersimpan dalam riwayat Git.

## E. Pemakaian kecerdasan buatan (jika digunakan)

- Nama alat: ChatGPT.
- Pertanyaan/instruksi yang diberikan:
  Meminta bantuan untuk menganalisis project, mengidentifikasi penyebab tiga masalah pada aplikasi, memberikan panduan perbaikan kode, serta menjelaskan langkah pemeriksaan menggunakan browser, terminal, Git, dan Biome.
- Bagian jawaban yang diterapkan:
  Penyesuaian alamat API, perbaikan selector tombol keranjang, perbaikan perhitungan total belanja, serta perapian format kode menggunakan Biome.
- Cara memeriksa apakah saran tersebut benar:
  Memeriksa Network dan Console pada Chrome DevTools, menguji fungsi aplikasi melalui browser, menjalankan tujuh pengujian otomatis, serta menjalankan pemeriksaan lint, format, dan quality menggunakan Biome.

## F. Refleksi singkat

Dari pengerjaan UTS ini saya belajar bahwa memperbaiki aplikasi tidak cukup hanya dengan mengganti kode. Saya perlu memahami penyebab masalah melalui bukti pemeriksaan terlebih dahulu. Saya juga belajar menggunakan Chrome DevTools, menjalankan pengujian otomatis, memeriksa kualitas kode dengan Biome, serta mencatat perubahan menggunakan Git. Dengan proses tersebut, saya lebih memahami bagaimana menemukan dan memperbaiki kesalahan pada sebuah aplikasi web.