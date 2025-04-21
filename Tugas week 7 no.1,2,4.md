# SISTEM OPERASI

## Konsep Single Thread dan Multithread

**Oleh:**  
Siti Romzatul Alimah  
D3 Teknik Informatika (A) PENS LA  
NRP 3124521019  

**Dosen Pembimbing:**  
Dr Ferry Astika Saputra, ST, M.Sc  

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**  
**Tahun Pelajaran 2024/2025**

---

**1. JELASKAN DALAM 2 PARAGRAPH DISERTAI DENGAN GAMBAR TENTANG KONSEP SINGLE THREAD DAN MULTITHREAD ! ADA PADA MATERI CH4.**

Jawab :
Single Thread adalah model eksekusi di mana sebuah proses hanya memiliki satu alur eksekusi (thread) yang menjalankan instruksi secara berurutan. Dalam single thread, hanya satu tugas yang dapat diproses pada satu waktu, sehingga jika terjadi blocking (misalnya menunggu I/O), seluruh proses akan terhenti hingga tugas tersebut selesai. Contohnya adalah program sederhana yang membaca input, memprosesnya, lalu menampilkan output tanpa kemampuan untuk menangani tugas lain secara bersamaan. Single thread cocok untuk aplikasi yang tidak membutuhkan paralelisme, seperti kalkulator atau skrip kecil.

Contoh ilustrasi :
[Proses] → [Thread 1] → Tugas 1 → Tugas 2 → Tugas 3

Multithread memungkinkan sebuah proses memiliki beberapa thread yang berjalan secara bersamaan dalam ruang alamat memori yang sama. Setiap thread dapat mengeksekusi tugas berbeda secara independen, sehingga meningkatkan responsivitas dan efisiensi. Misalnya, dalam aplikasi web browser, satu thread dapat menangani antarmuka pengguna, sementara thread lain mengunduh data atau memproses konten. Multithread sangat bermanfaat dalam sistem multicore karena memungkinkan paralelisme sejati. Namun, tantangannya adalah sinkronisasi dan manajemen sumber daya bersama untuk menghindari race condition atau deadlock.

Contoh ilustrasi :
[Proses] → [Thread 1] → Tugas 1
[Thread 2] → Tugas 2
[Thread 3] → Tugas 3


**2. KERJAKAN PROGRAMMING EXERCISE
BERI PENJELASAN DALAM BENTUK ESAY.**

Penerapan thread pada contoh SumTask.java


Penjelesan :
Di Java modern, salah satu mekanisme paling fleksibel untuk pekerjaan paralel adalah Fork/Join Framework. Contoh SumTask.java menunjukkan cara menjumlahkan sebuah array besar (10.000 elemen) secara paralel:
Divide and Conquer
Program akan membagi rentang indeks array menjadi dua bagian hingga setiap potongan berukuran kurang dari THRESHOLD (1.000 elemen).
Fork
Ketika sebuah tugas (task) masih terlalu besar, ia memanggil fork() pada dua subtugas baru—artinya Java menjalankan keduanya di thread terpisah, jika ada kapasitas di pool.
Join
Setelah subtugas selesai, join() mengumpulkan hasilnya dan menjumlahkannya kembali.
Keunggulan penting dari pendekatan ini adalah otomatisasi pengelolaan thread. Kita tidak perlu membuat atau menghancurkan Thread secara eksplisit—cukup gunakan ForkJoinPool, dan Java akan mengalokasikan worker thread yang optimal sesuai jumlah core di mesin. Hasilnya, kode menjadi ringkas, fokus pada logika pembagian pekerjaan, dan performa mudah diskalakan.
penerapan Thread di Linux (thrd-posix.c)


Penjelasan :
Di lingkungan Unix/Linux, standar de facto untuk thread adalah Pthreads. Program thrd-posix.c melakukan hal sederhana: menghitung jumlah bilangan dari 1 hingga N:
Membuat Thread
Fungsi pthread_create() dipanggil dari main(), memulai fungsi runner() di thread baru.
Berbagi Data
Variabel global sum digunakan oleh thread untuk menampung hasil penjumlahan.
Sinkronisasi
pthread_join() memastikan proses utama (main) menunggu hingga thread selesai sebelum mencetak sum.
Karena Pthreads adalah API level rendah, pengembang memiliki kontrol penuh terhadap atribut thread (seperti prioritas, stack size), tapi juga bertanggung jawab menangani sinkronisasi data bersama (shared data) agar terhindar dari race condition. Model ini cocok ketika kita perlu efisiensi tinggi dan kontrol granular di sistem operasi Unix-like.
penerapan thread di Microsoft Windows (thrd-win32.c).



