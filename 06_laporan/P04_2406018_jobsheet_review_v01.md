## SIA-UC08 Input Nilai Mata Kuliah

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mata kuliah dari dosen pengampu tersimpan di sistem |
| Aktor utama | Dosen |
| Aktor pendukung | — |
| Pemicu | Dosen memilih fungsi input nilai untuk satu mata kuliah yang diampunya setelah masa perkuliahan berakhir |
| Prasyarat | Dosen telah terautentikasi dan memiliki hak akses sesuai peran. Dosen adalah pengampu mata kuliah yang dipilih. Masa perkuliahan mata kuliah tersebut telah berakhir |
| Pascakondisi berhasil | Nilai mata kuliah tersimpan dengan status belum dipublikasikan, sehingga belum tampil pada KHS |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan. Data nilai tidak berubah |
| Generalization | Tidak ada generalization use case pada SIA-UC08. Aktor Dosen adalah aktor khusus dari Civitas Akademika |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |
| Aturan bisnis/asumsi | Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini. Rentang nilai yang sah, mekanisme publikasi, dan asal daftar mahasiswa tidak ditentukan skenario (pertanyaan terbuka nomor 1, 2, dan 3) |

**Alur utama:**

| Langkah | Tindakan Dosen | Respons sistem |
|---|---|---|
| 1 | Memilih mata kuliah yang diampu dan membuka input nilai | Memeriksa bahwa Dosen adalah pengampu mata kuliah itu dan masa perkuliahan telah berakhir |
| 2 | — | Menampilkan daftar mahasiswa dan isian nilai (asumsi: asal daftar belum ditentukan tugas) |
| 3 | Mengisi nilai | Menampung isian |
| 4 | Mengirim nilai | Memeriksa bahwa setiap nilai berada dalam rentang yang sah |
| 5 | — | Jika semua nilai sah, menyimpan nilai dengan status belum dipublikasikan |
| 6 | Melihat konfirmasi | Menampilkan ringkasan nilai yang tersimpan |

## SIA-UC09 Lihat KHS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 dan SIA-R12 |
| Tujuan | Mahasiswa melihat KHS untuk semester yang nilainya sudah dipublikasikan |
| Aktor utama | Mahasiswa |
| Aktor pendukung | — |
| Pemicu | Mahasiswa memilih fungsi lihat KHS |
| Prasyarat | Mahasiswa telah terautentikasi dan memiliki hak akses sesuai peran |
| Pascakondisi berhasil | KHS ditampilkan dan hanya memuat nilai yang sudah dipublikasikan |
| Pascakondisi gagal | Tidak ada KHS yang ditampilkan |
| Generalization | Tidak ada generalization use case pada SIA-UC09 |
| Collaboration | SIA-CO02: Lihat KHS |
| Aturan bisnis/asumsi | KHS hanya menampilkan nilai yang sudah dipublikasikan. Nilai yang belum dipublikasikan tidak ditampilkan |

**Alur utama:**

| Langkah | Tindakan Mahasiswa | Respons sistem |
|---|---|---|
| 1 | Memilih fungsi lihat KHS | Menampilkan semester yang nilainya sudah dipublikasikan |
| 2 | Memilih satu semester | Menampilkan KHS semester itu dengan nilai yang sudah dipublikasikan saja |
