# Analisa:
## Sjf Scheduling Algorithm Without Arrival Time (Non-Preemptive)
*SJF (Shortest Job First) Non-Preemptive adalah algoritma penjadwalan CPU yang memilih proses dengan waktu eksekusi (burst time) paling pendek untuk dieksekusi berikutnya. Karena bersifat non-preemptive, proses yang sedang berjalan tidak akan diganggu hingga selesai, bahkan jika ada proses lain dengan waktu yang lebih pendek.*
--
Analisis Kode:
1. Struktur Data
struct proc {
    int no, bt, ct, tat, wt;
};
--
•	no: Nomor proses.
•	bt: Burst time (waktu yang dibutuhkan proses untuk menjalankan tugasnya).
•	ct: Completion time (waktu selesai proses).
•	tat: Turnaround time (waktu total yang dibutuhkan untuk menjalankan proses dari kedatangan hingga selesai).
•	wt: Waiting time (waktu tunggu, yang dihitung sebagai TAT - Burst Time).
---
3. Fungsi read()
Fungsi ini membaca informasi dari pengguna untuk setiap proses. Setiap proses memiliki nomor dan burst time.
**struct proc read(int i) {
    struct proc p;
    printf("\nProcess No: %d\n", i);
    p.no = i;
    printf("Enter Burst Time: ");
    scanf("%d", &p.bt);
    return p;
}**
•	Fungsi ini meminta pengguna untuk memasukkan burst time untuk setiap proses dan mengembalikan objek proses.
---
5. Membaca Data dan Mengurutkan Proses
Dalam bagian ini, program meminta jumlah proses, kemudian memanggil fungsi read() untuk mendapatkan data burst time setiap proses. Setelah itu, data proses diurutkan berdasarkan burst time secara ascending menggunakan bubble sort.
**for (int i = 0; i < n-1; i++)
    for (int j = 0; j < n-i-1; j++)    
        if (p[j].bt > p[j+1].bt) {
            tmp = p[j];
            p[j] = p[j+1];
            p[j+1] = tmp;
        }**
•	Proses dengan burst time lebih kecil akan diutamakan untuk dieksekusi terlebih dahulu.
---
7. Perhitungan Waktu
Pada bagian ini, program menghitung completion time (CT), turnaround time (TAT), dan waiting time (WT) untuk setiap proses setelah diurutkan berdasarkan burst time.
•	Completion Time (CT): Waktu saat proses selesai dijalankan. Ini dihitung dengan menambahkan burst time proses ke waktu selesai proses sebelumnya (ct).
**ct += p[i].bt;
p[i].ct = ct;
•	Turnaround Time (TAT): Waktu yang dibutuhkan dari kedatangan proses sampai selesai. Ini dihitung dengan CT - Arrival Time (dalam hal ini, arrival time dianggap 0).
p[i].tat = p[i].ct;
•	Waiting Time (WT): Waktu yang dibutuhkan oleh proses untuk menunggu di antrian. Ini dihitung dengan TAT - Burst Time.
p[i].wt = p[i].tat - p[i].bt;**
---
9. Output Hasil
Setelah perhitungan selesai, program menampilkan tabel yang berisi informasi tentang setiap proses, seperti:
•	Nomor Proses (P1, P2, ...)
•	Burst Time (BT)
•	Completion Time (CT)
•	Turnaround Time (TAT)
•	Waiting Time (WT)
•	(Waktu RT yang tidak dihitung, mungkin seharusnya adalah Reponse Time yang biasa digunakan dalam penjadwalan interaktif).
Setelah itu, program juga menampilkan rata-rata Turnaround Time dan rata-rata Waiting Time untuk semua proses.
**avgtat /= n;
avgwt /= n;
printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f", avgtat, avgwt);**
---
11. Potensi Masalah atau Kekurangan
•	Response Time (RT): Di dalam tabel output ada kolom RT, namun kode tidak menghitung nilai RT (Respons Time), yang umumnya didefinisikan sebagai waktu sejak permintaan proses hingga pertama kali proses dijalankan. Kolom ini tidak diupdate dalam kode.
•	Tidak Mempertimbangkan Arrival Time: Kode ini bekerja dengan asumsi bahwa semua proses tiba pada waktu yang sama (arrival time = 0), sehingga tidak memproses kedatangan berbeda dari tiap proses.
•	Tidak Memverifikasi Input: Program tidak memeriksa apakah nilai input valid atau tidak (misalnya, jika nilai burst time adalah angka negatif, program tetap akan berjalan tanpa peringatan).
---
kesimpulan
Kode ini mengimplementasikan algoritma Shortest Job First (SJF) tanpa mempertimbangkan arrival time, yang berarti semua proses dianggap tiba pada waktu yang sama. Algoritma ini mengurutkan proses berdasarkan burst time dan menghitung waktu-waktu yang relevan (completion time, turnaround time, dan waiting time). Program ini memberikan gambaran yang baik tentang cara kerja SJF, meskipun ada beberapa kekurangan yang dapat diperbaiki, seperti perhitungan Response Time dan validasi input.