Penjelasan :

Di Windows, pembuatan thread dilakukan lewat Win32 API. Program thrd-win32.c sangat mirip konsepnya dengan Pthreads:
CreateThread
CreateThread() menjalankan fungsi Summation() di thread baru, sambil menerima parameter batas atas perhitungan.
Berbagi Variabel
Variabel Sum di-deklarasikan global untuk menampung hasil.
Menunggu Selesai
WaitForSingleObject() membuat thread utama menunggu hingga thread penyusun jumlah selesai, lalu CloseHandle() membersihkan sumber daya.
Win32 API memberikan ratusan opsi konfigurasi thread—dari security attributes hingga flags pembuatan—namun untuk kasus sederhana modelnya hampir sama dengan Pthreads. Cocok dipakai dalam aplikasi Windows desktop atau layanan yang memerlukan interaksi erat dengan subsistem OS.

Gunakan Link https://github.com/ferryastika/osc10e/tree/master/ch4

BUAT PPT TENTANG EVOLUSI TEKNILOGI PROCESSOR INTEL DENGAN MENGGUNAKAN REFERENSI :



**4.JAWAB PERTANYAAN PRACTICE EXERCISE PADA CHAPTER 4 !**

**PRACTICE EXERCISE:**

#4.1 Berikan tiga contoh pemrograman di mana multithreading memberikan kinerja yang lebih baik dibandingkan dengan solusi single-threaded.
Jawab:
Pemrosesan Gambar (Image Processing): Misalnya, saat menerapkan filter ke gambar resolusi tinggi, setiap bagian gambar dapat diproses secara paralel di thread yang berbeda, sehingga mempercepat keseluruhan proses.
Web Server (seperti Apache atau Nginx): Web server dapat menangani banyak permintaan klien secara bersamaan menggunakan multithreading. Setiap koneksi klien dapat ditangani oleh thread yang berbeda, meningkatkan kemampuan menangani banyak pengguna secara bersamaan.
Aplikasi Komputasi Ilmiah (Scientific Computing): Perhitungan numerik yang intensif, seperti simulasi fisika atau pemrosesan data besar, dapat dibagi menjadi beberapa thread untuk dijalankan secara paralel, mempercepat waktu komputasi.

4.2 Dengan menggunakan Hukum Amdahl, hitung peningkatan kecepatan (speedup gain) dari sebuah aplikasi yang memiliki komponen paralel sebesar 60 persen untuk:
(a) dua inti prosesor dan
(b) empat inti prosesor.
Jawab :
Menggunakan Hukum Amdahl, menghitung peningkatan kecepatan:
Hukum Amdahl: S = 1/((1-p) + p/n)
Dimana:

S = speedup (peningkatan kecepatan)
p = komponen paralel (60% = 0,6)
n = jumlah core

a) Untuk dua core pemrosesan:
S = 1/((1-0,6) + 0,6/2)
S = 1/(0,4 + 0,3)
S = 1/0,7
S = 1,43x
b) Untuk empat core pemrosesan:
S = 1/((1-0,6) + 0,6/4)
S = 1/(0,4 + 0,15)
S = 1/0,55
S = 1,82x




4.3 Apakah web server multithreaded yang dijelaskan pada Bagian 4.1 menunjukkan paralelisme tugas (task parallelism) atau paralelisme data (data parallelism)?

Jawab:
Web server multithreaded itu mengeksekusi banyak koneksi/permintaan klien secara terpisah di thread yang berbeda—masingmasing thread menangani satu permintaan penuh. Ini adalah paralelisme tugas (task parallelism), karena setiap thread menjalankan tugas yang berbeda (menangani request A, B, C, …) bukan membagi data tunggal di antara thread.

4.4 Sebutkan dua perbedaan antara userlevel threads dan kernellevel threads. Dalam kondisi apa masingmasing lebih baik?

