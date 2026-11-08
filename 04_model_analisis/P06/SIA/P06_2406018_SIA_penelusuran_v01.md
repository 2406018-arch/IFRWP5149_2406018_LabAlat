## Penelusuran Activity SIA: Input Nilai Mata Kuliah sampai Lihat KHS

Berkas diagram: `P06_2406018_SIA_activity_v01.drawio` dan `P06_2406018_SIA_activity_v01.png`.
Tabel skenario sumber: Tabel 5.16 SIA-UC08 Input Nilai Mata Kuliah dan Tabel 5.17 SIA-UC09 Lihat KHS (`01_skenario/P05_2406018_SIA_skenario_v01.md`).

| No | Action / unsur pada diagram | Swimlane | Sumber pada tabel skenario P05 | Keterangan |
|---|---|---|---|---|
| 1 | Initial node | Dosen | UC08 langkah 1 (awal alur) | Satu initial node |
| 2 | Memasukkan nilai mata kuliah | Dosen | UC08 langkah 3, 5, dan 7 (memilih mata kuliah, mengisi nilai setiap mahasiswa, menyimpan nilai) | Dilipat menjadi satu action mengikuti Langkah 2 jobsheet |
| 3 | Menyimpan nilai dan menampilkan konfirmasi penyimpanan nilai | Sistem | UC08 langkah 8 | Nama sama dengan bunyi langkah sumber |
| 4 | Decision Nilai sudah lengkap? dengan guard [lengkap] dan [belum lengkap] | Sistem | Tidak ada pada tabel UC08 | Unsur ketentuan tugas (C.3.a dan Langkah 3) |
| 5 | Melengkapi nilai mata kuliah yang belum lengkap | Dosen | Mengacu UC08 langkah 5 (Dosen mengisi nilai) | Cabang [belum lengkap], kembali melalui merge sebelum pengesahan |
| 6 | Merge | Sistem | - | Menggabungkan cabang [lengkap] dan hasil melengkapi nilai |
| 7 | Memeriksa dan mengesahkan nilai | Admin Akademik | Tidak ada pada tabel UC08 | Unsur ketentuan tugas (Langkah 2). Terkait pertanyaan terbuka mekanisme publikasi pada deskripsi SIA-UC08 Pertemuan 4 |
| 8 | Menyiapkan publikasi hasil studi | Sistem | Tidak ada pada tabel UC08 atau UC09 | Unsur ketentuan tugas (Langkah 4). Prasyarat UC09: hanya nilai yang sudah dipublikasikan yang tampil |
| 9 | Fork | Sistem | - | Membagi alur menjadi dua proses paralel |
| 10 | Menerbitkan KHS pada portal akademik | Sistem | Tidak ada langkah tersendiri pada UC09; mendasari UC09 langkah 4 (KHS memuat nilai yang sudah dipublikasikan) | Cabang paralel 1 |
| 11 | Mengirim pemberitahuan hasil studi kepada mahasiswa | Sistem | Tidak ada pada tabel UC09 | Unsur ketentuan tugas. Cabang paralel 2 |
| 12 | Join | Sistem | - | Menyatukan kedua proses paralel sebelum Mahasiswa melihat KHS |
| 13 | Melihat KHS | Mahasiswa | UC09 langkah 1, 3, dan 4 (membuka fungsi, memilih semester, KHS ditampilkan) | Dilipat menjadi satu action mengikuti Langkah 4 jobsheet |
| 14 | Activity final node | Mahasiswa | UC09 Skenario Akhir (KHS dengan nilai yang sudah dipublikasikan ditampilkan) | Satu activity final node |

Catatan:

- Action nomor 4, 5, 7, 8, 10, dan 11 berasal dari ketentuan tugas jobsheet, bukan dari tabel skenario UC08 dan UC09 yang disusun pada Pertemuan 5. Keenamnya ditandai di sini agar tidak dianggap berasal dari tabel skenario.
- Cabang Alternative UC08 (langkah 9 sampai 12: bukan pengampu, nilai di luar rentang 0 sampai 100) dan UC09 (langkah 5 sampai 6: belum ada nilai dipublikasikan) tidak digambar, karena tugas membatasi diagram pada unsur wajib C.3.a.
- Collaboration SIA-CO02 Lihat KHS tidak digambar sebagai action maupun swimlane.
- Diagram SIA Pertemuan 4 hanya menjadi acuan nama aktor dan tidak diubah.
