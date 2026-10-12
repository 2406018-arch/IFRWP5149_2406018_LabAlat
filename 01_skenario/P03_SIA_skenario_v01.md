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