Jawab:
Penjadwalan & Switching
Userlevel threads dimanaje di ruang pengguna (user space) oleh library (misalnya pthreads usermode). Context switch-nya sangat cepat (hanya mengubah data struktur di user space) tapi bila satu thread melakukan blocking system call, seluruh proses ikut terblokir.
Kernellevel threads dikelola oleh kernel; context switch membutuhkan interupsi ke mode kernel dan penyimpanan/register restore, sehingga lebih lambat, tapi satu thread yang blocking hanya memblokir dirinya saja, thread lain tetap jalan.
Multiprosesor & Prioritas
Userlevel threads biasanya dipetakan ke sejumlah kernel thread tertentu (misalnya manytoone atau manytomany), sehingga bisa jadi tidak memanfaatkan semua inti prosesor secara efisien.
Kernellevel threads langsung dijadwalkan di masingmasing CPU core oleh kernel, cocok untuk aplikasi computeintensive di SMP (symmetric multiprocessing).
Kapan lebih baik?
Jika banyak operasi ringan, overhead kernel ditakutkan, dan blocking bisa dikendalikan, userlevel threads (green threads) lebih cepat.
Jika aplikasi perlu paralelisme nyata di banyak core, blocking I/O, atau realtime constraint, kernellevel threads lebih andal.

4.5 Jelaskan aksi yang diambil oleh kernel saat melakukan contextswitch antar kernellevel threads.

Jawab:
Save Context Thread Lama
Simpan register CPU (program counter, stack pointer, generalpurpose registers) dari thread yang sedang berjalan ke dalam Thread Control Block (TCB).
Update Data Struktur Penjadwalan
Tandai thread lama sebagai siap/block/tertidur sesuai statusnya.
Pilih Thread Baru
Kernel scheduler memilih TCB thread berikutnya berdasarkan policy (RR, priority, dll.).
Restore Context Thread Baru
Muat kembali register dan stack pointer dari TCB thread baru ke CPU.
Lanjutkan Eksekusi
CPU mulai mengeksekusi instruksi thread baru pada alamat (PC) yang disimpan.

4.6 Resource apa saja yang digunakan saat sebuah thread dibuat? Bagaimana beda dengan saat proses dibuat?

Jawab:
Thread:
Thread Control Block (TCB) berisi register initial, ID thread, pointer ke stack (biasanya stack kecil ~kB–MB), dan struktur penjadwalan.
Berbagi address space, file descriptor, heap, dan resource proses induk.
Proses:
Process Control Block (PCB) lengkap: image alamat virtual baru, segment kode/data, page table terpisah, file descriptor (bisa copyonwrite), heap/stack terpisah, UID, GID, dsb.
Perbedaan utama: thread lebih “ringan”—hanya perlu stack dan TCB, tidak perlu membangun ruang alamat dan tabel halaman baru seperti proses.

4.7 Misalkan sistem operasi memetakan userlevel threads ke kernel threads dengan model manytomany melalui Lightweight Processes (LWPs), dan sistem mengizinkan developer membuat realtime threads untuk sistem realtime. Apakah perlu mengikat (bind) realtime thread ke sebuah LWP? Jelaskan.
Jawab :
Ya, perlu. Tanpa binding, realtime thread (userlevel) mungkin dipindahpindah atau dibagikan di atas beberapa LWP, sehingga hazard priority inversion atau jitter scheduling bisa terjadi. Dengan binding, setiap realtime thread selalu memiliki LWP khusus yang dijadwalkan oleh kernel dengan prioritas dan deadline realtime, sehingga ia mendapatkan jaminan waktu eksekusi dan latensi deterministik yang diperlukan sistem realtime.

4.8 Berikan dua contoh pemrograman di mana multithreading tidak memberikan kinerja lebih baik dibandingkan solusi single-threaded.
Jawab:
Program kecil yang sederhana dan bersifat IO-bound, seperti membaca satu file konfigurasi. Overhead dari membuat thread bisa lebih besar dari keuntungan kinerja.
Aplikasi dengan sinkronisasi intensif, seperti akses ke banyak variabel global yang perlu dilindungi dengan mutex, bisa menyebabkan bottleneck dan kinerja lebih buruk.

4.9 Dalam kondisi apa solusi multithreaded dengan banyak kernel thread memberikan kinerja lebih baik dibandingkan solusi single-threaded pada sistem dengan satu prosesor?
Jawab:
Saat aplikasi memiliki banyak operasi IO-blocking (misalnya membaca file atau menunggu jaringan), thread lain tetap dapat bekerja saat satu thread sedang menunggu. Ini meningkatkan efisiensi walaupun hanya ada satu CPU.

