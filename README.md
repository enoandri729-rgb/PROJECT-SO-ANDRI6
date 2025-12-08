# PROJECT-SO-ANDRI^

Ini adalah panduan lengkap Anda, mulai dari Tugas 1 hingga Tugas 4.

-----

## 🎯 Ringkasan Proyek

Tujuan proyek ini adalah mensimulasikan pemulihan data penting menggunakan Command Line Interface (CMD) saat sistem mengalami *bluescreen* dan hanya bisa diakses melalui Recovery Environment.

### Struktur Data yang Perlu Dibuat

| Nama Folder | Peran |
| :--- | :--- |
| **`SimulasiDrive_D`** | Sumber data (Drive yang rusak) |
| **`SimulasiDrive_C`** | Destinasi *backup* (Drive yang aman) |

-----

## 1\. Tugas Wajib: Basic Recovery (Tugas 1)

Tugas pertama Anda adalah membuat lingkungan simulasi dan melakukan *recovery* dasar.

### 📝 A. Script Setup (`1_setup_simulasi.bat`)

Script ini membuat struktur folder `SimulasiDrive_D` (10 Folder Utama, 30 Subfolder, \~180 File).

**Tindakan:** Simpan kode di bawah ini sebagai **`1_setup_simulasi.bat`** di Desktop Anda, lalu **jalankan**.

```batch
@echo off
setlocal enabledelayedexpansion
set "SourceDir=%USERPROFILE%\Desktop\SimulasiDrive_D"
set "FileCount=0"

echo.
echo === SIMULASI DATA RECOVERY - SETUP ===
echo.
if exist "%SourceDir%" rmdir /s /q "%SourceDir%"
mkdir "%SourceDir%"

echo Membuat 10 Folder Utama dan Subfoldernya...
for /L %%i in (1,1,10) do (
    set "FolderMain=Folder_%%i"
    call :CreateFolder "%SourceDir%\!FolderMain!"
)

echo.
echo Setup Selesai. Total File Dibuat: !FileCount!
pause
goto :eof

:CreateFolder
set "CurrentDir=%~1"
mkdir "%CurrentDir%"

for %%j in (A B C) do (
    set "SubDir=%CurrentDir%\SubFolder_%%j"
    mkdir "!SubDir!"
    
    rem Membuat 9 file per subfolder
    echo Dokumen Penting - SubFolder %%j > "!SubDir!\dokumen_%%j.pdf"
    echo Laporan Bulanan - SubFolder %%j > "!SubDir!\laporan_%%j.docx"
    echo Catatan Teks Biasa > "!SubDir!\catatan_%%j.txt"
    echo Header1,Header2,Header3 > "!SubDir!\data_%%j.csv"
    echo Simpan Data Database Ini! > "!SubDir!\database_%%j.db"
    echo @echo off > "!SubDir!\setup_%%j.bat"
    echo print("Python Script") > "!SubDir!\logic_%%j.py"
    echo [Config] > "!SubDir!\setting_%%j.ini"
    echo Data Cadangan > "!SubDir!\cadangan_%%j.dat"
    
    set /A FileCount+=9
)
goto :eof
```

### 💾 B. Script Recovery (`2_recovery_data.bat`)

Script ini menyalin semua data dari `SimulasiDrive_D` ke folder *timestamped* di `SimulasiDrive_C` menggunakan **`xcopy`** dan membuat **`recovery_log.txt`**.

**Tindakan:** Simpan kode di bawah ini sebagai **`2_recovery_data.bat`** di Desktop Anda, lalu **jalankan**.

