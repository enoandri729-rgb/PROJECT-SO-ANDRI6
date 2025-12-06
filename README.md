# 💻 Tugas Mahasiswa (Wajib)
# Tugas 1: Basic Recovery (Wajib)
Tugas ini melibatkan menjalankan dua script dasar yang disediakan (atau dibuat) dan mendokumentasikannya.

# Langkah-Langkah:
 * Buat Script Setup
   * Buat file 1_setup_simulasi.bat (atau gunakan artifact yang disediakan) yang berisi perintah untuk membuat struktur folder simulasi (10 folder utama, 30 subfolder) di lokasi sumber, misalnya SimulasiDrive_D di Desktop, sesuai dengan struktur proyek yang diberikan. Gunakan perintah mkdir dan copy atau xcopy untuk membuat folder dan menyalin file-file contoh.
  
 * Buat Script Recovery
   * Buat file 2_recovery_data.bat (atau gunakan artifact yang disediakan) yang berisi perintah xcopy atau robocopy untuk menyalin data dari sumber (SimulasiDrive_D) ke lokasi backup tujuan (SimulasiDrive_C/DataRecovery_YYYYMMDD_HHMM).
   * Perintah dasar xcopy yang disarankan:
     xcopy D:\FolderPenting C:\Backup /E /H /C /I /Y

     (Asumsikan D: adalah drive sumber simulasi dan C:\Backup adalah tujuan backup).
 * Jalankan Script
   * Jalankan 1_setup_simulasi.bat terlebih dahulu.
   * Jalankan 2_recovery_data.bat. Catat waktu mulai dan waktu selesai proses recovery.
 * Dokumentasi dan Verifikasi
   * Screenshot proses setup (min. 5) dan proses recovery (min. 5).
   * Buat/Isi file recovery_log.txt yang mencatat:
     * Waktu total yang dibutuhkan untuk recovery.
     * Detail setup dan hasil recovery (termasuk jumlah file yang disalin).
   * Verifikasi data di folder tujuan: cek jumlah folder/subfolder dan file yang disalin.
Tugas 2: Modifikasi Script (Intermediate)
Modifikasi script recovery (2_recovery_data.bat) dengan menambahkan fitur-fitur berikut:
 * Backup Terpilih: Modifikasi perintah copy agar hanya mem-backup file tertentu (misalnya, hanya .pdf dan .docx). Anda mungkin perlu menyesuaikan argumen xcopy atau menggunakan tool lain seperti robocopy yang lebih kuat.
 * Progress Bar/Counter: Tambahkan mekanisme sederhana untuk menampilkan progress bar atau counter jumlah file yang telah di-copy (ini mungkin sulit dengan batch script murni, gunakan logika logging atau echo sederhana jika perlu).
 * Verifikasi Checksum/File Size: Tambahkan langkah untuk membandingkan ukuran total file di sumber dan tujuan untuk verifikasi integritas data.
 * Compress hasil backup ke .zip: Setelah copy selesai, gunakan tool kompresi command-line (jika tersedia di recovery environment simulasi) untuk mengarsipkan hasil backup.
Tugas 💡 Tugas 3: Skenario Advanced (Challenge)
Buat script baru untuk menangani skenario lanjutan:
 * Selective Backup: Script meminta input dari user untuk memilih folder mana saja yang akan di-backup.
 * Incremental Backup: Script hanya menyalin file yang berubah sejak backup terakhir (gunakan robocopy dengan parameter yang sesuai, seperti /XO, /XC, /XN, /L).
 * Scheduled Backup: Buat mekanisme untuk menjalankan backup secara otomatis setiap X menit (di lingkungan Windows normal, ini menggunakan Task Scheduler; dalam konteks simulasi, jelaskan konsepnya).
 * Email Notification: Tambahkan fungsi untuk mengirim notifikasi email setelah backup selesai (gunakan tool CLI eksternal jika memungkinkan, seperti Blat, atau jelaskan konsepnya).
Tugas 📝 Tugas 4: Analisis & Dokumentasi
Buat laporan yang mencakup poin-poin berikut:
1. Analisis Masalah
 * Penyebab umum bluescreen (misalnya, driver rusak, hardware gagal, registry korup).
 * Mengapa CMD masih bisa diakses? (Karena Anda berada di Windows Recovery Environment atau WinRE, yang merupakan lingkungan minimal bootable terpisah dari Windows utama).
2. Solusi Alternatif
 * Tool recovery data lain (misalnya, Recuva, TestDisk, MiniTool Partition Wizard).
 * Cloud backup sebagai langkah preventif (misalnya, Google Drive, OneDrive, Dropbox).
3. Best Practice
 * Strategi backup 3-2-1 Rule (jelaskan: 3 salinan, 2 media berbeda, 1 offsite backup). * Automasi backup rutin.
4. Kesimpulan
 * Pelajari tentang simulasi.
 * Penerapan di dunia nyata (bagaimana CLI digunakan oleh profesional IT saat data recovery).
📌 Penilaian Project
Pastikan setiap aspek berikut tercakup dalam laporan dan file yang dikumpulkan:
| Aspek | Bobot | Kriteria |
|---|---|---|
| Setup Simulasi | 15% | Berhasil membuat struktur folder. |
| Recovery Data | 25% | Data tersalin lengkap & terverifikasi. |
| Dokumentasi | 20% | Screenshot, log, analisis lengkap. |
| Modifikasi Script | 20% | Improvisasi & kreativitas. |
| Laporan Akhir | 20% | Analisis mendalam & kesimpulan. |
🔑 Tips Keamanan Data (Ringkasan)
Preventif (Sebelum Bluescreen):
 * Backup rutin (harian/mingguan).
 * Gunakan cloud storage (Google Drive, OneDrive).
 * External HDD/SSD backup.
 * System restore point aktif.
 * Update Windows & driver rutin.
Reaktif (Saat Bluescreen):
 * Jangan panik!
 * Catat kode error bluescreen.
 * Boot ke Safe Mode dulu.
 * Jika gagal, gunakan CMD Recovery.
 * Backup data penting segera.
🛠️ Panduan Command Line
Perintah Penting (Dasar)
| Kategori | Perintah | Deskripsi |
|---|---|---|
| Navigasi | dir | List isi folder. |
|  | cd NamaFolder | Masuk ke folder. |
|  | cd .. | Kembali ke folder parent. |
| Manajemen File | copy source dest | Copy 1 file. |
|  | xcopy source dest /E | Copy folder + subfolder. |
|  | move source dest | Pindah file. |
|  | mkdir NamaFolder | Buat folder. |
| Identifikasi Drive | diskpart | Masuk ke tool manajemen disk. |
|  | list volume | List semua drive. |
Troubleshooting (Penting untuk Recovery)
| Error | Solusi |
|---|---|
| Access Denied | Jalankan CMD sebagai Administrator. |
| Insufficient Disk Space | Cek disk space tersedia (dir C:\) atau kompres file (compact /c C:\Backup\*.*). |
| File in Use | Lewati file yang sedang digunakan (gunakan parameter xcopy /C atau robocopy /XF). |
| Proses Terlalu Lambat | Gunakan tool multi-thread seperti robocopy /MT:16 (16 thread) untuk mempercepat proses. |
Apakah Anda ingin saya memberikan contoh script batch dasar untuk 1_setup_simulasi.bat atau 2_recovery_data.bat?
