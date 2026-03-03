# Measure Distance

## 1. Pengertian

Dalam penambangan data (data mining), mengukur jarak digunakan untuk
mengetahui tingkat kemiripan atau perbedaan antara dua data. Semakin
kecil nilai jarak, maka semakin mirip kedua data tersebut. Semakin besar
nilai jarak, maka semakin berbeda.

Konsep ini banyak digunakan pada algoritma seperti: - K-Nearest Neighbor
(KNN) - K-Means Clustering - Hierarchical Clustering - DBSCAN

------------------------------------------------------------------------

## 2. Jenis-Jenis Pengukuran Jarak

### 2.1 Euclidean Distance

Rumus:

d = √((x1 - x2)\^2 + (y1 - y2)\^2)

Digunakan untuk data numerik kontinu dan merupakan jarak garis lurus
antara dua titik.

Cocok untuk: - K-Means - KNN - Data numerik

------------------------------------------------------------------------

### 2.2 Manhattan Distance

Rumus:

d = \|x1 - x2\| + \|y1 - y2\|

Disebut juga City Block Distance karena seperti menghitung jarak di
jalan kota.

Cocok untuk: - Data berdimensi tinggi - Data yang memiliki kemungkinan
outlier

------------------------------------------------------------------------

### 2.3 Minkowski Distance

Rumus umum:

d = ( Σ \|xi - yi\|\^p )\^(1/p)

Keterangan: - Jika p = 1 → Manhattan Distance - Jika p = 2 → Euclidean
Distance

------------------------------------------------------------------------

### 2.4 Cosine Similarity

Rumus:

cos(θ) = (A · B) / (\|\|A\|\| \|\|B\|\|)

Digunakan untuk mengukur sudut antar dua vektor.

Cocok untuk: - Text Mining - Natural Language Processing (NLP) -
Analisis dokumen

Nilai mendekati 1 berarti semakin mirip.

------------------------------------------------------------------------

### 2.5 Hamming Distance

Digunakan untuk data biner atau kategorikal.

Menghitung jumlah posisi yang berbeda antara dua data.

Contoh: 101110 100100

Berbeda pada 2 posisi → jarak = 2

------------------------------------------------------------------------

## 3. Pentingnya Normalisasi Data

Jika fitur memiliki skala berbeda (misalnya tinggi dalam cm dan gaji
dalam juta), maka fitur dengan nilai besar akan lebih dominan dalam
perhitungan jarak.

Solusi: - Min-Max Scaling - Standardisasi (Z-Score)

------------------------------------------------------------------------

## 4. Kesimpulan

Mengukur jarak dalam penambangan data bertujuan untuk: - Menentukan
tingkat kemiripan antar data - Membentuk cluster - Menentukan tetangga
terdekat - Membantu proses klasifikasi

Pemilihan metode jarak harus disesuaikan dengan jenis data dan tujuan
analisis.