4.10.Komponen program mana dari berikut ini yang dibagikan oleh thread-thread dalam proses multithreaded?
a. Nilai register
b. Memori heap
c. Variabel global
d. Memori stack
Jawab: Yang dibagikan adalah b. Memori heap dan c. Variabel global Sedangkan a. Nilai register dan d. Memori stack adalah privat untuk masing-masing thread.

4.11.Apakah solusi multithreaded yang menggunakan banyak thread tingkat pengguna (user-level thread) bisa memberikan kinerja lebih baik di sistem multiprosesor dibandingkan sistem satu prosesor? Jelaskan.
Jawab:
Ya, karena pada sistem multiprosesor, beberapa thread bisa berjalan secara paralel di core berbeda, meningkatkan kinerja. Pada sistem satu prosesor, hanya satu thread yang bisa berjalan pada satu waktu sehingga manfaat paralelisme tidak tercapai.

4.12.Pada Bab 3, dibahas bahwa Google Chrome membuka setiap tab baru dalam proses terpisah. Apakah manfaat yang sama akan diperoleh jika Chrome menggunakan thread terpisah untuk setiap tab? Jelaskan.
Jawab :
Tidak sepenuhnya. Menggunakan proses terpisah memberikan isolasi lebih baik;
jika satu tab crash, tidak memengaruhi tab lain. Jika menggunakan thread,
semuanya berada dalam satu proses, sehingga crash atau kebocoran memori bisa
memengaruhi semua tab.

4.13. Apakah mungkin memiliki keserentakan (concurrency) tanpa paralelisme  (parallelism)? Jelaskan.
Jawab:
Ya. Concurrency terjadi saat dua atau lebih tugas aktif secara bersamaan, meski tidak dijalankan pada saat yang sama. Di sistem satu prosesor, concurrency bisa dicapai dengan pergiliran tugas (time-sharing), tetapi tidak ada paralelisme karena hanya satu instruksi yang dijalankan dalam satu waktu.

Gunakan Hukum Amdahl untuk menghitung peningkatan kecepatan (speedup) dari aplikasi-aplikasi berikut:
Jawab :


4.15 Tentukan apakah masalah-masalah berikut menunjukkan paralelisme tugas (task parallelism) atau paralelisme data (data parallelism):
Menggunakan thread terpisah untuk menghasilkan thumbnail untuk setiap foto dalam koleksi
Mentranspos matriks secara paralel
Aplikasi jaringan di mana satu thread membaca dari jaringan dan thread lain menulis ke jaringan
Aplikasi penjumlahan array dengan metode fork-join seperti yang dijelaskan di Bagian 4.5.2
Sistem Grand Central Dispatch
Jawab :

4.16 Sebuah sistem dengan dua prosesor dual-core memiliki empat prosesor (inti) yang tersedia untuk penjadwalan. Sebuah aplikasi yang sangat bergantung pada CPU sedang berjalan di sistem ini.
Semua input dilakukan saat program dimulai, ketika sebuah file harus dibuka. Demikian pula, semua output dilakukan tepat sebelum program selesai, ketika hasil program harus ditulis ke dalam satu file.Antara waktu mulai dan waktu selesai program, aplikasi ini sepenuhnya bergantung pada CPU (CPU-bound).Tugasmu adalah meningkatkan performa aplikasi ini dengan cara menggunakan multithreading.Aplikasi berjalan di sistem yang menggunakan model thread satu-ke-satu (setiap thread pengguna dipetakan langsung ke thread kernel).
Berapa banyak thread yang akan kamu buat untuk menangani input dan output? Jelaskan.
Jawab :

akan membuat 1 thread saja untuk menangani proses input dan output.Penjelasan:
Berdasarkan deskripsi soal, proses input hanya dilakukan satu kali di awal, dan proses output hanya dilakukan sekali di akhir program.
Karena proses ini tidak dilakukan secara bersamaan dan hanya terjadi sekali, tidak diperlukan lebih dari satu thread.
Membuat satu thread terpisah untuk menangani IO akan mencegah blocking terhadap thread utama, dan ini sudah cukup efisien.

