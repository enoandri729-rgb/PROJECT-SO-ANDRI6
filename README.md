# PROJECT-SO-ANDRI6
PROJECT: SIMULASI DATA RECOVERY SAAT
BLUESCREEN
📋 Deskripsi Project
Project ini mensimulasikan kondisi darurat dimana komputer mengalami bluescreen dan hanya
Command Prompt (CMD) yang bisa diakses. Mahasiswa akan belajar teknik menyelamatkan data
penting menggunakan command line.
🎯 Tujuan Pembelajaran
1. Memahami Command Line Interface (CLI)
• Perintah dasar CMD Windows
• Navigasi file system via command line
2. Manajemen File dengan CMD
• Copy file dan folder dengan struktur
• Verifikasi integritas data
3. Problem Solving
• Analisis situasi darurat
• Pengambilan keputusan cepat
4. Batch Scripting
• Automasi tugas repetitif
• Error handling dan logging

# Struktur Project
---
Total Data Simulasi:
10 Folder utama
30 SubFolder (3 per folder)
Desktop/
├── SimulasiDrive_D/ # Drive D (sumber data)
│ ├── Folder_1/
│ │ ├── SubFolder_A/
│ │ │ ├── dokumen_1_A.pdf
│ │ │ ├── data_1_A.csv
│ │ │ ├── catatan_1_A.txt
│ │ │ ├── laporan_1_A.docx
│ │ │ └── aplikasi_1_A.bat
│ │ ├── SubFolder_B/
│ │ │ └── (5 file berbagai format)
│ │ ├── SubFolder_C/
│ │ │ └── (6 file berbagai format)
│ │ ├── database_1.db
│ │ └── config_1.ini
│ ├── Folder_2/
│ │ └── (struktur sama, 3 subfolder)
│ └── ... (hingga Folder_10)
│
└── SimulasiDrive_C/ # Drive C (destinasi backup)
 └── DataRecovery_YYYYMMDD_HHMM/
 └── (hasil recovery)
 
 ---

 # Total Data Simulasi:

10 Folder utama
30 SubFolder (3 per folder)

~180 File berbagai format

# Format File:
.pdf - Dokumen
.csv - Data spreadsheet
.txt - Text file
.docx - Word document
.bat - Batch script
.py - Python script
.db - Database file
.ini - Configuration file
# 🚀 Cara Menjalankan Project

# CATATAN PENTING:

Project ini TIDAK memerlukan download dari internet. Mahasiswa membuat file batch (.bat) sendiri dari nol atau menggunakan kode contoh yang sudah disediakan.

# OPSI A: Buat Script Sendiri dari Nol (Pembelajaran Mendalam)

Mahasiswa menulis sendiri batch script dengan cara:

# 1. Buka Notepad
# 2. Tulis kode batch sesuai kebutuhan:

• Buat folder dengan mkdir
Isi file dengan echo dan >
• Copy data dengan xcopy

# 3. Save dengan ekstensi .bat
# 4. Test dan debug sendiri

# Kelebihan: 
Belajar lebih mendalam tentang batch scripting

# OPSI B: Gunakan Kode Contoh (Lebih Cepat)

Jika dosen menyediakan kode contoh (seperti artifact di atas), mahasiswa bisa:

# Cara 1 - File Terpisah:

# 1. Buat file setup:

• Buka Notepad
• Lihat artifact "Simulasi Data Recovery - Setup Environment"
• Ketik ulang atau copy-paste kode tersebut
• Save As → 1_setup_simulasi.bat (pilih "All Files")
• Simpan di Desktop

# 2. Buat file recovery:
• Notepad baru
• Lihat artifact "Solusi Data Recovery - Script CMD"
• Ketik ulang atau copy-paste kode tersebut
• Save As → 2_recovery_data.bat
• Simpan di Desktop

# 3. Jalankan:

• Double-click 1_setup_simulasi.bat → tunggu selesai
• Double-click 2_recovery_data.bat → lihat hasil

# Cara 2 - File All-in-One (PALING MUDAH):

# 1. Buat file:
• Buka Notepad
• Lihat artifact "All-in-One Batch Script"
• Ketik ulang atau copy-paste kode tersebut
• Save As → simulator.bat

# 2. Jalankan & pilih menu:
• Double-click simulator.bat
• Ketik 1 → Enter (setup)
• Ketik 2 → Enter (recovery)

# OPSI C: Manual via CMD (Advanced)

Mahasiswa yang sudah paham bisa langsung ketik command di CMD:

---
cmd

mkdir D:\FolderPenting

xcopy D:\Data C:\Backup\ /E /H /C /I /Y

---

# Verifikasi Hasil:
✅ Cek folder SimulasiDrive_D di Desktop (sumber)
✅ Cek folder SimulasiDrive_C di Desktop (backup)
✅ Baca file recovery_log.txt

# 🔧 Perintah CMD Penting

# Navigasi Dasar
---
cmd

dir # List isi folder
cd NamaFolder # Masuk ke folder
cd .. # Kembali ke folder parent
cd \ # Ke root drive
D: # Pindah ke drive D
C: # Pindah ke drive C

