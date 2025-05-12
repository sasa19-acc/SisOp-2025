# 5.17 Analisis Penjadwalan Proses

## Diketahui

| Proses | Burst Time (ms) | Prioritas |
| ------ | --------------- | --------- |
| P₁     | 5               | 4         |
| P₂     | 3               | 1         |
| P₃     | 1               | 2         |
| P₄     | 7               | 2         |
| P₅     | 4               | 3         |

Semua proses tiba pada waktu **0 ms** dengan urutan **P₁, P₂, P₃, P₄, P₅**.

---

## a. Gantt Chart untuk Setiap Algoritma

### 1. FCFS (First Come First Serve)

```
| P1 | P2 | P3 | P4 | P5 |
0    5    8    9   16   20
```

### 2. SJF (Shortest Job First)

```
| P3 | P2 | P5 | P1 | P4 |
0    1    4    8   13   20
```

### 3. Prioritas (Non-preemptive)

```
| P1 | P5 | P3 | P4 | P2 |
0    5    9   10   17   20
```

### 4. Round Robin (Quantum = 2 ms)

```
| P1 | P2 | P3 | P4 | P5 | P1 | P2 | P4 | P5 | P1 | P4 |
0    2    4    5    7    9   11   12   14   16   18   19   22
```

---

## b. Turnaround Time (TAT)

TAT = Waktu Selesai - Waktu Tiba

| Proses | FCFS | SJF | Prioritas | RR |
| ------ | ---- | --- | --------- | -- |
| P₁     | 5    | 13  | 5         | 19 |
| P₂     | 8    | 4   | 20        | 12 |
| P₃     | 9    | 1   | 10        | 5  |
| P₄     | 16   | 20  | 17        | 22 |
| P₅     | 20   | 8   | 9         | 16 |

---

## c. Waiting Time (WT)

WT = TAT - Burst Time

| Proses | BT | FCFS | SJF | Prioritas | RR |
| ------ | -- | ---- | --- | --------- | -- |
| P₁     | 5  | 0    | 8   | 0         | 14 |
| P₂     | 3  | 5    | 1   | 17        | 9  |
| P₃     | 1  | 8    | 0   | 9         | 4  |
| P₄     | 7  | 9    | 13  | 10        | 15 |
| P₅     | 4  | 16   | 4   | 5         | 12 |

**Rata-rata WT:**

* FCFS: 7.6
* SJF: 5.2
* Prioritas: 8.2
* RR: 10.8

---

## d. Algoritma dengan Waktu Tunggu Rata-rata Minimum

**Shortest Job First (SJF)** menghasilkan rata-rata WT terendah: **5.2 ms**.

## Penjelasan Singkat

* **FCFS**: Sederhana, namun proses panjang di depan memblokir proses pendek (Convoy Effect).
* **SJF**: Eksekusi proses tergantung burst terpendek → proses pendek cepat selesai → WT rata-rata rendah.
* **Prioritas**: Berdasarkan tingkat prioritas; proses prioritas rendah bisa menunggu lama.
* **Round Robin**: Adil dengan quantum tetap, tetapi proses kecil menunggu giliran berkali-kali → WT tinggi.

---

# 5.18 Analisis Penjadwalan dengan Preemptive Priority Round Robin
---
## Diketahui

| Proses | Prioritas | Burst Time (ms) | Arrival Time (ms) |
| ------ | --------- | --------------- | ----------------- |
| P₁     | 5         | 15              | 0                 |
| P₂     | 3         | 20              | 0                 |
| P₃     | 4         | 20              | 20                |
| P₄     | 4         | 20              | 25                |
| P₅     | 5         | 5               | 30                |
| P₆     | 5         | 15              | 55                |

* **Algoritma:** Preemptive, priority-based, Round Robin (quantum = 10 ms)
* **Ketentuan:** Jika datang proses dengan prioritas lebih tinggi, proses yang sedang berjalan dipreempt dan ditempatkan di akhir antrean prioritasnya.

---

## a. Gantt Chart

```text
| P1 | P2 | P3 | P5 | P4 | P3 | P6 | P4 | P2 |
0    15   20   30   35   45   55   70   80   95
```

* **P1**: 0–10 (quantum pertama), 10–15 (sisa 5 ms)
* **P2**: 15–20 (dihentikan karena ada P3 datang)
* **P3**: 20–30 (quantum pertama), 45–55 (sisa 10 ms setelah P4 dan P5 selesai)
* **P5**: 30–35 (burst = 5 ms)
* **P4**: 35–45 (quantum pertama), 70–80 (sisa 10 ms setelah P6 selesai)
* **P6**: 55–65 (quantum pertama), 65–70 (sisa 5 ms)
* **P2**: 80–90 (quantum pertama setelah semua prioritas ≥3 selesai), 90–95 (sisa 5 ms)

---

## b. Turnaround Time (TAT)

TAT = Completion Time − Arrival Time

| Proses | Arrival | Completion | TAT (ms) |
| ------ | ------- | ---------- | -------- |
| P₁     | 0       | 15         | 15       |
| P₂     | 0       | 95         | 95       |
| P₃     | 20      | 55         | 35       |
| P₄     | 25      | 80         | 55       |
| P₅     | 30      | 35         | 5        |
| P₆     | 55      | 70         | 15       |

---

## c. Waiting Time (WT)

WT = TAT − Burst Time

| Proses | Burst | TAT | WT (ms) |
| ------ | ----- | --- | ------- |
| P₁     | 15    | 15  | 0       |
| P₂     | 20    | 95  | 75      |
| P₃     | 20    | 35  | 15      |
| P₄     | 20    | 55  | 35      |
| P₅     | 5     | 5   | 0       |
| P₆     | 15    | 15  | 0       |

---

## Penjelasan Singkat

1. **Preemptive Priority**: Setiap kali datang proses dengan prioritas lebih tinggi, proses yang berjalan langsung dihentikan.
2. **Round Robin**: Jika banyak proses dalam prioritas sama, giliran diberikan berdasarkan quantum 10 ms.
3. **Pengaturan Antrian**: Proses yang dipreempt (karena quantum habis atau kedatangan prioritas lebih tinggi) ditempatkan di akhir antrean dengan prioritas yang sama.