Berapa banyak thread yang akan kamu buat untuk bagian aplikasi yang intensif terhadap CPU? Jelaskan.
Jawab :
Saya akan membuat 4 thread untuk bagian yang intensif terhadap CPU.Penjelasan:
Sistem memiliki empat inti prosesor (2 prosesor dual-core = 4 core), maka idealnya kita menggunakan empat thread untuk memaksimalkan pemanfaatan CPU.
Karena program menggunakan model satu-ke-satu (one-to-one threading), maka sistem operasi bisa menjadwalkan keempat thread tersebut secara paralel, satu thread per inti.
Dengan cara ini, kita bisa mencapai performansi optimal dari sistem tanpa over-subscription (jumlah thread melebihi jumlah inti prosesor).

4.17 Pertimbangkan potongan kode berikut:

Analisis :
Langkah 1 :
pid = fork(); ( Membuat 1 proses anak → Sekarang ada 2 proses berjalan.
Langkah 2 :
if (pid == 0) {
fork();
thread_create(...);
}
- Ini hanya dijalankan oleh proses anak dari fork pertama.
 - fork(); → proses anak membuat 1 proses anak lagi → Tambah 1 proses.
 - thread_create(...) → membuat 1 thread baru di proses ini.
Total saat ini:
Proses: 3
Thread: 4 (3 proses masing-masing punya 1 thread utama, 1 proses punya 1 thread tambahan)
Langkah 3 :
fork();
(Ini dijalankan oleh semua proses yang ada saat ini (3 proses) → Masing-masing membuat 1 anak → Tambah 3 proses lagi.)
Berapa banyak proses unik yang dibuat?
Jawab :
Awalnya: 1
Setelah fork pertama: +1 → 2 proses
Di dalam if (pid == 0): fork lagi → +1 → 3 proses
fork terakhir dijalankan oleh ketiga proses tersebut → +3 → Total: 6 proses unik

Berapa banyak thread unik yang dibuat?
Jawab :
Semua proses punya 1 thread default
Satu proses (yang menjalankan thread_create(...)) menambahkan 1 thread ekstra
jadi, banyak thread yaitu 7 thread (6 proses × 1 thread + 1 thread tambahan)

4.18 Seperti yang dijelaskan dalam Bagian 4.7.2, Linux tidak membedakan antara proses dan thread. Sebaliknya, Linux memperlakukan keduanya dengan cara yang sama, memungkinkan sebuah task menjadi lebih mirip proses atau thread tergantung pada kumpulan flag yang diberikan ke system call clone(). Namun, sistem operasi lain, seperti Windows, memperlakukan proses dan thread secara berbeda. Biasanya, sistem seperti itu menggunakan notasi di mana struktur data untuk sebuah proses berisi pointer ke thread-thread terpisah yang dimiliki oleh proses tersebut. Bandingkan dua pendekatan ini untuk memodelkan proses dan thread di dalam kernel.
Jawab :
Pendekatan Linux:
Linux menggunakan pendekatan unified atau terpadu, di mana proses dan thread diperlakukan sebagai task yang sama.
Perbedaan antara proses dan thread ditentukan oleh flag yang diberikan ke system call clone().
Karena itu, Linux tidak memiliki perbedaan mendasar antara proses dan thread pada level kernel.
Fleksibilitas clone() memungkinkan pembentukan berbagai bentuk hubungan antara task, seperti thread berbagi memori atau proses terpisah.
Pendekatan Windows (dan sistem lainnya):
Windows membedakan secara eksplisit antara proses dan thread.
Sebuah proses memiliki ruang alamat sendiri dan sumber daya lainnya.
Thread adalah unit eksekusi yang hidup di dalam proses, dan semua thread dalam proses yang sama berbagi ruang alamat dan sumber daya.
Struktur data kernel untuk proses berisi pointer ke semua thread-nya.
Perbandingan:
Linux lebih fleksibel dan sederhana di level implementasi kernel karena menyatukan keduanya, namun dapat membingungkan bagi pemula.
Windows memberikan pemisahan yang lebih jelas antara proses dan thread, memudahkan pemahaman konseptual, tapi implementasi kernel lebih kompleks.
4.19 Program yang ditunjukkan pada Gambar 4.23 menggunakan API Pthreads. Apa output dari program tersebut pada BARIS C dan BARIS P?
Jawab :
Gambar.4.23

Penjelasan fungsi pthread_setcancelstate:
Fungsi ini mengatur apakah sebuah thread dapat dibatalkan (cancelled) oleh thread lain.
PTHREAD_CANCEL_DISABLE: Membuat thread tidak bisa dibatalkan.
PTHREAD_CANCEL_ENABLE: Membuat thread bisa dibatalkan lagi.
Argumen kedua (&oldstate) akan menyimpan nilai status pembatalan thread sebelum perubahan, misalnya apakah sebelumnya thread bisa dibatalkan atau tidak.
Jadi :
LINE C adalah baris pertama pemanggilan pthread_setcancelstate(PTHREAD_CANCEL_DISABLE, &oldstate);
LINE P adalah baris kedua pthread_setcancelstate(PTHREAD_CANCEL_ENABLE, &oldstate);
Maka:
Output di LINE C: nilai oldstate berisi status pembatalan sebelum DISABLE, yang biasanya ENABLE secara default. Jadi oldstate = PTHREAD_CANCEL_ENABLE.
Output di LINE P: nilai oldstate sekarang adalah PTHREAD_CANCEL_DISABLE, karena status sebelumnya dinonaktifkan oleh LINE C.
4.20 Pertimbangkan sebuah sistem multicore dan program multithread yang ditulis menggunakan model many-to-many threading. Misalkan jumlah user-level thread dalam program lebih banyak daripada jumlah inti pemrosesan (core) dalam sistem. Diskusikan implikasi performa dari skenario berikut:
a. Jumlah kernel thread yang dialokasikan untuk program lebih sedikit daripada jumlah inti pemrosesan.
b. Jumlah kernel thread yang dialokasikan untuk program sama dengan jumlah inti pemrosesan.
c. Jumlah kernel thread yang dialokasikan untuk program lebih banyak dari jumlah inti pemrosesan tetapi masih lebih sedikit dari jumlah user-level thread.
Jawab :
a. Kernel thread < Jumlah core
Implikasi:
Tidak semua core bisa digunakan secara optimal karena ada lebih sedikit kernel thread yang bisa dijadwalkan ke core.
Underutilization (pemanfaatan kurang) dari hardware terjadi.
Beberapa user-level thread harus menunggu lebih lama untuk mendapatkan akses ke kernel thread.
Performa menurun karena tidak memanfaatkan seluruh kapasitas paralelisme dari prosesor.
b. Kernel thread = Jumlah core
Implikasi:
Ini adalah situasi ideal dalam banyak kasus.
Setiap kernel thread bisa berjalan pada satu core secara paralel tanpa kompetisi antar thread di level kernel.
Penjadwalan menjadi lebih efisien dan meminimalisasi context switching.
Performa optimal bisa dicapai asalkan tidak terlalu banyak blocking atau operasi I/O.
c. Kernel thread > Jumlah core, tetapi < jumlah user thread
Implikasi:
Lebih banyak kernel thread daripada core berarti akan terjadi konteks switching antar kernel thread di core yang sama.
Namun, karena masih lebih sedikit dari jumlah user thread, tetap saja ada beberapa user thread yang harus menunggu untuk bisa dieksekusi.
Sistem jadi lebih fleksibel dibanding skenario (a), karena lebih banyak user thread bisa dijalankan secara paralel.
Performa lebih baik dari (a), tapi tidak sebaik (b)—karena adanya overhead switching dan antrian thread.
4.21 Pthreads menyediakan API untuk mengelola pembatalan thread. Fungsi pthread_setcancelstate() digunakan untuk mengatur status pembatalan. Prototipe fungsi tersebut adalah sebagai berikut:
pthread_setcancelstate(int state, int *oldstate)
Dua nilai yang mungkin untuk parameter state adalah:
PTHREAD_CANCEL_ENABLE dan PTHREAD_CANCEL_DISABLE
Dengan menggunakan potongan kode yang ditunjukkan pada Gambar 4.24, berikan dua contoh operasi yang sesuai untuk dilakukan di antara pemanggilan fungsi untuk menonaktifkan dan mengaktifkan kembali pembatalan thread.
Jawab :
1.  Penulisan ke File atau Database (I/O sensitif):
Misalnya, menyimpan data penting yang tidak boleh terganggu karena jika pembatalan terjadi di tengah proses, file atau database bisa rusak:

2.  Alokasi atau Dealokasi Memori Kritis:
Saat mengalokasikan atau membebaskan memori, kita tidak ingin thread dibatalkan di tengah proses, karena bisa menyebabkan memory leak atau kebocoran sumber daya:

4.22 Tulis program multithreaded yang menghitung berbagai nilai statistik dari sebuah daftar angka. Program ini akan menerima sekumpulan angka melalui baris perintah (command line), lalu membuat tiga thread pekerja (worker threads) yang terpisah.Thread pertama menghitung rata-rata dari angka-angka tersebut.Thread kedua menentukan nilai maksimum.Thread ketiga menentukan nilai minimum.
90 81 78 95 79 72 85
Nilai rata-rata adalah 82
Nilai minimum adalah 72
Nilai maksimum adalah 95
Variabel yang menyimpan nilai rata-rata, minimum, dan maksimum disimpan secara global. Thread pekerja akan mengatur nilai-nilai ini, dan thread utama (parent thread) akan mencetak hasilnya setelah semua worker selesai dieksekusi.
jawab :
Gunakan array global untuk menyimpan angka dari input.
Buat tiga thread:
Thread 1: menghitung rata-rata.
Thread 2: mencari nilai maksimum.
Thread 3: mencari nilai minimum.
Setelah semua thread selesai (pthread_join), cetak semua nilai.
Gunakan variabel global untuk hasilnya.



Tulis program multithreaded yang mencetak bilangan prima. Cara  kerjanya: Pengguna menjalankan program dan memasukkan sebuah angka lewat command line.Program akan membuat satu thread yang mencetak semua bilangan prima yang kurang dari atau sama dengan angka yang dimasukkan.
Jawab :

Buat thread baru yang menerima angka sebagai parameter.
Di dalam thread, loop dari 2 hingga angka tersebut dan cek apakah bilangan tersebut prima.
Cetak semua bilangan prima yang ditemukan.


4.24 Teknik Monte Carlo untuk Menghitung π
Cara menarik untuk menghitung π adalah dengan menggunakan teknik yang dikenal sebagai Monte Carlo, yang memanfaatkan pengacakan. Teknik ini bekerja sebagai berikut: Misalkan Anda memiliki sebuah lingkaran yang terinskripsi di dalam sebuah persegi (lihat Gambar 4.25). Anggap jarijari lingkaran ini = 1.
Hasilkan sejumlah titik acak sebagai koordinat (x, y). Titiktitik ini harus terletak di dalam batas persegi, yaitu –1 ≤ x ≤ 1 dan –1 ≤ y ≤ 1. Dari keseluruhan titik acak yang dihasilkan, sebagian akan jatuh di dalam lingkaran.
Taksir nilai π dengan rumus:
π = 4x (jumlah titik dalam lingkaran ) / (total titik)
Buatlah versi multithreaded dari algoritma di atas, dengan ketentuan: Setiap thread bertanggungjawab menghasilkan sejumlah titik acak dan menghitung berapa banyak di antaranya yang jatuh di dalam lingkaran. Hasil hitung tiap thread (jumlah titik dalam lingkaran) disimpan dalam variabel global bersama. Setelah semua thread selesai, thread induk (“parent”) akan mengumpulkan hasil-hasil tersebut, menghitung taksiran π, dan menampilkannya. Silakan bereksperimen dengan berbagai jumlah titik acak: secara umum, semakin banyak titik, semakin dekat taksiran nilai π.
Gambar 4.25. Teknik Monte Carlo untuk menghitung π
(Lingkaran biru berjarijari 1 di dalam persegi berkoordinat (–1,–1) sampai (1,1). Titik pusat di (0,0).)
Jawab :
contoh implementasi C menggunakan pthread untuk menghitung π dengan metode Monte Carlo secara multithreaded.
Program menerima dua argumen:
Jumlah thread
Total titik (akan dibagi merata ke tiap thread)



4.25 Ulangi soal 4.24, tetapi alih-alih menggunakan thread terpisah untuk menghasilkan titik acak, gunakan OpenMP untuk melakukan paralelisasi proses pembangkitan titik-titik tersebut.
Berhati-hatilah agar perhitungan nilai π tidak ditempatkan dalam bagian paralel, karena Anda hanya ingin menghitung π satu kali saja
jawab :

Penjelasan :
-   Pembacaan Input
     Program menerima satu argumen: total_points (jumlah total titik acak).
-  Variabel Reduksi
in_circle dihitung lewat #pragma omp atomic agar penambahan dari tiap thread aman.
Tiap thread punya local_count sendiri untuk mengurangi kontensi.
-  Pengacakan
Gunakan rand_r(&seed) agar setiap thread punya seed berbeda (seed diturunkan dari time(NULL) dan ID thread).
-  Paralelisasi
#pragma omp parallel memulai region paralel.
#pragma omp for membagi loop i = 0 … total_points-1 ke setiap thread.
-  Perhitungan π
     Dilakukan di luar region paralel, sekali saja, setelah semua thread selesai (} otomatis     melakukan barrier).

