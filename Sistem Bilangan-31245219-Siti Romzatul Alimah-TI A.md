# tugas-sistem-informasi
## Siti Romzatul Alimah
## NRP 3124521019
## TI A 1 PENS LA
# Latihan Sistem Bilangan


## 1. Pertanyaan Dasar
1. a. Bilangan biner adalah bilangan yang berbasis **Dua (2)**  
   b. Bilangan heksadesimal adalah bilangan yang berbasis **Enam Belas (16)**  

## 2. Konversi Bilangan
###  Konversi Desimal ke Biner
**1234₁₀ ke biner:**
```
1234 ÷ 2 = 617  sisa 0
617 ÷ 2 = 308  sisa 1
308 ÷ 2 = 154  sisa 0
154 ÷ 2 = 77   sisa 0
77 ÷ 2 = 38   sisa 1
38 ÷ 2 = 19   sisa 0
19 ÷ 2 = 9     sisa 1
9 ÷ 2 = 4     sisa 1
4 ÷ 2 = 2     sisa 0
2 ÷ 2 = 1     sisa 0
1 ÷ 2 = 0     sisa 1
```
**Hasil:** `10011010010₂`

### 3. Konversi Biner ke Desimal
**10101010₂ ke desimal:**
```
(1 × 2⁷) + (0 × 2⁶) + (1 × 2⁵) + (0 × 2⁴) + (1 × 2³) + (0 × 2²) + (1 × 2¹) + (0 × 2⁰)
= 128 + 0 + 32 + 0 + 8 + 0 + 2 + 0
= 170
```
**Hasil:** `170₁₀`

### 4. Konversi Biner ke Oktal
**101011111001₂ ke oktal:**
```
101 011 111 001
5   3   7   1
```
**Hasil:** `5371₈`

### 5. Konversi Oktal ke Biner
**2170₈ ke biner:**
```
2 → 010
1 → 001
7 → 111
0 → 000
```
**Hasil:** `010001111000₂`

### 6. Konversi Desimal ke Heksadesimal
**1780₁₀ ke heksadesimal:**
```
1780 ÷ 16 = 111  sisa 4
111 ÷ 16 = 6    sisa F
6 ÷ 16 = 0    sisa 6
```
**Hasil:** `06F4₁₆`

### 7. Konversi Heksadesimal ke Desimal
**ABCD₁₆ ke desimal:**
```
A = 10 × 16³ = 40960
B = 11 × 16² = 2816
C = 12 × 16¹ = 192
D = 13 × 16⁰ = 13
Total = 43981₁₀
```
**Hasil:** `43981₁₀`

### 8. Konversi Pecahan Desimal ke Biner
**0,3125₁₀ ke biner:**
```
0,3125 × 2 = 0,625 → 0
0,625 × 2 = 1,250 → 1
0,250 × 2 = 0,500 → 0
0,500 × 2 = 1,000 → 1
```
**Hasil:** `0.0101₂`

### 9. Konversikan bilangan desimal di bawah ini ke dalam bilangan biner
**a. 11,625₁₀**

- **Pembagian berulang dengan 2 (11₁₀):**
  ```
  11 ÷ 2 = 5 sisa 1
  5 ÷ 2 = 2 sisa 1
  2 ÷ 2 = 1 sisa 0
  1 ÷ 2 = 0 sisa 1
  ```
  **Hasil bilangan bulat:** `1011₂`

- **Perkalian berulang dengan 2 (0,625₁₀):**
  ```
  0,625 × 2 = 1,25 → 1
  0,25 × 2 = 0,50 → 0
  0,50 × 2 = 1,00 → 1
  ```
  **Hasil bilangan pecahan:** `101₂`

**Hasil akhir:** `1011.101₂`

### 10. Konversikan bilangan desimal di bawah ini ke dalam bilangan heksadesimal
**a. 348,654₁₀**

- **Pembagian berulang dengan 16 (348₁₀):**
  ```
  348 ÷ 16 = 21 sisa 12 (C)
  21 ÷ 16 = 1 sisa 5 (5)
  1 ÷ 16 = 0 sisa 1 (1)
  ```
  **Hasil bilangan bulat:** `15C₁₆`

- **Perkalian berulang dengan 16 (0,654₁₀):**
  ```
  0,654 × 16 = 10,464 → A
  0,464 × 16 = 7,424 → 7
  0,424 × 16 = 6,784 → 6
  0,784 × 16 = 12,544 → C
  ```
  **Hasil bilangan pecahan:** `A76C₁₆`

**Hasil akhir:** `15C.A76C₁₆`

### 11. Konversikan bilangan di bawah ini ke dalam bilangan desimal
**a. 010100011,001111101₂**