```batch
@echo off
setlocal enabledelayedexpansion

rem Menentukan nama folder destinasi dengan Tanggal dan Waktu
for /f "tokens=2-4 delims=/ " %%a in ('date /t') do (set "DD=%%a" & set "MM=%%b" & set "YY=%%c")
set "CurrentDate=!YY!!MM!!DD!"
for /f "tokens=1-3 delims=: " %%x in ('echo %time%') do (set "HH=%%x" & set "Min=%%y" & set "Sec=%%z")
set "CurrentTime=!HH!%%y!Sec:~0,2!"

set "SourceDir=%USERPROFILE%\Desktop\SimulasiDrive_D"
set "DestFolderName=DataRecovery_BASIC_!CurrentDate!_!CurrentTime!"
set "DestDir=%USERPROFILE%\Desktop\SimulasiDrive_C\%DestFolderName%"
set "LogFile=%DestDir%\recovery_log.txt"

echo === SIMULASI DATA RECOVERY - BASIC ===

if not exist "%SourceDir%" (
    echo [ERROR]: Folder sumber tidak ditemukan.
    pause & goto :eof
)

mkdir "%DestDir%"
echo Proses Recovery Dimulai: %DATE% %TIME% >> "%LogFile%"

set StartTime=%time%

rem Parameter XCOPY WAJIB: /E /H /C /I /Y
xcopy "%SourceDir%" "%DestDir%" /E /H /C /I /Y >> "%LogFile%" 2>&1

set EndTime=%time%
echo Proses XCOPY Selesai. >> "%LogFile%"

echo.
echo Total File yang Berhasil Disalin (Verifikasi):
dir "%DestDir%" /s /b | find /c /v ""
echo Waktu Mulai: %StartTime% >> "%LogFile%"
echo Waktu Selesai: %EndTime% >> "%LogFile%"
type "%LogFile%"
pause
```

-----

## 2\. Tugas Modifikasi (Tugas 2)

Lakukan modifikasi pada *script* recovery Anda. Contoh modifikasi di sini adalah **File Filtering** (hanya menyalin `.pdf` dan `.docx`).

### 🛠️ Script Modifikasi (`2_recovery_data_modifikasi.bat`)

Script ini menggunakan dua perintah `xcopy` untuk memfilter file berdasarkan ekstensi.

**Tindakan:** Simpan kode ini sebagai **`2_recovery_data_modifikasi.bat`** dan **jalankan**.

```batch
@echo off
setlocal enabledelayedexpansion
rem [Script Modifikasi: Hanya menyalin file .pdf dan .docx]

rem Menentukan nama folder destinasi dengan Tanggal dan Waktu
for /f "tokens=2-4 delims=/ " %%a in ('date /t') do (set "DD=%%a" & set "MM=%%b" & set "YY=%%c")
set "CurrentDate=!YY!!MM!!DD!"
for /f "tokens=1-3 delims=: " %%x in ('echo %time%') do (set "HH=%%x" & set "Min=%%y" & set "Sec=%%z")
set "CurrentTime=!HH!%%y!Sec:~0,2!"

set "SourceDir=%USERPROFILE%\Desktop\SimulasiDrive_D"
set "DestFolderName=DataRecovery_MODIFIED_!CurrentDate!_!CurrentTime!"
set "DestDir=%USERPROFILE%\Desktop\SimulasiDrive_C\%DestFolderName%"
set "LogFile=%DestDir%\recovery_log_modified.txt"

echo === SIMULASI DATA RECOVERY - MODIFIKASI (.pdf & .docx) ===

if not exist "%SourceDir%" (
    echo [ERROR]: Folder sumber tidak ditemukan.
    pause & goto :eof
)

mkdir "%DestDir%"
echo Proses Recovery Dimulai: %DATE% %TIME% >> "%LogFile%"

set StartTime=%time%

rem XCOPY untuk file *.pdf
xcopy "%SourceDir%\*.pdf" "%DestDir%" /S /H /C /I /Y >> "%LogFile%" 2>&1

rem XCOPY untuk file *.docx
xcopy "%SourceDir%\*.docx" "%DestDir%" /S /H /C /I /Y >> "%LogFile%" 2>&1

set EndTime=%time%
echo Proses XCOPY Selesai. >> "%LogFile%"

echo.
echo Total File .pdf dan .docx yang Berhasil Disalin (Verifikasi):
dir "%DestDir%" /s /b | find /c /v ""
echo Waktu Mulai: %StartTime%
echo Waktu Selesai: %EndTime%
pause
```

