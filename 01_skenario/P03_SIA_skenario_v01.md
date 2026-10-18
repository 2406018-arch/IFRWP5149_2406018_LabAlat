## Skenario tugas:
Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap
pengajuan menjalankan validasi KRS yang memeriksa kelengkapan,
prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil,
sistem menyimpan pengajuan berstatus menunggu persetujuan dosen
wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih
mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS
dan memberikan catatan keputusan.

## Kebutuhan Tugas
   ID  |Kebutuhan tugas
SIA-R01| Mahasiswa dapat melihat jadwal kuliah
SIA-R02| Admin akademik dapat mengelola jadwal kuliah
SIA-R03| Mahasiswa dapat mengajukan KRS
SIA-R04| Sistem memvalidasi KRS sebagai bagian pengajuan
SIA-R05| Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan
SIA-R06| Dosen wali dapat memproses persetujuan atau penolakan KRS

## Batas dan asumsi:
• Pengguna telah terautentikasi.
• Data mata kuliah, prasyarat, dan jadwal tersedia.
• Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
• Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
• KRS tersimpan belum berarti disetujui.
• Pembayaran, pengisian nilai, dan implementasi basis data berada di luar
tugas.

## Aktor
|Aktor         | Tujuan terhadap sistem
|Mahasiswa     | Melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pada konfirmasi pengajuan
|Admin Akademik| Mengelola jadwal kuliah, Memvalidasi KRS
|Dosen Wali    | Memproses persetujuan atau penolakan KRS

## Katalog use case
| ID | Nama use case | Aktor terkait | Sumber kebutuhan | Peran dalam model |
| SIA-UC01 | Lihat jadwal kuliah | Mahasiswa | SIA-R01 | Fungsi utama mahasiswa |
| SIA-UC02 | Kelola jadwal kuliah | Admin akademik | SIA-R02 | Fungsi utama admin akademik |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 | Fungsi utama mahasiswa |
| SIA-UC04 | Validasi KRS | Admin akademik | SIA-R04 | Perilaku yang disertakan UC03 |
| SIA-UC05 | Unduh bukti pengajuan KRS | Mahasiswa | SIA-R05 | Tambahan bersyarat pada UC03 |
| SIA-UC06 | Proses keputusan KRS | Dosen wali | SIA-R06 | Fungsi utama dosen wali |

## Tentukan Include
| Sumber | Hubungan | Tujuan | Alasan |
| SIA-UC03 Ajukan KRS | «include» | SIA-UC04 Validasi KRS | Setiap pengajuan menjalankan validasi yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal (SIA-R04). Pemeriksaan selalu dilakukan pada tahap pengajuan dan hasilnya menentukan apakah pengajuan tersimpan. Hasil gagal tidak berarti validasinya opsional |

- **Sumber kebutuhan:** SIA-R03 dan SIA-R04.
- **Tujuan relasi:** memastikan pengajuan lengkap, memenuhi prasyarat, dan bebas benturan jadwal sebelum disimpan.
- **Letak pemanggilan:** langkah 3 alur utama SIA-UC03 (sistem menjalankan SIA-UC04).
- **Hasil perilaku yang disertakan:** berhasil atau gagal, dikembalikan ke SIA-UC03.
- **Bukan include (prasyarat):** pengguna terautentikasi serta data mata kuliah, prasyarat, dan jadwal tersedia. Itu kondisi sebelum use case berjalan, sehingga tidak diberi relasi include (misalnya Login).
- Kelengkapan, prasyarat mata kuliah, dan benturan jadwal adalah tiga pemeriksaan di dalam SIA-UC04, bukan use case tersendiri.

## Tentukan extend
| Use case dasar | Use case tambahan | Kondisi | Extension point |
| SIA-UC03 Ajukan KRS | SIA-UC05 Unduh bukti pengajuan KRS | [mahasiswa memilih mengunduh bukti] | Konfirmasi penyimpanan |

- **Arah panah:** dari SIA-UC05 (tambahan) ke SIA-UC03 (dasar). Extension point dimiliki SIA-UC03.
- **Syarat kondisi terjangkau:** extension point tercapai hanya jika validasi berhasil dan pengajuan sudah tersimpan (langkah 5 alur utama SIA-UC03).
- **Perilaku tambahan:** sistem menyiapkan bukti pengajuan yang dapat diunduh.
- **Alasan:** pengajuan tetap berhasil tersimpan tanpa unduh bukti (SIA-R05 dan batas tugas). SIA-UC03 tetap bermakna tanpa SIA-UC05.
- Validasi gagal tidak dijadikan extend. Itu alur alternatif SIA-UC03.

## Susun Deskripsi
### SIA-UC03 Ajukan KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC03 — Ajukan KRS |
| Sumber kebutuhan | SIA-R03, SIA-R04 |
| Tujuan | Menghasilkan pengajuan KRS yang tersimpan |
| Aktor utama | Mahasiswa |
| Aktor pendukung | — |
| Pemicu | Mahasiswa memilih fungsi pengajuan KRS |
| Prasyarat | Mahasiswa terautentikasi. Data mata kuliah, prasyarat, dan jadwal tersedia |
| Pascakondisi berhasil | Pengajuan tersimpan berstatus menunggu persetujuan dosen wali. KRS belum disetujui |
| Pascakondisi gagal | Tidak ada pengajuan yang berhasil tersimpan |
| Include | SIA-UC04 Validasi KRS (langkah 3) |
| Extension point | Konfirmasi penyimpanan, pada langkah 5 |
| Extend | SIA-UC05 jika [mahasiswa memilih mengunduh bukti] |
| Aturan bisnis/asumsi | Validasi dijalankan pada setiap pengajuan. Unduh bukti bukan syarat keberhasilan. KRS tersimpan belum berarti disetujui |

