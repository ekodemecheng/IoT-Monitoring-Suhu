# IoT-Monitoring-Suhu #
Monitoring suhu dan kelembaban menggunakan ESP32 dan sensor DHT11 serta aplikasiFirebase dan MIT APP Inventor

# Tahapan:

# 1) Membuat Project di Firebase
  - Log in Firebase >> Create a project >> Enter your project name (isi nama project) >> Klik Continue
  - Enable Google Analytics for this project >>  Pilih Default Account for Firebase >> Klik Create project

1.1) Membuat Autentifikasi: 
- Pilih Menu "Build" >> Pilih Sub menu "Authentication" >> Klik Get started
- Pada bag. Authentication >> pilih menu "Sign-in method" >> Pilih Anonymous, lalu Enabled.
- Pada bag. Project Overview >> Pilih Project settings >> Copy and paste "Web API Key" ke notepad.

1.2) Membuat Realtime Database:
- Pilih Menu "Build" >> Pilih Sub menu "Authentication" >> Klik Create Database
- Muncul Set up database >> 1. Database option: Pilih lokasi >> klik Next. Lalu 2. Security rules: pilih "Start in locked mode" >> klik Enable.
- Berhasil membuat Database: Copy paste "URL Database" ke notepad.
- Pada bag. Realtime Database >> pilih menu "Rules" >> Edit rules >> ubah read & write menjadi: true >> klik Publish.

1.3) Database Secret:
- Pada bag. Project Overview >> Pilih Project settings >> Pilih Service accounts
- Pilih Database secrets: Show Secrets >> Copy and paste ke Notepad.

# 2) Membuat Program di IDE Arduino
Program dan Deskripsi terlampir di Folder

# 3) Membuat Aplikasi di MIT App Inventor
Link video tutorial: https://www.youtube.com/watch?v=H0M6lhGOFdo 

Hal yang perlu diperhatikan ketika masukkan database Firebase 
ke dalam MIT App Inventor:
- ProjectBucket: nama sesuai di Realtime Database pada Firebase. contoh: DHT
- FirebaseToken: diisi dengan Database Secret
- FirebaseURL: diisi dengan URL Database 
