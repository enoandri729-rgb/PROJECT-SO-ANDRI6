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