# Gantt Chart dan Data Proses

| Process | BT | CT | TAT | WT |
|---------|----|----|-----|----|
| P4      | 3  | 3  | 3   | 0  |
| P1      | 6  | 9  | 9   | 3  |
| P3      | 7  | 16 | 16  | 9  |
| P2      | 8  | 24 | 24  | 16 |

## Gantt Chart

| P4  |      P1       |       P3       |        P2        |
|-----|---------------|----------------|------------------|
0     3               9                16                 24





---



## Sjf Scheduling Algorithm (Non-Preemptive)
*SJF (Shortest Job First) adalah algoritma penjadwalan yang memilih proses dengan burst time terpendek di antara semua proses yang sudah tiba (arrival time ≤ waktu saat ini).
Dalam versi non-preemptive, jika sebuah proses sedang berjalan, ia tidak akan dihentikan sampai selesai—meskipun ada proses baru dengan burst time lebih pendek yang datang kemudian.*
--
Analisis Kode:
1. Struktur Data
**struct proc {
    int no, at, bt, it, ct, tat, wt;
};**

•	no: Nomor proses.
•	at: Arrival time (waktu kedatangan).
•	bt: Burst time (waktu yang dibutuhkan untuk eksekusi).
•	it: Internal time (waktu mulai eksekusi).
•	ct: Completion time (waktu selesai eksekusi).
•	tat: Turnaround time (waktu dari kedatangan hingga selesai, CT - AT).
•	wt: Waiting time (waktu tunggu sebelum proses dimulai, TAT - BT).
---
2. Fungsi read()
Fungsi read() digunakan untuk membaca input dari pengguna. Di sini, pengguna diminta untuk memasukkan Arrival Time (AT) dan Burst Time (BT) untuk setiap proses yang akan dihitung oleh algoritma.
**struct proc read(int i) {
    struct proc p;
    printf("\nProcess No: %d\n", i);
    p.no = i;
    printf("Enter Arrival Time: ");
    scanf("%d", &p.at);
    printf("Enter Burst Time: ");
    scanf("%d", &p.bt);
    return p;
}**
•	at: Waktu kedatangan proses.
•	bt: Waktu burst (waktu yang diperlukan untuk menjalankan proses).
---
4. Input dan Pengurutan Berdasarkan Arrival Time
Setelah mendapatkan input jumlah proses, kode ini akan mengurutkan proses berdasarkan Arrival Time (AT). Proses dengan arrival time lebih awal akan diproses terlebih dahulu.
**for (int i = 0; i < n - 1; i++)
    for (j = 0; j < n - i - 1; j++)    
        if (p[j].at > p[j + 1].at) {
            temp = p[j];
            p[j] = p[j + 1];
            p[j + 1] = temp;
        }**
•	Kode ini menggunakan algoritma Bubble Sort untuk mengurutkan proses berdasarkan arrival time.
---
6. Penentuan Proses Pertama
Setelah pengurutan berdasarkan arrival time, kode mencari proses dengan burst time paling kecil di antara proses yang tiba pada waktu yang sama (arrival time yang sama).
for (j = 1; j < n && p[j].at == p[0].at; j++)
    if (p[j].bt < p[min].bt)
        min = j;