-----

## 3\. Tugas Tantangan (Tugas 3)

Tugas ini mensimulasikan **Incremental Backup** menggunakan perintah **`robocopy`**, yang lebih kuat dari `xcopy`.

### ⚙️ Script Incremental Backup (`3_incremental_backup.bat`)

Script ini hanya menyalin file yang **baru atau diubah** sejak *backup* terakhir.

**Tindakan:** Simpan kode ini sebagai **`3_incremental_backup.bat`** dan **jalankan dua kali** untuk melihat efek *incremental*.

```batch
@echo off
setlocal enabledelayedexpansion

set "SourceDir=%USERPROFILE%\Desktop\SimulasiDrive_D"
set "DestDir=%USERPROFILE%\Desktop\SimulasiDrive_C\Backup_Robocopy"
set "LogFile=%DestDir%\Robocopy_Log_%DATE:~-4%%DATE:~-7,2%%DATE:~-10,2%.txt"

echo.
echo === TUGAS 3: INCREMENTAL BACKUP (Robocopy) ===

if not exist "%SourceDir%" (
    echo [ERROR]: Folder sumber tidak ditemukan.
    pause & goto :eof
)

if not exist "%DestDir%" (
    echo Membuat folder destinasi utama: %DestDir%
    mkdir "%DestDir%"
)

echo Melakukan Incremental Backup. Log ditambahkan ke %LogFile%
set StartTime=%time%

rem Robocopy Command untuk Incremental Backup:
rem /E: Salin Subdirektori (termasuk kosong)
rem /DCOPY:T: Salin Timestamp Direktori
rem /XO: Exclude Older files (hanya salin yang baru atau diubah)
robocopy "%SourceDir%" "%DestDir%" /E /DCOPY:T /XO /R:0 /W:0 /LOG+:"%LogFile%" /ETA

set EndTime=%time%
echo.
echo Proses Robocopy Selesai.
echo Waktu Mulai: %StartTime%
echo Waktu Selesai: %EndTime%

pause
```

-----

## 4\. Tugas Analisis & Dokumentasi (Tugas 4)

Tugas ini adalah bagian penulisan/laporan. Pastikan laporan Anda mencakup semua poin berikut:

### 📄 Isi Laporan PDF/Word Anda:

| Bagian | Isi yang Harus Dilaporkan |
| :--- | :--- |
| **Analisis Masalah** | 1. Penyebab Umum *Bluescreen* (Hardware, Driver, OS Error). 2. Penjelasan mengapa CMD/Recovery Environment masih bisa diakses saat OS utama gagal. |
| **Solusi Alternatif** | 1. Alat *Recovery* Data Pihak Ketiga (misalnya, software *live boot*). 2. Pentingnya *Cloud Backup* (*preventif*). |
| **Best Practice** | 1. **Strategi *Backup* 3-2-1 Rule** (3 salinan, 2 media berbeda, 1 *offsite*). 2. Perlunya Automasi *Backup* Rutin. |
| **Kesimpulan** | Pembelajaran dari simulasi (keterampilan CLI, pentingnya `xcopy`/`robocopy`) dan aplikasi di dunia nyata. |

-----

## ✅ Checklist Penyerahan (Yang Harus Dikumpulkan)

Pastikan Anda mengumpulkan semua *file* berikut untuk menyelesaikan proyek:

1.  Kedua file **`1_setup_simulasi.bat`** dan **`2_recovery_data.bat`** (atau versi modifikasi Anda).
2.  Minimal **5 Screenshot** proses (Setup, Recovery, Verifikasi).
3.  File **`recovery_log.txt`** dari hasil *Basic Recovery* (Tugas 1).
4.  Laporan **PDF/Word** (Analisis lengkap - Tugas 4).
5.  Jika mengerjakan Tugas 3, sertakan *script* **`3_incremental_backup.bat`** dan *log* `robocopy`.
