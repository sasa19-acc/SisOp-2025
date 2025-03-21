# SISTEM OPERASI

## RESUME CHAPTER 1 : INTRODUCTION

**Oleh:**  
Siti Romzatul Alimah

**Program Studi:**  
D3 Teknik Informatika (A) PENS LA

**NRP:**  
3124521019

**Dosen Pembimbing:**  
Dr Ferry Astika Saputra ST, M.Sc

**Institusi:**  
POLITEKNIK ELEKTRONIKA NEGERI SURABAYA

**Tahun Pelajaran:**  
2024/2025

---

### Tujuan Bab

- Menjelaskan bagaimana fitur sistem operasi bermigrasi dari sistem komputer besar ke sistem yang lebih kecil.
- Membahas fitur-fitur dari beberapa sistem operasi yang penting secara historis.

---

## A.1 Migrasi Fitur

Fitur yang awalnya hanya ada di sistem besar (seperti mainframe) akhirnya diadopsi oleh sistem yang lebih kecil (seperti mikrokomputer).

Contoh: Sistem operasi **MULTICS** mempengaruhi perkembangan sistem operasi modern.

---

## A.2 Sistem Awal

### A.2.1 Sistem Komputer Dedikasi
- Awalnya, programmer juga berperan sebagai operator.
- Program dimuat secara manual melalui panel depan, pita kertas, atau kartu berlubang.

### A.2.2 Sistem Komputer Bersama
- Untuk meningkatkan efisiensi, operator profesional dipekerjakan.
- Job dijalankan secara batch.

### A.2.3 I/O Tumpang Tindih
- Penggunaan tape magnetik untuk mengurangi waktu idle CPU.

---

## A.3 Atlas

Sistem operasi **Atlas** dikembangkan di Universitas Manchester pada akhir 1950-an.

- **Fitur Utama:**
  - Manajemen memori dengan paging.
  - Penggunaan drum sebagai memori utama.
- Menggunakan algoritma penggantian halaman yang canggih untuk waktu itu.

---

## A.4 XDS-940

Sistem operasi time-sharing yang dikembangkan di UC Berkeley pada awal 1960-an.

- Menggunakan paging untuk relokasi memori, tetapi bukan untuk demand paging.
- Memungkinkan beberapa proses pengguna berjalan bersamaan.

---

## A.5 THE

Sistem operasi batch yang dirancang di Technische Hogeschool Eindhoven pada pertengahan 1960-an.

- Dikenal karena desainnya yang bersih.
- Menggunakan semaphore untuk sinkronisasi proses.
- Menggunakan algoritma penjadwalan CPU berbasis prioritas.

---

## A.6 RC 4000

Dirancang untuk komputer Denmark 4000 pada akhir 1960-an.

- Fokus pada pembuatan kernel sistem operasi yang dapat digunakan untuk membangun sistem operasi lengkap.
- Menggunakan mekanisme pesan untuk komunikasi antar proses.

---

## A.7 CTSS

Sistem time-sharing eksperimental yang dikembangkan di MIT pada tahun 1961.

- Mendukung hingga 32 pengguna interaktif.
- Menggunakan algoritma penjadwalan CPU multilevel feedback queue.

---

## A.8 MULTICS

Dikembangkan dari tahun 1965 hingga 1970 sebagai penerus CTSS.

- Dirancang sebagai sistem time-sharing dengan sistem file yang besar dan terdistribusi.
- Menggunakan paged-segmentation untuk manajemen memori.

---

## A.9 IBM OS/360

Sistem operasi untuk keluarga komputer IBM/360 yang muncul pada pertengahan 1960-an.

- Dirancang untuk menjadi sistem operasi tunggal yang dapat digunakan di berbagai jenis komputer IBM.
- Mengalami masalah karena kompleksitas dan upaya untuk memenuhi semua kebutuhan.

---

## A.10 TOPS-20

Sistem operasi time-sharing yang dikembangkan oleh DEC pada tahun 1970-an.

- Dikenal karena antarmuka command-line yang canggih.
- Mendukung virtual memory.

---

## A.11 CP/M dan MS-DOS

- **CP/M:**  
  Sistem operasi awal untuk komputer mikro berbasis Intel 8080.
  
- **MS-DOS:**  
  Dikembangkan oleh Microsoft untuk IBM PC dan menjadi sistem operasi dominan pada era PC awal.

---

## A.12 Macintosh Operating System dan Windows

- **Mac OS:**  
  Sistem operasi pertama dengan GUI yang dirancang untuk pengguna rumahan.
  
- **Windows:**  
  Menjadi pesaing utama Mac OS dan akhirnya mendominasi pasar PC.

---

## A.13 Mach

Sistem operasi yang dikembangkan di Carnegie Mellon University pada 1980-an.

- Dirancang untuk mendukung komputasi paralel dan terdistribusi.
- Menjadi dasar untuk beberapa sistem operasi modern, termasuk macOS dan iOS.

---

## A.14 Sistem Berbasis Kemampuan – Hydra dan CAP

- **Hydra:**  
  Sistem proteksi berbasis kemampuan yang fleksibel, memungkinkan definisi hak akses oleh pengguna.
  
- **CAP:**  
  Sistem proteksi yang lebih sederhana, dengan dua jenis kemampuan: *data capability* dan *software capability*.

---

## A.15 Sistem Lain

Beberapa sistem operasi lain yang menarik, seperti **MCP** untuk Burroughs dan **SCOPE** untuk CDC 6600.
