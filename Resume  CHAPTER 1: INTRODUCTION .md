# SISTEM OPERASI

## RESUME CHAPTER 1: INTRODUCTION

### Oleh:
**Siti Romzatul Alimah**  
D3 Teknik Informatika (A) PENS LA  
NRP 3124521019  
Dosen Pembimbing: Dr Ferry Astika Saputra ST, M.Sc  

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**  
**TAHUN PELAJARAN 2024/2025**  

---

## Pendahuluan
Sistem Operasi (OS) adalah perangkat lunak yang mengelola sumber daya perangkat keras komputer dan menyediakan layanan untuk aplikasi pengguna.

Bab ini membahas berbagai topik terkait sistem operasi, termasuk:
- Organisasi sistem komputer
- Operasi sistem operasi
- Manajemen sumber daya
- Keamanan
- Virtualisasi
- Lingkungan komputasi

---

## Tujuan Pembelajaran
1. Menjelaskan organisasi umum sistem komputer dan peran interupsi.
2. Menjelaskan komponen dalam sistem komputer multiprosesor modern.
3. Mengilustrasikan transisi dari mode pengguna ke mode kernel.
4. Mendiskusikan penggunaan sistem operasi dalam berbagai lingkungan komputasi.
5. Memberikan contoh sistem operasi open-source.

---

## Struktur Sistem Komputer
Sistem komputer dapat dibagi menjadi empat komponen utama:
1. **Perangkat Keras (Hardware)** - Menyediakan sumber daya komputasi dasar seperti CPU, memori, dan perangkat I/O.
2. **Sistem Operasi** - Mengontrol dan mengkoordinasikan penggunaan perangkat keras di antara berbagai aplikasi dan pengguna.
3. **Program Aplikasi** - Menentukan cara sumber daya sistem digunakan untuk menyelesaikan masalah komputasi pengguna.
4. **Pengguna** - Orang, mesin, atau komputer lain yang berinteraksi dengan sistem.

---

## Fungsi Sistem Operasi
- Bertindak sebagai **alokator sumber daya** dan **program kontrol** yang mengelola eksekusi program pengguna.
- Pada sistem **mainframe**, OS harus memastikan semua pengguna puas.
- Pada **perangkat mobile**, OS dioptimalkan untuk penggunaan baterai dan antarmuka pengguna yang mudah digunakan.

---

## Definisi Sistem Operasi
- Tidak ada definisi universal untuk sistem operasi.
- **Kernel** adalah program yang selalu berjalan di komputer, sementara program lain bisa berupa **program sistem** atau **program aplikasi**.
- Sistem operasi modern juga mencakup **middleware** yang menyediakan layanan tambahan untuk pengembang aplikasi.

---

## Organisasi Sistem Komputer
- Sistem komputer terdiri dari satu atau lebih CPU dan pengontrol perangkat yang terhubung melalui bus.
- CPU dan perangkat I/O dapat berjalan secara bersamaan, dengan setiap pengontrol perangkat memiliki buffer lokal.
- **Interupsi** digunakan untuk memberi tahu CPU bahwa operasi I/O telah selesai.

---

## Fungsi Umum Interupsi
- Interupsi mengalihkan kontrol ke **rutin layanan interupsi** melalui **vektor interupsi**.
- **Trap** atau **exception** adalah interupsi yang dihasilkan oleh perangkat lunak, baik karena kesalahan atau permintaan pengguna.

---

## Penanganan Interupsi
- OS menyimpan status CPU saat interupsi terjadi dan menentukan jenis interupsi yang terjadi.
- Dua metode penanganan interupsi:
  1. **Polling**
  2. **Vectored Interrupt System**

---

## Struktur I/O
- Setelah I/O dimulai, kontrol dapat kembali ke program pengguna setelah I/O selesai atau tanpa menunggu I/O selesai.
- **System call** digunakan untuk meminta OS menunggu penyelesaian I/O.

---

## Struktur Penyimpanan
1. **Memori utama** - Media penyimpanan besar yang dapat diakses langsung oleh CPU.
2. **Penyimpanan sekunder** (seperti hard disk) - Kapasitas penyimpanan besar dan non-volatile.
3. **Memori non-volatile (NVM)** - Seperti SSD, semakin populer karena kecepatan dan kapasitasnya.

---

## Hierarki Penyimpanan
- Sistem penyimpanan diorganisir dalam hierarki berdasarkan **kecepatan**, **biaya**, dan **volatilitas**.
- **Caching** adalah teknik menyalin informasi ke penyimpanan yang lebih cepat untuk meningkatkan kinerja.

---

## Arsitektur Komputer Modern
- Komputer modern menggunakan **arsitektur von Neumann**, di mana instruksi dan data disimpan dalam memori yang sama.
- **Direct Memory Access (DMA)** memungkinkan perangkat I/O mentransfer data langsung ke memori tanpa intervensi CPU.

---

## Arsitektur Sistem Komputer
- **Sistem multiprosesor** semakin banyak digunakan karena meningkatkan throughput, efisiensi, dan keandalan.
- Dua jenis multiprosesor:
  1. **Asymmetric Multiprocessing**
  2. **Symmetric Multiprocessing**

---

## Desain Dual-Core dan NUMA
- **Sistem multicore** menggabungkan beberapa inti prosesor dalam satu chip.
- **Non-Uniform Memory Access (NUMA)** adalah sistem di mana waktu akses memori bervariasi tergantung pada lokasi memori relatif terhadap prosesor.

---

## Sistem Terkluster
- **Sistem terkluster** terdiri dari beberapa sistem yang bekerja bersama, biasanya berbagi penyimpanan melalui **Storage-Area Network (SAN)**.
- Sistem ini menyediakan layanan **high-availability** yang dapat bertahan dari kegagalan.

---

## Motherboard PC
- Motherboard PC modern memiliki **soket prosesor, slot DRAM, dan slot PCIe**, serta konektor I/O dan daya.
- Beberapa motherboard memiliki **beberapa soket prosesor**, memungkinkan sistem NUMA.

---

## Operasi Sistem Operasi
- **Bootstrap program** adalah kode sederhana yang menginisialisasi sistem dan memuat kernel.
- Kernel bersifat **interrupt-driven**, merespons interupsi dari perangkat keras dan perangkat lunak.

---

## Multiprogramming dan Multitasking
- **Multiprogramming** meningkatkan efisiensi dengan memastikan CPU selalu memiliki pekerjaan untuk dieksekusi.
- **Timesharing (multitasking)** memungkinkan CPU beralih antar pekerjaan dengan cepat sehingga pengguna dapat berinteraksi dengan sistem secara interaktif.

---

## Manajemen Proses
- **Proses** adalah program yang sedang dieksekusi dan membutuhkan sumber daya seperti CPU, memori, dan I/O.
- OS bertanggung jawab untuk:
  1. Membuat, menghapus, menangguhkan, dan melanjutkan proses.
  2. Menyediakan mekanisme untuk sinkronisasi dan komunikasi proses.