4.26 Modifikasilah server tanggal berbasis socket (Gambar 3.27 pada Bab 3) sehingga server tersebut melayani setiap permintaan klien dalam thread yang terpisah.

4.27 Deret Fibonacci adalah deret angka 0, 1, 1, 2, 3, 5, 8, ...
Secara formal, deret ini dapat didefinisikan sebagai:
fib₀ = 0
fib₁ = 1
fibₙ = fibₙ₋₁ + fibₙ₋₂
Tulis sebuah program multithreaded yang menghasilkan deret Fibonacci. Program ini harus bekerja sebagai berikut:
Di command line, pengguna akan memasukkan berapa banyak angka Fibonacci yang ingin dihasilkan oleh program.
Program kemudian akan membuat thread terpisah yang akan menghitung angka-angka Fibonacci, dan menyimpannya dalam struktur data bersama (array kemungkinan adalah struktur data yang paling nyaman).
Setelah thread selesai menjalankan tugasnya, thread induk (parent) akan mencetak deret Fibonacci yang telah dihitung oleh thread anak (child).
Karena thread induk tidak dapat mulai mencetak deret Fibonacci sebelum thread anak selesai menghitung, maka thread induk harus menunggu thread anak selesai terlebih dahulu.
Gunakan teknik yang dijelaskan di Bagian 4.4 untuk memenuhi kebutuhan ini.


