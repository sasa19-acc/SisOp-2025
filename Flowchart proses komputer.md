# SISTEM OPERASI  
## FLOWCHART PROSES KOMPUTER

**Oleh:**  
Siti Romzatul Alimah  
D3 Teknik Informatika (A) PENS LA  
NRP 3124521019  
Dosen Pembimbing: Dr Ferry Astika Saputra ST, M.Sc  

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**  
**TAHUN PELAJARAN 2024/2025**



```plaintext
+--------------------------------------------------+
|            Power On (Komputer Dinyalakan)        |
+--------------------------------------------------+
                          |
                          v
+--------------------------------------------------+
|   CPU membaca BIOS/UEFI dari ROM di Motherboard  |
+--------------------------------------------------+
                          |
                          v
+--------------------------------------------------+
|      Jalankan BIOS/UEFI & Lakukan POST           |
|   (Power-On Self Test untuk cek hardware)        |
+--------------------------------------------------+
                          |
                          v
+--------------------------------------------------+
|         Apakah terjadi Hardware Error?         |
+--------------------------------------------------+
          /                      \
         / Yes                   \ No
        v                          v
+-----------------------+    +--------------------------+
| Tampilkan Error/Beep  |    |   Pindai Boot Device     |
| Code (Error Handling) |    | (HDD/SSD/USB, dsb.)       |
+-----------------------+    +--------------------------+
                                       |
                                       v
                           +--------------------------+
                           |  Boot Device Ditemukan?  |
                           +--------------------------+
                              /               \
                             / Yes            \ No
                            v                   v
               +---------------------+  +-----------------------------+
               | Load Bootloader     |  | Tampilkan Error:            |
               | (MBR/GPT)           |  | "No Boot Device/Failure"    |
               +---------------------+  +-----------------------------+
                            |
                            v
               +---------------------+
               | Bootloader Dieksekusi|
               +---------------------+
                            |
                            v
               +---------------------+
               |  Multi-Boot Menu?   |
               | (Pilihan OS tersedia?) |
               +---------------------+
                    /           \
                   / Yes         \ No
                  v               v
         +----------------+  +----------------------+
         | User Pilih OS  |  |   OS Default         |
         +----------------+  +----------------------+
                  \               /
                   \             /
                    v           v
               +---------------------+
               | Load Kernel ke RAM  |
               +---------------------+
                          |
                          v
               +-------------------------------+
               | Kernel Inisialisasi:          |
               | - Struktur Data & Memori      |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               | Load & Inisialisasi Driver    |
               | (Hardware Drivers)            |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               | Mount Root Filesystem         |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               | Spawn Proses init             |
               | (systemd, init, dsb.)         |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               | Jalankan Layanan & Daemon     |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               | Tampilkan Login Screen        |
               | (Display Manager / CLI)       |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               |        User Login             |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               |  Load User Environment/       |
               |  Desktop (GUI atau Shell)     |
               +-------------------------------+
                          |
                          v
               +-------------------------------+
               |     Sistem Siap Digunakan     |
               +-------------------------------+
```
**Penjelasan :**
1.	Power On: Komputer dinyalakan, lalu CPU membaca instruksi awal dari BIOS/UEFI.
2.	POST: Sistem menjalankan Power-On Self Test untuk memeriksa kondisi hardware. Jika ada error, error atau beep code ditampilkan.
3.	Boot Device: Jika POST sukses, BIOS/UEFI memindai perangkat boot (HDD/SSD/USB). Jika tidak ada boot device, muncul pesan error.
4.	Bootloader: Jika boot device ditemukan, bootloader (misalnya MBR/GPT) dimuat dan dieksekusi. Jika ada menu multi-boot, user dapat memilih OS, jika tidak, OS default dipilih.
5.	Kernel & Inisialisasi: Kernel dimuat ke RAM, menginisialisasi memori, struktur data, dan driver perangkat keras. Root filesystem dipasang.
6.	Proses init & Layanan: Proses init (seperti systemd) dijalankan untuk memulai layanan sistem dan daemon.
7.	Login & User Environment: Display manager atau login prompt muncul, setelah login berhasil, user environment (desktop atau shell) dimuat, sehingga komputer siap digunakan.