---

# Manajemen file 

---
cmd

copy source dest # Copy 1 file
xcopy source dest /E # Copy folder + subfolder
move source dest # Pindah file
del namafile # Hapus file
mkdir NamaFolder # Buat folder
rmdir NamaFolder # Hapus folder

---

# informasi sistem 

---
cmd

dir /s # List semua file recursive
dir /b # List nama file saja
tree # Tampilkan struktur folder
echo %date% %time% # Tampilkan tanggal & waktu

---

# 💡 Skenario Real Bluescreen
# Situasi Darurat:

---
❌ Windows tidak bisa boot normal
❌ Safe Mode gagal
❌ GUI tidak accessible
✅ Command Prompt (CMD) masih bisa diakses via Recovery Environment

---

# Langkah Penyelamatan Data Real:

# 1. Boot ke Recovery Environment
Restart 3x paksa (tekan tombol power)
Pilih "Advanced Options"
Pilih "Command Prompt"
# 2. Identifikasi Drive

---
cmd 

diskpart
list volume
exit

---

(Cari drive D: dan C:)

# 3. Copy Data Penting

---
cmd

xcopy D:\FolderPenting C:\Backup\ /E /H /C /I /Y

---

# 4. Verifikasi

---
cmd

dir C:\Backup /s
 
---

# 5. Parameter Penting xcopy:

• [/E] - Copy semua subfolder termasuk yang kosong

• [/H] - Copy file hidden & system

• [/C] - Lanjutkan meski ada error

• [/I] - Asumsikan destination adalah folder

• [/Y] - Overwrite tanpa konfirmasi


# 📊 Tugas Mahasiswa

# Tugas 1: Basic Recovery (Wajib)

✅ Jalankan kedua script dan dokumentasikan:

• Screenshot proses setup

• Screenshot proses recovery

• Isi file recovery_log.txt

• Total waktu yang dibutuhkan

# Tugas 2: Modifikasi Script (Intermediate)

📝 Modifikasi 2_recovery_data.bat untuk:

• Backup hanya file tertentu (misal: hanya .pdf dan .docx)

• Tambahkan progress bar atau counter

• Buat verifikasi checksum/file size

• Compress hasil backup ke .zip

# Tugas 3: Skenario Advanced (Challenge)

🔥 Buat script baru untuk:

• Selective Backup: User bisa pilih folder mana yang di-backup

• Incremental Backup: Hanya backup file yang berubah

• Scheduled Backup: Backup otomatis tiap X menit

• Email Notification: Kirim notifikasi setelah backup selesai

# Tugas 4: Analisis & Dokumentasi

📄 Buat laporan mencakup:

# 1. Analisis Masalah:

• Penyebab umum bluescreen
• Kenapa CMD masih bisa diakses?

# 2. Solusi Alternatif:

• Tool recovery data lainnya
• Cloud backup sebagai preventif

# 3. Best Practice:

• Strategi backup 3-2-1 rule
• Automasi backup rutin

# 4. Kesimpulan:

• Pembelajaran dari simulasi
• Aplikasi di dunia nyata

# 🛡 Tips Keamanan Data

Preventif (Sebelum Bluescreen):

1. ✅ Backup rutin (harian/mingguan)
2. ✅ Gunakan cloud storage (Google Drive, OneDrive)
3. ✅ External HDD/SSD backup
4. ✅ System restore point aktif
5. ✅ Update Windows & driver rutin

# Reaktif (Saat Bluescreen):

1. 🔴 Jangan panic!
2. 🔴 Catat kode error bluescreen
3. 🔴 Boot ke Safe Mode dulu
4. 🔴 Jika gagal, gunakan CMD Recovery
5. 🔴 Backup data penting segera
   
# 3-2-1 Backup Rule:

• 3 copy data (original + 2 backup)

• 2 media berbeda (HDD + Cloud)

• 1 offsite backup (Cloud/eksternal)

# 🔍 Troubleshooting

Error: "Access Denied"

---
cmd

#Jalankan CMD sebagai Administrator

#Atau gunakan parameter /G

xcopy D:\Data C:\Backup /E /G

---

Error: "Insufficient Disk Space"

---
cmd

#Cek space tersedia
dir C:\ 

#Compress file saat copy (jika Windows support)

compact /c C:\Backup\*.*

---

# Error: "File in Use"

---

cmd

#Skip file yang sedang digunakan

xcopy D:\Data C:\Backup /E /C

---

# Proses Terlalu Lambat

---
cmd

#Copy dengan multi-thread (Windows 10+)

robocopy D:\Data C:\Backup /E /MT:16

---

# 📚 Referensi Command Line

Dokumentasi Lengkap:

xcopy /? - Help xcopy

robocopy /? - Help robocopy (advanced)

help - List semua perintah CMD

# Alternatif Tool (Advanced):

---
cmd

# Robocopy (lebih powerful dari xcopy)

robocopy D:\Data C:\Backup /E /Z /MT:8 /LOG:backup.log

#Parameter robocopy:

#/Z - Copy dengan mode restart

#/MT - Multi-threaded (lebih cepat)

#/LOG - Simpan log detail
