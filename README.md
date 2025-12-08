# PROYEK-SO-ANDRI6
# 1. Tugas 1: Basic Recovery (Wajib) 💾
Tugas ini mensimulasikan kondisi darurat di mana Anda harus menyelamatkan data penting menggunakan Command Prompt (CMD). Anda akan menjalankan dua batch script (.bat) untuk mengatur lingkungan dan melakukan pemulihan data dasar.
# A. Persiapan Lingkungan (Setup)
 * Buat File Setup: Buat batch script bernama 1_setup_simulasi.bat di Desktop. Skrip ini harus berisi perintah untuk membuat struktur folder simulasi, yaitu SimulasiDrive_D (sumber data) dan SimulasiDrive_C (destinasi backup).
 * Jalankan Setup: Double-click 1_setup_simulasi.bat. Pastikan struktur folder (10 folder utama, 30 subfolder, ~180 file berbagai format) terbuat sempurna di Desktop Anda.
 * Dokumentasi: Ambil Screenshot proses setup.
# B. Proses Pemulihan Data (Recovery)
 * Buat File Recovery: Buat batch script bernama 2_recovery_data.bat di Desktop. Skrip ini harus menggunakan perintah copy tingkat lanjut seperti xcopy atau robocopy untuk menyalin data dari SimulasiDrive_D ke folder backup di SimulasiDrive_C.
   * Gunakan parameter penting xcopy seperti /E (salin subfolder), /H (salin hidden & system file), dan /C (lanjutkan meski ada error).
   * Pastikan skrip mencatat semua aktivitas ke dalam file recovery_log.txt.
 * Jalankan Recovery: Double-click 2_recovery_data.bat.
 * Dokumentasi:
   * Ambil Screenshot proses recovery.
   * Catat Total waktu yang dibutuhkan.
# C. Verifikasi dan Pelaporan
 * Verifikasi: Cek folder SimulasiDrive_C (destinasi backup) dan bandingkan dengan SimulasiDrive_D (sumber) untuk memastikan data tersalin lengkap dan terverifikasi.
 * Log: Baca dan lampirkan isi file recovery_log.txt.
# 2. Tugas 2: Modifikasi Script (Intermediate) 🛠️
Modifikasi file 2_recovery_data.bat untuk meningkatkan fungsionalitasnya.
| Modifikasi yang Diperlukan | Strategi Implementasi |
|---|---|
| Backup hanya file tertentu | Gunakan xcopy atau robocopy dengan wildcard *.pdf atau *.docx untuk menyaring file. |
| Tambahkan progress bar/counter | Gunakan ROBOCOPY karena ia lebih informatif dan mendukung multi-threaded copy (/MT:16) yang mempercepat proses. |
| Buat verifikasi checksum/file size | Gunakan perintah dir /s untuk membandingkan jumlah dan ukuran file, atau pertimbangkan robocopy yang memiliki fitur verifikasi integritas. |
| Compress hasil backup ke .zip | Karena CMD standar tidak mendukung kompresi .zip, opsi termudah adalah menggunakan compact /c untuk mengompresi file di level NTFS (jika didukung). |
# 3. Tugas 3: Skenario Advanced (Challenge) 🧠
Buat script baru untuk menangani skenario pemulihan data yang lebih kompleks.
 * Selective Backup: Buat menu menggunakan perintah SET /P untuk menerima input pengguna dan struktur IF/GOTO untuk menjalankan backup hanya pada folder yang dipilih oleh pengguna.
 * Incremental Backup: Gunakan perintah ROBOCOPY dengan parameter yang hanya menyalin file yang baru atau berubah sejak backup terakhir (Robocopy secara bawaan melakukan incremental copy yang efisien).
 * Scheduled Backup: Skrip batch yang dibuat dapat diintegrasikan dengan Windows Task Scheduler agar berjalan secara otomatis pada interval waktu tertentu (misalnya, setiap X menit).
 * Email Notification: Memerlukan pemanggilan bahasa scripting yang lebih kuat seperti PowerShell (menggunakan cmdlet Send-MailMessage) dari dalam skrip batch untuk mengirim notifikasi setelah proses backup selesai.
# 4. Tugas 4: Analisis & Dokumentasi 📝
Buat laporan akhir yang mencakup analisis mendalam dan kesimpulan dari proyek.
# A. Analisis Masalah
 * Penyebab Bluescreen: Jelaskan penyebab umum layar biru (misalnya, driver yang rusak, masalah hardware, atau corrupted system files).
 * Akses CMD: Jelaskan mengapa Command Prompt masih dapat diakses (biasanya melalui Windows Recovery Environment meskipun GUI Windows gagal boot).
# B. Solusi Alternatif
 * Ulas tool pemulihan data lain yang tersedia (misalnya, tool GUI, atau tool CMD yang lebih kuat seperti Robocopy).
 * Jelaskan peran Cloud backup sebagai tindakan pencegahan (preventif).
# C. Best Practice
 * Jelaskan dan diskusikan 3-2-1 Backup Rule (3 copy data, 2 media berbeda, 1 offsite backup).
 * Tekankan pentingnya automasi backup rutin dan system restore point.
# D. Kesimpulan
 * Rangkum pembelajaran yang didapat dari simulasi.
 * Jelaskan aplikasi skill command line ini di dunia nyata sebagai seorang IT Professional.
 * 
