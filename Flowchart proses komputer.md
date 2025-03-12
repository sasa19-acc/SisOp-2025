# SISTEM OPERASI  
## FLOWCHART PROSES KOMPUTER

**Oleh:**  
Siti Romzatul Alimah  
D3 Teknik Informatika (A) PENS LA  
NRP 3124521019  
Dosen Pembimbing: Dr Ferry Astika Saputra ST, M.Sc  

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**  
**TAHUN PELAJARAN 2024/2025**


![flowchart-Siti Romzatul Allimah](https://github.com/user-attachments/assets/510b522b-9aa3-4543-aa91-82d4054fdd4d)


**Penjelasan :**

1.	Start System
Proses dimulai ketika daya komputer diaktifkan.
2.	Load Firmware (BIOS/UEFI)
Firmware dibaca dari NVRAM, lalu inisialisasi dasar dimulai.
3.	Deteksi & Inisialisasi Hardware
Firmware mengenali perangkat keras, seperti CPU, RAM, dan disk.
4.	Pilih Boot Device
Menentukan sumber boot (disk, jaringan, USB, dsb.). Jika UEFI, sistem juga mengakses EFI System Partition (ESP).
5.	Load Bootloader
Bootloader (misalnya GRUB) diambil dari perangkat/partisi yang telah ditentukan.
6.	Bootloader Pilih Kernel & Muat Kernel ke Memori
Bootloader menampilkan menu atau otomatis memilih kernel tertentu, lalu memuatnya.
7.	Kernel Inisialisasi
Kernel melakukan konfigurasi driver, manajemen memori, dan menyiapkan struktur internal.
8.	Jalankan init/systemd (PID 1)
Kernel meluncurkan proses utama (init/systemd) sebagai induk semua proses di user space.
9.	Eksekusi Skrip & Service Startup
init/systemd memuat berbagai layanan, daemon, dan konfigurasi startup.
10.	Sistem Berjalan
Setelah semua layanan aktif, sistem siap digunakan untuk login atau menjalankan aplikasi.