temp = p[0];
p[0] = p[min];
p[min] = temp;
•	Proses dengan burst time terkecil di antara proses yang tiba pertama kali akan dipilih untuk dieksekusi pertama.
---
8. Perhitungan Completion Time, Turnaround Time, dan Waiting Time
Pada bagian ini, kode menghitung Completion Time (CT), Turnaround Time (TAT), dan Waiting Time (WT) untuk setiap proses:
•	Completion Time (CT): Waktu selesai eksekusi proses, dihitung dari waktu mulai eksekusi ditambah dengan burst time.
•	Turnaround Time (TAT): Selisih antara waktu selesai dan arrival time (CT - AT).
•	Waiting Time (WT): Selisih antara turnaround time dan burst time (TAT - BT).
p[0].it = p[0].at;
p[0].ct = p[0].it + p[0].bt;
for (int i = 1; i < n; i++) {
    for (j = i + 1, min = i; j < n && p[j].at <= p[i - 1].ct; j++)
        if (p[j].bt < p[min].bt)
            min = j;
    temp = p[i];
    p[i] = p[min];
    p[min] = temp;
    if (p[i].at <= p[i - 1].ct)
        p[i].it = p[i - 1].ct;
    else
        p[i].it = p[i].at;
    p[i].ct = p[i].it + p[i].bt;
}
•	Proses 1 akan memulai eksekusi berdasarkan arrival time-nya.
•	Proses berikutnya akan dimulai setelah proses sebelumnya selesai, dengan mempertimbangkan burst time terkecil di antara proses yang sudah tiba.
---
10. Output Hasil
Setelah perhitungan selesai, program akan menampilkan informasi untuk setiap proses seperti nomor proses, arrival time, burst time, completion time, turnaround time, waiting time, dan response time. Selain itu, program juga menghitung dan menampilkan rata-rata Turnaround Time dan rata-rata Waiting Time.
for (int i = 0; i < n; i++) {
    p[i].tat = p[i].ct - p[i].at;
    avgtat += p[i].tat;
    p[i].wt = p[i].tat - p[i].bt;
    avgwt += p[i].wt;
    printf("P%d\t\t%d\t%d\t%d\t%d\t%d\t%d\n", p[i].no, p[i].at, p[i].bt, p[i].ct, p[i].tat, p[i].wt, p[i].wt);
}
avgtat /= n, avgwt /= n;
printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f", avgtat, avgwt);
•	Average TurnAroundTime: Rata-rata waktu yang dibutuhkan untuk setiap proses dari kedatangan hingga selesai.
•	Average WaitingTime: Rata-rata waktu yang dihabiskan oleh proses dalam antrian sebelum dieksekusi.
---
12. Potensi Masalah atau Kekurangan
•	Tidak Mempertimbangkan Preemption: Algoritma ini menggunakan pendekatan non-preemptive, yang berarti proses yang sedang berjalan tidak dapat dihentikan hingga selesai.
•	Masalah Jika Ada Proses Dengan Arrival Time Sama: Jika lebih dari satu proses memiliki arrival time yang sama, algoritma ini memilih berdasarkan burst time terpendek. Ini mungkin tidak ideal jika terdapat banyak proses dengan arrival time yang sama.
Kesimpulan
Kode ini memberikan implementasi algoritma Shortest Job First (SJF) dengan arrival time yang mempertimbangkan kedatangan proses dan memilih proses dengan burst time terkecil untuk dieksekusi terlebih dahulu. Ini adalah implementasi sederhana dan efektif untuk memahami dasar-dasar SJF, meskipun ada beberapa aspek yang bisa ditingkatkan, seperti mempertimbangkan
Output: 
 
# Gantt Chart dan Data Proses

| Process | AT | BT | CT | TAT | WT |
|---------|----|----|----|-----|----|
| P1      | 0  | 8  | 8  | 8   | 0  |
| P2      | 1  | 4  | 12 | 11  | 7  |
| P4      | 3  | 5  | 17 | 14  | 9  |
| P3      | 2  | 9  | 26 | 24  | 15 |

## Gantt Chart

|  P1   |  P2  |  P4  |     P3     |
|-------|-------|-------|------------|
0       8      12      17           26



---


## SRTF Scheduling Algorithm (Preemptive)
*SRTF adalah versi preemptive dari algoritma SJF (Shortest Job First). Pada algoritma ini, CPU selalu memilih proses dengan sisa burst time paling pendek di antara semua proses yang sudah tiba (arrival time ≤ waktu saat ini).
Jika ada proses baru yang masuk dan memiliki burst time lebih kecil dari proses yang sedang berjalan, maka proses yang sedang berjalan akan dihentikan sementara (preempted) dan digantikan oleh proses baru tersebut.*
--
Analisis Kode:
1. Struktur Data
struct proc {
    int no, at, bt, rt, ct, tat, wt;
};
•	no: Nomor proses.
•	at: Arrival time (waktu kedatangan proses).
•	bt: Burst time (waktu eksekusi awal).
•	rt: Remaining time (waktu tersisa untuk eksekusi).
•	ct: Completion time (waktu selesai eksekusi).
•	tat: Turnaround time (waktu total yang dibutuhkan untuk eksekusi, CT - AT).
•	wt: Waiting time (waktu tunggu, TAT - BT).
---
2. Fungsi read()
Fungsi ini digunakan untuk membaca input dari pengguna, yaitu arrival time (AT) dan burst time (BT) untuk setiap proses. Fungsi ini juga menetapkan remaining time (rt) sama dengan burst time awal.

struct proc read(int i) {
    struct proc p;
    printf("\nProcess No: %d\n", i);
    p.no = i;
    printf("Enter Arrival Time: ");
    scanf("%d", &p.at);
    printf("Enter Burst Time: ");
    scanf("%d", &p.bt);
    p.rt = p.bt;
    return p;
}