Alur utama:

| Langkah | Tindakan mahasiswa | Respons sistem |
|---|---|---|
| 1 | Membuka pengajuan KRS | Menampilkan daftar mata kuliah |
| 2 | Memilih mata kuliah | Menampung pilihan |
| 3 | Mengirim pengajuan | Menjalankan SIA-UC04 |
| 4 | — | Jika validasi berhasil, menyimpan pengajuan berstatus menunggu persetujuan dosen wali |
| 5 | Melihat konfirmasi | Menampilkan konfirmasi penyimpanan; mencapai extension point |
| 6 | Mengakhiri pengajuan | Menutup proses pengajuan |

Alur alternatif/pengecualian:

- **A1 — validasi gagal (langkah 3 sampai 4):** SIA-UC04 mengembalikan hasil gagal. Sistem memberi tahu mahasiswa bahwa pengajuan belum berhasil tersimpan. Langkah 4 sampai 6 tidak dijalankan, tidak ada konfirmasi penyimpanan, dan SIA-UC05 tidak tersedia. Use case berakhir dengan pascakondisi gagal.
- **E1 — unduh bukti (langkah 5):** jika [mahasiswa memilih mengunduh bukti], SIA-UC05 dijalankan, lalu alur kembali ke langkah 6. Jika tidak dipilih, alur langsung ke langkah 6 dan hasilnya tetap pascakondisi berhasil.

### SIA-UC04 Validasi KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC04 — Validasi KRS |
| Sumber kebutuhan | SIA-R04 |
| Tujuan | Menentukan apakah pengajuan layak disimpan |
| Aktor utama | Admin akademik (sesuai tabel aktor). Validasi dijalankan sistem saat SIA-UC03 |
| Aktor pendukung | — |
| Pemicu | SIA-UC03 menjalankan validasi pada langkah 3 |
| Prasyarat | Pilihan mata kuliah diterima dari SIA-UC03. Data mata kuliah, prasyarat, dan jadwal tersedia |
| Pascakondisi berhasil | Hasil berhasil dikembalikan ke SIA-UC03 |
| Pascakondisi gagal | Hasil gagal dikembalikan ke SIA-UC03. Validasi sendiri tidak menyimpan pengajuan |
| Aturan bisnis/asumsi | Ketiga pemeriksaan selalu dilakukan. Hanya SIA-UC03 yang menyimpan pengajuan, dan hanya jika hasilnya berhasil |

### SIA-UC05 Unduh bukti pengajuan KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC05 — Unduh bukti pengajuan KRS |
| Sumber kebutuhan | SIA-R05 |
| Tujuan | Mahasiswa memperoleh bukti pengajuan yang baru tersimpan |
| Aktor utama | Mahasiswa |
| Aktor pendukung | — |
| Pemicu | Mahasiswa memilih mengunduh bukti pada konfirmasi penyimpanan |
| Prasyarat | Validasi berhasil, pengajuan tersimpan, dan konfirmasi penyimpanan sedang ditampilkan |
| Pascakondisi berhasil | Mahasiswa memiliki bukti pengajuan |
| Pascakondisi gagal | Bukti tidak diperoleh. Status pengajuan tidak berubah (tetap menunggu persetujuan dosen wali) |
| Use case dasar | SIA-UC03, melalui extension point Konfirmasi penyimpanan |
| Kondisi extend | [mahasiswa memilih mengunduh bukti] |
| Aturan bisnis/asumsi | Unduh bukti tidak menjadi syarat keberhasilan pengajuan. Isi dan format bukti tidak ditentukan skenario |

Alur utama:

| Langkah | Tindakan mahasiswa | Respons sistem |
|---|---|---|
| 1 | Memilih mengunduh bukti | Menyiapkan bukti pengajuan |
| 2 | Menerima bukti | Menyediakan unduhan, lalu kembali ke SIA-UC03 langkah 6 |

### SIA-UC06 Proses keputusan KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC06 — Proses keputusan KRS |
| Sumber kebutuhan | SIA-R06 |
| Tujuan | Memutuskan menyetujui atau menolak KRS yang diajukan mahasiswa |
| Aktor utama | Dosen wali |
| Aktor pendukung | — |
| Pemicu | Dosen wali memilih pengajuan KRS yang menunggu persetujuan |
| Prasyarat | Dosen wali terautentikasi. Ada KRS tersimpan berstatus menunggu persetujuan dosen wali (hasil SIA-UC03 yang berhasil, hanya terhubung lewat data pengajuan) |
| Pascakondisi berhasil | Keputusan tersimpan beserta catatan keputusan. Status pengajuan disetujui atau ditolak |
| Pascakondisi gagal | Tidak ada keputusan tersimpan. Status pengajuan tetap menunggu persetujuan |
| Aturan bisnis/asumsi | Catatan keputusan diberikan pada persetujuan maupun penolakan. Tindak lanjut setelah penolakan tidak diatur skenario dan berada di luar model |

Alur utama (persetujuan):

| Langkah | Tindakan dosen wali | Respons sistem |
|---|---|---|
| 1 | Membuka daftar pengajuan menunggu persetujuan | Menampilkan daftar pengajuan |
| 2 | Memilih satu pengajuan | Menampilkan isi pengajuan |
| 3 | Memilih menyetujui dan memberikan catatan keputusan | Menyimpan keputusan dan mengubah status menjadi disetujui |
| 4 | Melihat hasil | Menampilkan keputusan yang tersimpan |
