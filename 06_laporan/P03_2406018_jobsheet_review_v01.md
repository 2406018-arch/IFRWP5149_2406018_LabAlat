Ketiga situasi konsisten antara diagram dan deskripsi.

**a. Validasi berhasil, mahasiswa tidak mengunduh bukti**
- Diagram: Ajukan KRS menyertakan Validasi KRS. Kondisi extend [mahasiswa memilih mengunduh bukti] tidak terpenuhi, jadi Unduh bukti tidak berjalan.
- Deskripsi: Ajukan KRS alur utama langkah 1 sampai 6 tanpa E1. Pengajuan tersimpan berstatus menunggu persetujuan dosen wali.
- Hasil: konsisten.

**b. Validasi gagal**
- Diagram: Validasi KRS gagal, jadi tidak ada penyimpanan. Extension point tidak tercapai, sehingga Unduh bukti tidak mungkin berjalan.
- Deskripsi: A1 pada Ajukan KRS (langkah 3 sampai 4) dan A1 pada Validasi KRS. Tidak ada pengajuan tersimpan dan Unduh bukti tidak tersedia.
- Hasil: konsisten.

**c. Validasi berhasil, mahasiswa memilih mengunduh bukti**
- Diagram: Unduh bukti memperluas Ajukan KRS di extension point Konfirmasi penyimpanan karena kondisinya terpenuhi.
- Deskripsi: E1 pada langkah 5 menjalankan Unduh bukti, lalu kembali ke langkah 6. Pengajuan tetap menunggu persetujuan.
- Hasil: konsisten.

**Kesimpulan**
- Situasi a dan c berakhir sama: pengajuan tersimpan berstatus menunggu persetujuan dosen wali. Unduh bukti tidak menentukan keberhasilan pengajuan.
- Pada situasi b, Unduh bukti tidak bisa berjalan karena extension point berada setelah penyimpanan, sedangkan validasi gagal berhenti sebelum itu.
- Nama use case di diagram sama dengan katalog. Include dirujuk di langkah 3, extension point di langkah 5, dan titik kembali di langkah 6, sama di diagram dan deskripsi.

**Keterbatasan**
- Diagram tidak menggambarkan kegagalan validasi. Hal itu hanya ada di alur alternatif deskripsi, sesuai ketentuan jobsheet.
- Extension point hanya tertulis di catatan, tidak di dalam elips Ajukan KRS.