•	Arrival time (at) dan burst time (bt) diminta dari pengguna.
•	Remaining time (rt) diinisialisasi dengan nilai burst time (bt) karena ini adalah waktu yang dibutuhkan untuk menyelesaikan eksekusi proses.

---
3. Input dan Pengurutan Proses
Setelah menerima input dari pengguna, kode mengurutkan proses berdasarkan arrival time (AT) secara ascending. Pengurutan ini memastikan bahwa proses yang datang lebih awal akan diproses terlebih dahulu.

for (int i = 0; i < n - 1; i++)
    for (int j = 0; j < n - i - 1; j++)    
        if (p[j].at > p[j + 1].at) {
            temp = p[j];
            p[j] = p[j + 1];
            p[j + 1] = temp;
        }
•	Bubble sort digunakan untuk mengurutkan proses berdasarkan arrival time.

---
4. Proses Eksekusi dengan SRTF
Di bagian ini, algoritma SRTF dijalankan. Program mengecek pada setiap unit waktu (time) proses mana yang memiliki waktu tersisa (remaining time) paling kecil dan belum selesai dieksekusi (rt > 0). Proses dengan waktu tersisa paling kecil akan dilanjutkan eksekusinya.
for (time = 0; remain != n; time++) {
    s = 9;
    for (int i = 0; i < n; i++)
        if (p[i].at <= time && p[i].rt < p[s].rt && p[i].rt > 0)
            s = i;
    p[s].rt--;
    if (p[s].rt == 0) {
        remain++;
        p[s].ct = time + 1;
        p[s].tat = p[s].ct - p[s].at;
        avgtat += p[s].tat;
        p[s].wt = p[s].tat - p[s].bt;
        avgwt += p[s].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n", p[s].no, p[s].at, p[s].bt, p[s].ct, p[s].tat, p[s].wt);
    }
}

•	remain digunakan untuk menghitung jumlah proses yang telah selesai.
•	Pada setiap unit waktu, program memilih proses dengan remaining time (rt) terkecil yang sudah tiba (arrival time ≤ waktu saat ini) dan mengurangi remaining time (rt) proses tersebut.
•	Completion time (ct) dihitung saat proses selesai, dan turnaround time (tat) serta waiting time (wt) dihitung berdasarkan waktu selesai dan burst time.
•	Program mencetak informasi untuk setiap proses seperti nomor proses, arrival time, burst time, completion time, turnaround time, dan waiting time.

---
5. Perhitungan Rata-rata Waktu
Setelah semua proses selesai, kode menghitung rata-rata turnaround time (TAT) dan waiting time (WT) dari semua proses.
avgtat /= n, avgwt /= n;
printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f", avgtat, avgwt);

•	Average Turnaround Time: Rata-rata waktu yang dibutuhkan proses dari kedatangan hingga selesai.
•	Average Waiting Time: Rata-rata waktu tunggu proses sebelum dieksekusi.

---
6. Potensi Masalah atau Kekurangan
•	Proses dengan Arrival Time yang Sama: Kode ini menangani kondisi ketika beberapa proses memiliki arrival time yang sama dengan memilih proses yang memiliki remaining time paling kecil. Ini adalah solusi sederhana, tetapi mungkin kurang efisien pada kondisi tertentu.
•	Tidak Ada Penanganan Error: Kode tidak memeriksa apakah input dari pengguna valid atau tidak. Jika pengguna memasukkan nilai yang tidak valid (misalnya, angka negatif untuk burst time), program tetap akan berjalan tanpa memberikan peringatan.
•	Output Tidak Termasuk Response Time: Kolom RT (Response Time) yang biasanya digunakan dalam penjadwalan preemptive tidak dihitung dalam program ini.
Kode ini mengimplementasikan algoritma Shortest Remaining Time First (SRTF) yang preemptive, yang memilih proses dengan waktu eksekusi tersisa paling pendek pada setiap unit waktu dan mengeksekusinya. Algoritma ini sering digunakan untuk sistem yang harus melakukan penjadwalan proses dengan mempertimbangkan perubahan dalam waktu eksekusi secara dinamis. Program ini mencetak informasi tentang setiap proses, serta menghitung rata-rata waktu turnaround dan waiting time.
Namun, ada beberapa aspek yang bisa diperbaiki, seperti validasi input dan perhitungan response time.

---

# Gantt Chart dan Data Proses

| Process | AT | BT | CT | TAT | WT |
|---------|----|----|----|-----|----|
| P2      | 1  | 4  | 5  | 4   | 0  |
| P4      | 3  | 5  | 10 | 7   | 2  |
| P1      | 0  | 8  | 17 | 17  | 9  |
| P3      | 2  | 9  | 26 | 24  | 15 |

## Gantt Chart

|  P2  |  P4  |   P1   |     P3     |
|------|-------|--------|------------|
1      5       10       17           26


---