4.28 Modifikasi soal pemrograman Exercise 3.20 dari Bab 3, yang meminta Anda merancang manajer PID (Process ID).
Modifikasi ini berupa pembuatan program multithreaded yang menguji solusi Anda terhadap Exercise 3.20.
Anda akan membuat sejumlah thread—misalnya, 100 thread—dan setiap thread akan:
Meminta sebuah PID,
Tidur (sleep) selama waktu acak,
Lalu melepaskan PID tersebut.
(Tidur dalam waktu acak ini mensimulasikan penggunaan PID pada sistem nyata, di mana sebuah PID diberikan ke proses baru, proses berjalan, lalu selesai, dan PID dilepas setelah proses tersebut berhenti.)
Jawab :
Buat manajer PID untuk mengatur ID proses dari rentang tertentu. Contohnya:
Rentang PID: 300 – 5000
Fungsi:
allocate_pid() → mengembalikan PID yang belum digunakan
release_pid(pid) → melepaskan PID agar bisa dipakai lagi.


Struktuk Program Multithreaded
1. Kelas PidManager
Mengelola PID menggunakan array atau struktur boolean.
2. Kelas PidUser
Simulasi proses yang berjalan dengan sleep random.
3. Kelas PidTest
Membuat dan menjalankan 100 thread
Penjelasan :
PidManager menggunakan array boolean untuk melacak PID mana yang digunakan.
Semua metode synchronized agar thread-safe (mencegah race condition).
PidUser adalah simulasi proses:
Minta PID → Sleep → Lepas PID
ExecutorService digunakan untuk mengatur 100 thread dalam pool yang efisien.

Pada sistem UNIX dan Linux, tidur dilakukan melalui fungsi sleep(), yang menerima nilai integer sebagai parameter untuk menunjukkan berapa detik thread harus tidur.
Masalah ini akan dimodifikasi lagi di Bab 7.


4.29 Latihan 3.25 di Bab 3 melibatkan perancangan server echo menggunakan Java Threading API.
Server ini single-threaded, artinya server tidak dapat merespons beberapa klien secara bersamaan hingga klien saat ini selesai.
Modifikasi solusi untuk Exercise 3.25 agar server echo menangani setiap permintaan klien dalam thread yang terpisah.
Jawab :
Menggunakan Java Threading API (Thread atau Runnable) untuk memproses setiap koneksi klien secara paralel.
ServerSocket tetap berjalan di thread utama.
Untuk setiap koneksi klien yang diterima:
Buat objek ClientHandler (mengimplementasikan Runnable)
Jalankan dalam thread baru menggunakan new Thread(handler).start();
Server bisa menangani banyak klien secara bersamaan tanpa menunggu klien sebelumnya selesai.











