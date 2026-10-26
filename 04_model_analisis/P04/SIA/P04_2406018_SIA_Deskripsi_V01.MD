<!-- Tabel 4.6 Kebutuhan tugas Pertemuan 4 -->
| ID | Kebutuhan tugas |
| --- | --- |
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik. |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya. |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan. |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa. |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. |
| SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS. |

<!-- Batas dan asumsi -->
• Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02
(Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap
mempunyai identitas berbeda.
• Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
• Kalender akademik pada tugas ini adalah agenda resmi institusi (awal
semester, batas KRS, masa ujian, dan sejenisnya); jangan
menyamakannya dengan jadwal kuliah pada Pertemuan 2.
• Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai
yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan
tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan.
• Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data
akademik aktif. Ketentuan ini fiktif untuk latihan.
• Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari
Pertemuan 3. Pembayaran dan perancangan basis data berada di luar
tugas ini.

<!-- Skenario -->
Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang
dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang
diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu
Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin
Akademik mengelola data mahasiswa: menambah data mahasiswa baru,
mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case
utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh
collaboration yang bersesuaian.

<!-- Aktor -->

| Aktor | Kedudukan | Tujuan terhadap sistem |
|---|---|---|
| Civitas Akademika | Umum (general), baru pada Pertemuan 4 | Peran umum bagi pengguna kampus. Melihat kalender akademik dan mewariskan fungsi itu kepada Mahasiswa dan Dosen |
| Mahasiswa | Khusus dari Civitas Akademika, tetap dari Pertemuan 3 | Melihat kalender akademik (diwarisi), melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pengajuan, dan melihat KHS (asosiasi sendiri) |
| Dosen | Khusus dari Civitas Akademika, baru pada Pertemuan 4 | Melihat kalender akademik (diwarisi) dan menginput nilai mata kuliah yang diampunya |
| Admin Akademik | Tetap dari Pertemuan 2 dan 3 | Mengelola jadwal kuliah, memvalidasi KRS, dan mengelola data mahasiswa |
| Dosen Wali | Tetap dari Pertemuan 3 | Memproses persetujuan atau penolakan KRS |

Kelima aktor digambar pada diagram kumulatif. Aktor baru adalah Civitas Akademika dan Dosen. Mahasiswa, Admin Akademik, dan Dosen Wali tetap seperti Pertemuan 3.

<!-- use case -->

| ID | Nama use case | Aktor terkait | Sumber kebutuhan | Tanda | Peran dalam model |
|---|---|---|---|---|---|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | SIA-R01 | Tetap (P2) | Fungsi utama Mahasiswa |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R02 | Tetap (P2) | Fungsi utama Admin Akademik |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 | Tetap (P3) | Fungsi utama Mahasiswa. Menyertakan SIA-UC04 |
| SIA-UC04 | Validasi KRS | Admin Akademik | SIA-R04 | Tetap (P3) | Perilaku yang disertakan SIA-UC03 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | SIA-R05 | Tetap (P3) | Tambahan bersyarat pada SIA-UC03 melalui «extend» |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R06 | Tetap (P3) | Fungsi utama Dosen Wali |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika (diwarisi Mahasiswa dan Dosen) | SIA-R07 | Baru (P4) | Fungsi aktor umum |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen | SIA-R08, SIA-R12 | Baru (P4) | Fungsi utama Dosen. Direalisasikan SIA-CO01 |
| SIA-UC09 | Lihat KHS | Mahasiswa | SIA-R09, SIA-R12 | Baru (P4) | Fungsi utama Mahasiswa. Direalisasikan SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik | SIA-R10 | Baru (P4) | Use case UMUM bagi SIA-UC11, SIA-UC12, SIA-UC13 |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik (melalui SIA-UC10) | SIA-R11 | Baru (P4) | Use case KHUSUS dari SIA-UC10 |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik (melalui SIA-UC10) | SIA-R11 | Baru (P4) | Use case KHUSUS dari SIA-UC10 |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik (melalui SIA-UC10) | SIA-R11 | Baru (P4) | Use case KHUSUS dari SIA-UC10 |

<!-- Generalization use case -->

Keputusan: SIA-UC11, SIA-UC12, dan SIA-UC13 adalah bentuk khusus dari SIA-UC10 Kelola Data Mahasiswa.

Alasan: ketiganya sama-sama mengelola data mahasiswa (perilaku umum), tetapi hasil akhirnya berbeda.

| Use case khusus | Perilaku pembeda (satu kalimat) |
|---|---|
| SIA-UC11 Tambah Data Mahasiswa | Menghasilkan data mahasiswa baru yang tersimpan |
| SIA-UC12 Ubah Data Mahasiswa | Menghasilkan data mahasiswa yang berubah |
| SIA-UC13 Hapus Data Mahasiswa | Menghasilkan data mahasiswa yang terhapus, dengan syarat mahasiswa tidak memiliki data akademik aktif |

Aturan penggambaran yang dipenuhi:

- Panah segitiga kosong menunjuk SIA-UC10 (umum), digambar dari tiap use case khusus.
- Admin Akademik hanya dihubungkan ke SIA-UC10, bukan ke ketiga use case khusus.
- SIA-UC10 tetap bermakna sebagai konsep pengelolaan, dan use case khusus tidak sekadar mengganti nama.
- Satu pasang use case hanya memakai satu jenis hubungan. Pasangan SIA-UC10 dan use case khususnya tidak diberi include atau extend.
- Use case lain tidak dijadikan bentuk khusus SIA-UC10. Misalnya SIA-UC02 Kelola Jadwal Kuliah mengelola jadwal, bukan data mahasiswa, sehingga bukan bentuk khusus walaupun namanya mirip.

<!-- Collaboration dan realization -->

| ID | Nama collaboration (sama dengan nama use case) | Use case yang direalisasikan |
|---|---|---|
| SIA-CO01 | Input Nilai Mata Kuliah | SIA-UC08: Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS | SIA-UC09: Lihat KHS |

Alasan: kedua use case itu adalah use case utama pada potongan model ini (SIA-R12), sehingga realisasinya ditunjukkan secara eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini.

Aturan penggambaran yang dipenuhi:

- Collaboration digambar sebagai elips garis putus-putus dan diberi ID SIA-CO, bukan ID use case.
- Relasi realization: garis putus-putus dengan ujung segitiga kosong, dari collaboration menuju use case, tanpa label.
- Collaboration tidak dihubungkan langsung ke aktor. Aktor berinteraksi dengan use case.
- Satu collaboration merealisasikan tepat satu use case.
- Isi collaboration (peran elemen dan pertukaran pesan) tidak ditulis di sini. Itu menjadi bahan diagram interaksi pada pertemuan berikutnya.