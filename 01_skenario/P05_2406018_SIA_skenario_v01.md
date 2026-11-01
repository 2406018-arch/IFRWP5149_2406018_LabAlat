## Tabel 5.15 Skenario Use Case SIA-UC07 Lihat Kalender Akademik

| | |
|---|---|
| **Nama use case** | SIA-UC07 Lihat Kalender Akademik |
| **Aktor** | Civitas Akademika (berlaku untuk Mahasiswa dan Dosen) |
| **Tujuan** | Civitas Akademika dapat mengetahui jadwal kegiatan akademik pada periode yang dipilih |
| **Deskripsi** | Civitas Akademika membuka fungsi kalender akademik, memilih periode akademik, dan melihat kalender akademik periode tersebut |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Civitas Akademika membuka fungsi Lihat Kalender Akademik | |
| | 2. Sistem menampilkan daftar tahun akademik dan semester |
| 3. Civitas Akademika memilih tahun akademik dan semester | |
| | 4. Sistem menampilkan kalender akademik periode tersebut beserta tanggal kegiatan akademiknya |
| **Skenario Alternative** | |
| 5. Kalender akademik belum tersedia untuk periode yang dipilih (cabang dari langkah 4) | |
| | 6. Sistem menampilkan pesan kalender akademik belum tersedia pada periode tersebut |
| **Skenario Akhir** | Use case selesai jika kalender akademik periode yang dipilih ditampilkan; jika kalender belum tersedia, use case selesai dengan pesan tersebut. |

## Tabel 5.16 Skenario Use Case SIA-UC08 Input Nilai Mata Kuliah

| | |
|---|---|
| **Nama use case** | SIA-UC08 Input Nilai Mata Kuliah |
| **Aktor** | Dosen (dosen pengampu mata kuliah) |
| **Tujuan** | Nilai mahasiswa pada mata kuliah yang diampu tersimpan |
| **Deskripsi** | Dosen pengampu memilih mata kuliah yang diampu, mengisi nilai setiap mahasiswa dalam rentang yang sah, dan menyimpan nilai. Prasyarat: dosen adalah pengampu mata kuliah tersebut |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Dosen membuka fungsi Input Nilai Mata Kuliah | |
| | 2. Sistem memeriksa dosen sebagai pengampu dan menampilkan daftar mata kuliah yang diampu |
| 3. Dosen memilih mata kuliah yang akan dinilai | |
| | 4. Sistem menampilkan daftar mahasiswa peserta mata kuliah beserta isian nilai |
| 5. Dosen mengisi nilai setiap mahasiswa | |
| | 6. Sistem memeriksa nilai berada dalam rentang yang sah, yaitu 0 sampai 100 |
| 7. Dosen menyimpan nilai | |
| | 8. Sistem menyimpan nilai dan menampilkan konfirmasi penyimpanan nilai |
| **Skenario Alternative** | |
| 9. Dosen bukan pengampu mata kuliah apa pun (cabang dari langkah 2) | |
| | 10. Sistem menolak akses dan menampilkan pesan bahwa nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut |
| 11. Nilai berada di luar rentang yang sah (cabang dari langkah 6) | |
| | 12. Sistem menolak penyimpanan dan menampilkan pesan nilai harus berada pada rentang 0 sampai 100 |
| **Skenario Akhir** | Use case selesai jika nilai mahasiswa tersimpan; jika dosen bukan pengampu atau nilai di luar rentang yang sah, nilai tidak tersimpan. |

## Tabel 5.17 Skenario Use Case SIA-UC09 Lihat KHS

| | |
|---|---|
| **Nama use case** | SIA-UC09 Lihat KHS |
| **Aktor** | Mahasiswa |
| **Tujuan** | Mahasiswa dapat mengetahui nilai mata kuliah yang sudah dipublikasikan pada semester yang dipilih |
| **Deskripsi** | Mahasiswa membuka fungsi KHS, memilih semester, dan melihat KHS yang hanya memuat nilai yang sudah dipublikasikan |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Mahasiswa membuka fungsi Lihat KHS | |
| | 2. Sistem menampilkan daftar semester yang diikuti mahasiswa |
| 3. Mahasiswa memilih semester | |
| | 4. Sistem menampilkan KHS semester tersebut berisi mata kuliah, SKS, dan nilai yang sudah dipublikasikan |
| **Skenario Alternative** | |
| 5. Tidak ada nilai yang sudah dipublikasikan pada semester yang dipilih (cabang dari langkah 4) | |
| | 6. Sistem menampilkan pesan nilai semester tersebut belum dipublikasikan |
| **Skenario Akhir** | Use case selesai jika KHS dengan nilai yang sudah dipublikasikan ditampilkan; jika belum ada nilai yang dipublikasikan, use case selesai dengan pesan tersebut dan tidak ada nilai yang ditampilkan. |

Keterangan tabel: use case ini direalisasikan oleh collaboration SIA-CO02 Lihat KHS. Collaboration tersebut tidak mempunyai langkah kegiatan pada tabel ini. Nilai yang belum dipublikasikan tidak pernah ditampilkan.

## Tabel 5.18 Skenario Use Case SIA-UC10 Kelola Data Mahasiswa

