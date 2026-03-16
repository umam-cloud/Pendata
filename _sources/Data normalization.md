# Normalisasi Data

## Pengertian Normalisasi Data

Normalisasi data adalah proses **mengubah nilai atribut ke dalam skala yang sama** agar tidak ada atribut yang memiliki pengaruh lebih besar dalam proses perhitungan.  

Normalisasi sering digunakan pada algoritma **data mining dan machine learning**, terutama yang berbasis perhitungan jarak seperti:

- KNN (K-Nearest Neighbor)
- WKNN (Weighted KNN)
- Clustering
- Cosine Similarity

Jika data memiliki skala yang berbeda, misalnya **usia (18–25)** dan **IPK (2–4)**, maka atribut dengan nilai yang lebih besar dapat mendominasi perhitungan.

---

# Data Contoh

| Atribut | Mahasiswa 1 | Mahasiswa 2 |
|---|---|---|
| Usia | 18 | 25 |
| Semester | 5 | 3 |
| IPK | 2.22 | 3.72 |
| Jumlah_Organisasi | 1 | 4 |
| Jenis_Kelamin | Perempuan | Perempuan |
| Program_Studi | Manajemen | Sistem Informasi |
| Tingkat_Kepuasan | Sedang | Rendah |
| Motivasi_Belajar | Rendah | Sangat Tinggi |
| Status_Beasiswa | Tidak | Ya |
| Status_Kerja | Part Time | Full Time |

Pada proses normalisasi biasanya **hanya atribut numerik yang dinormalisasi**, seperti:

- Usia  
- Semester
- IPK
- Jumlah Organisasi

---

# 1. Min-Max Normalization

Min-Max Normalization digunakan untuk **mengubah nilai data ke dalam rentang 0 sampai 1**.

## Rumus

$
X' = (X - Xmin) / (Xmax - Xmin)
$

### Contoh pada atribut Usia

- Xmin = 18
- Xmax = 25

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | (18 − 18) / (25 − 18) | 0 |
| 2 | (25 − 18) / (25 − 18) | 1 |

### Contoh pada atribut IPK

- Xmin = 2.22
- Xmax = 3.72

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | (2.22 − 2.22) / (3.72 − 2.22) | 0 |
| 2 | (3.72 − 2.22) / (3.72 − 2.22) | 1 |

### Hasil Normalisasi Min-Max

| Atribut | Mahasiswa 1 | Mahasiswa 2 |
|---|---|---|
| Usia | 0 | 1 |
| Semester | 1 | 0 |
| IPK | 0 | 1 |
| Jumlah_Organisasi | 0 | 1 |

---

# Min-Max Normalization dengan Rentang Baru (New Min dan New Max)

Selain digunakan untuk mengubah data ke rentang **0 sampai 1**, metode **Min-Max Normalization** juga dapat digunakan untuk mengubah data ke **rentang baru yang ditentukan**.

Rentang baru ini disebut:

- **NewMin** → nilai minimum baru
- **NewMax** → nilai maksimum baru

Metode ini berguna ketika suatu algoritma membutuhkan skala tertentu, misalnya:

- 0 – 10
- -1 – 1
- 1 – 100

---

## Rumus

$
X' = (X - Xmin) / (Xmax - Xmin) × (NewMax - NewMin) + NewMin
$

Keterangan:

- **X** = nilai data asli  
- **Xmin** = nilai minimum atribut  
- **Xmax** = nilai maksimum atribut  
- **NewMin** = batas minimum baru  
- **NewMax** = batas maksimum baru  
- **X'** = hasil normalisasi

---

## Contoh pada atribut Usia

Data usia:

- 18
- 25

Nilai minimum = 18  
Nilai maksimum = 25  

Misalkan ingin mengubah data ke rentang **0 sampai 10**.

$
X' = (X - 18) / (25 - 18) × (10 - 0)
$

### Perhitungan

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | (18 − 18) / (25 − 18) × 10 | 0 |
| 2 | (25 − 18) / (25 − 18) × 10 | 10 |

---

## Contoh pada atribut IPK

Data IPK:

- 2.22
- 3.72

Nilai minimum = 2.22  
Nilai maksimum = 3.72  

Rentang baru yang digunakan **0 – 10**

$
X' = (X - 2.22) / (3.72 - 2.22) × 10
$

### Perhitungan

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | (2.22 − 2.22) / (3.72 − 2.22) × 10 | 0 |
| 2 | (3.72 − 2.22) / (3.72 − 2.22) × 10 | 10 |

---

```{note}
Min-Max Normalization tidak hanya digunakan untuk mengubah data ke rentang **0 sampai 1**, tetapi juga dapat digunakan untuk menyesuaikan data ke rentang lain dengan menambahkan **NewMin** dan **NewMax** pada rumus.

Dengan demikian, data dapat disesuaikan dengan kebutuhan algoritma atau analisis yang digunakan tanpa mengubah hubungan antar nilai dalam dataset.
```

# 2. Z-Score Normalization (Standardization)

Z-Score Normalization mengubah data berdasarkan **rata-rata (mean)** dan **standar deviasi**.

## Rumus

$
Z = (X - μ) / σ
$

Keterangan:

- μ = mean (rata-rata)
- σ = standar deviasi

---

## Contoh pada atribut Usia

Data: 18, 25

### Mean

$
μ = (18 + 25) / 2
μ = 21.5
$

### Standar Deviasi

$
σ = √((18 − 21.5)² + (25 − 21.5)²) / 2
σ = 3.5
$

### Normalisasi

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | (18 − 21.5) / 3.5 | -1 |
| 2 | (25 − 21.5) / 3.5 | 1 |

---

# 3. Decimal Scaling Normalization

Metode ini menormalisasi data dengan **membagi nilai data dengan pangkat 10**.

## Rumus

$
X' = X / (10^j)
$

Dimana:

- j = jumlah digit dari nilai terbesar

---

## Contoh pada atribut Usia

Nilai terbesar = 25  
Jumlah digit = 2

$
X' = X / 100
$

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | 18 / 100 | 0.18 |
| 2 | 25 / 100 | 0.25 |

---

## Contoh pada Jumlah Organisasi

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | 1 / 10 | 0.1 |
| 2 | 4 / 10 | 0.4 |

---

# 4. Mean Normalization

Mean normalization menggunakan **rata-rata data untuk menyesuaikan skala**.

## Rumus

$
X' = (X - mean) / (max - min)
$

---

## Contoh pada atribut Usia

Mean = 21.5  
Max = 25  
Min = 18  

| Mahasiswa | Perhitungan | Hasil |
|---|---|---|
| 1 | (18 − 21.5) / 7 | -0.5 |
| 2 | (25 − 21.5) / 7 | 0.5 |

---

# Perbandingan Metode Normalisasi

| Metode | Karakteristik |
|---|---|
| Min-Max | Mengubah data ke rentang 0–1 |
| Z-Score | Menggunakan mean dan standar deviasi |
| Decimal Scaling | Membagi nilai dengan pangkat 10 |
| Mean Normalization | Data dipusatkan di sekitar nilai rata-rata |

---

# Kesimpulan

Normalisasi data merupakan langkah penting dalam proses **preprocessing data** pada data mining. Normalisasi bertujuan untuk menyamakan skala antar atribut sehingga tidak ada atribut yang mendominasi proses perhitungan.

Beberapa metode normalisasi yang umum digunakan antara lain:

- Min-Max Normalization
- Z-Score Normalization
- Decimal Scaling
- Mean Normalization

Pemilihan metode normalisasi bergantung pada karakteristik data dan algoritma yang digunakan dalam analisis.