- **Konversi bilangan bulat ke desimal:**
  ```
  (0×2⁸) + (1×2⁷) + (0×2⁶) + (1×2⁵) + (0×2⁴) + (0×2³) + (0×2²) + (1×2¹) + (1×2⁰)
  = 0 + 128 + 0 + 32 + 0 + 0 + 0 + 2 + 1
  = 163
  ```
  **Hasil bilangan bulat:** `163₁₀`

- **Konversi bilangan pecahan ke desimal:**
  ```
  (0×2⁻¹) + (0×2⁻²) + (1×2⁻³) + (1×2⁻⁴) + (1×2⁻⁵) + (1×2⁻⁶) + (1×2⁻⁷) + (0×2⁻⁸) + (1×2⁻⁹)
  = 0 + 0 + 0.125 + 0.0625 + 0.03125 + 0.015625 + 0.0078125 + 0 + 0.001953125
  = 0.244140625
  ```
  **Hasil bilangan pecahan:** `0.245₁₀`

**Hasil akhir:** `163.245₁₀`

### 12. Konversi Bilangan ke BCD
**10100110000111₂ ke BCD:**
```
Dipisah 4 digit dari kanan:
0010 = 2
1001 = 9
1000 = 8
0111 = 7
```
**Hasil:** `2987 (BCD)`

### 13. Rubahlah bentuk BCD di bawah ini ke dalam bilangan biner
**a. 1987**

- **Konversi BCD (4 bit per digit):**
  ```
  1 = 0001
  9 = 1001
  8 = 1000
  7 = 0111
  ```
  **Hasil:** `0001100110000111` (0 dua di depan dihilangkan)

**Hasil akhir:** `01 1001 1000 0111₂`

### 14. Rubahlah bilangan biner di bawah ini ke dalam BCO
**a. 11111101001₂**

- **Dipisah 3 digit dari kanan, ditambah 0 dua di depan:**
  ```
  0011 = 3
  0111 = 7
  0101 = 5
  0001 = 1
  ```
  **Hasil:** `3751₈`
  
### 15. Rubahlah bilangan biner di bawah ini ke dalam BCH
**a. 1101111100101110₂**

- **Dibagi 4-bit:**
  ```
  1101 = C
  1111 = F
  0010 = 2
  1110 = E
  ```
  **Hasil:** `CF2E₁₆`

  ### 16. Rubahlah bentuk BCH di bawah ini ke dalam bilangan heksadesimal
**a. F0DE**

- **Dikonversi ke biner:**
  ```
  F = 1111
  0 = 0000
  D = 1101
  E = 1110
  ```
  **Hasil:** `1111000011011110₂`

### 17. Nyatakan positif atau negatif bilangan biner di bawah ini
**a. 01111111₂**

- **MSB (bit pertama) = 0, bilangan ini positif:**
  ```
  = (0×2⁷) + (1×2⁶) + (1×2⁵) + (1×2⁴) + (1×2³) + (1×2²) + (1×2¹) + (1×2⁰)
  = 0 + 64 + 32 + 16 + 8 + 4 + 2 + 1
  = 127₁₀
  ```
  **Hasil:** `Positif 127`

  #### **18. Nyatakan bilangan biner negatif di bawah ini ke dalam bilangan desimal:**

**a. 10001000₂**

- **Hitung komplemen dua:**
  ```
  Inversi: 01110111
  Tambahkan 1: 01111000
  ```

- **Konversi ke desimal:**
  ```
  (0×2⁷) + (1×2⁶) + (1×2⁵) + (1×2⁴) + (1×2³) + (0×2²) + (0×2¹) + (0×2⁰)
  = 0 + 64 + 32 + 16 + 8 + 0 + 0 + 0
  = 120₁₀
  ```
  **Hasil:** `-120₁₀`

### 19. Nyatakan ASCII Code dalam Karakter
**41₁₆ ke ASCII:**
```
41₁₆ = 65₁₀ → 'A'
```
**Hasil:** `A`

#### **20. Nyatakan karakter di bawah ini dalam ASCII Code:**
| Karakter | ASCII Desimal | ASCII Heksadesimal |
|----------|--------------|--------------------|
| a        | 97           | 61₁₆              |
| x        | 120          | 78₁₆              |
| m        | 109          | 6D₁₆              |
| H        | 72           | 48₁₆              |

**Hasil:** ` 61₁₆ `


### 21. Representasi ASCII dari "PRINT X"
```
P = 50₁₆ (1010000₂)
R = 52₁₆ (1010010₂)
I = 49₁₆ (1001001₂)
N = 4E₁₆ (1001110₂)
T = 54₁₆ (1010100₂)
Spasi = 20₁₆ (00100000₂)
X = 58₁₆ (1011000₂)
```
**Hasil:** `50 52 49 4E 54 20 58₁₆`