| | |
|---|---|
| **Nama use case** | SIA-UC10 Kelola Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa terkelola melalui satu fungsi pengelolaan bersama |
| **Deskripsi** | Admin Akademik membuka fungsi pengelolaan data mahasiswa, memilih bentuk pengelolaan, dan menyimpan perubahan. Bentuk tambah, ubah, dan hapus dijabarkan pada tabel khususnya masing-masing |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Kelola Data Mahasiswa | |
| | 2. Sistem menampilkan daftar data mahasiswa |
| 3. Admin Akademik memilih bentuk pengelolaan, yaitu tambah, ubah, atau hapus | |
| | 4. Sistem menampilkan formulir sesuai bentuk pengelolaan yang dipilih |
| 5. Admin Akademik mengisi atau mengonfirmasi data mahasiswa | |
| | 6. Sistem memeriksa kelengkapan dan keabsahan data |
| 7. Admin Akademik menyimpan perubahan | |
| | 8. Sistem menyimpan perubahan dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 9. Data tidak lengkap atau tidak sah (cabang dari langkah 6) | |
| | 10. Sistem menolak penyimpanan dan menampilkan pesan kesalahan data |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak lengkap atau tidak sah, perubahan tidak tersimpan. |

Keterangan tabel: use case umum (generalization use case). Tabel ini memuat perilaku bersama yang dirujuk oleh SIA-UC11 Tambah Data Mahasiswa, SIA-UC12 Ubah Data Mahasiswa, dan SIA-UC13 Hapus Data Mahasiswa.

## Tabel 5.19 Skenario Use Case SIA-UC11 Tambah Data Mahasiswa

| | |
|---|---|
| **Nama use case** | SIA-UC11 Tambah Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa baru tersimpan sebagai bentuk khusus dari pengelolaan data mahasiswa |
| **Deskripsi** | Admin Akademik mengisi data mahasiswa baru dan menyimpan data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10 |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Tambah Data Mahasiswa | |
| | 2. Sistem menampilkan formulir data mahasiswa baru |
| 3. Admin Akademik mengisi NIM, nama, dan program studi mahasiswa baru | |
| | 4. Sistem memeriksa kelengkapan data dan keunikan NIM |
| 5. Admin Akademik menyimpan data | |
| | 6. Sistem menyimpan data mahasiswa baru dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data tidak lengkap (cabang dari langkah 4) | |
| | 8. Sistem menolak penyimpanan dan meminta Admin Akademik melengkapi data |
| 9. NIM sudah terdaftar (cabang dari langkah 4) | |
| | 10. Sistem menolak penyimpanan dan menampilkan pesan NIM sudah terdaftar |
| **Skenario Akhir** | Use case selesai jika data mahasiswa baru tersimpan; jika data tidak lengkap atau NIM sudah terdaftar, data tidak tersimpan. |

Keterangan tabel: use case khusus dari SIA-UC10 Kelola Data Mahasiswa. Perilaku pembeda: data mahasiswa baru tersimpan. Langkah bersama mengikuti Tabel skenario SIA-UC10.

## Tabel 5.20 Skenario Use Case SIA-UC12 Ubah Data Mahasiswa

| | |
|---|---|
| **Nama use case** | SIA-UC12 Ubah Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa berubah sebagai bentuk khusus dari pengelolaan data mahasiswa |
| **Deskripsi** | Admin Akademik memilih data mahasiswa, mengubah datanya, dan menyimpan perubahan; langkah bersama mengikuti Tabel skenario SIA-UC10 |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan diubah | |
| | 2. Sistem menampilkan data mahasiswa saat ini |
| 3. Admin Akademik mengubah data mahasiswa | |
| | 4. Sistem memeriksa kelengkapan dan keabsahan perubahan data |
| 5. Admin Akademik menyimpan perubahan | |
| | 6. Sistem menyimpan data yang diubah dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data mahasiswa tidak ditemukan (cabang dari langkah 2) | |
| | 8. Sistem menampilkan pesan data mahasiswa tidak ditemukan |
| 9. Perubahan data tidak lengkap atau tidak sah (cabang dari langkah 4) | |
| | 10. Sistem menolak penyimpanan dan menampilkan pesan kesalahan data |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak ditemukan atau perubahan tidak lengkap atau tidak sah, perubahan tidak tersimpan. |

Keterangan tabel: use case khusus dari SIA-UC10 Kelola Data Mahasiswa. Perilaku pembeda: data mahasiswa berubah. Langkah bersama mengikuti Tabel skenario SIA-UC10.

## Tabel 5.21 Skenario Use Case SIA-UC13 Hapus Data Mahasiswa

| | |
|---|---|
| **Nama use case** | SIA-UC13 Hapus Data Mahasiswa |
| **Aktor** | Admin Akademik |
| **Tujuan** | Data mahasiswa terhapus sebagai bentuk khusus dari pengelolaan data mahasiswa |
| **Deskripsi** | Admin Akademik memilih data mahasiswa, mengonfirmasi penghapusan, dan sistem menghapus data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10 |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan dihapus | |
| | 2. Sistem memeriksa mahasiswa tidak memiliki data akademik aktif |
| 3. Admin Akademik mengonfirmasi penghapusan | |
| | 4. Sistem menghapus data mahasiswa dan menampilkan konfirmasi penghapusan |
| **Skenario Alternative** | |
| 5. Mahasiswa memiliki data akademik aktif (cabang dari langkah 2) | |
| | 6. Sistem menolak penghapusan dan menampilkan pesan mahasiswa masih memiliki data akademik aktif |
| **Skenario Akhir** | Use case selesai jika data mahasiswa terhapus; jika mahasiswa memiliki data akademik aktif, data tidak terhapus. |

Keterangan tabel: use case khusus dari SIA-UC10 Kelola Data Mahasiswa. Perilaku pembeda: data mahasiswa terhapus, dengan syarat mahasiswa tidak memiliki data akademik aktif. Langkah bersama mengikuti Tabel skenario SIA-UC10.
