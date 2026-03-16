# KNN Missing Value

Contoh ini menunjukkan cara menentukan **nilai usia yang hilang pada
data ke‑10** menggunakan metode **K‑Nearest Neighbor (KNN)**.

Atribut pada dataset:

-   Usia
-   Tingkat_Kepuasan
-   Status_Beasiswa
-   Program_Studi

Untuk memprediksi **Usia**, atribut pembanding yang digunakan:

-   Tingkat_Kepuasan
-   Status_Beasiswa
-   Program_Studi

# Perhitungan Missing Value Menggunakan Euclidean Distance

## Data Mahasiswa

| Data ke | Usia | Tingkat_Kepuasan | Status_Beasiswa | Program_Studi |
|--------|------|------------------|-----------------|---------------|
| 1 | 18 | Sedang | Tidak | Manajemen |
| 2 | 25 | Rendah | Ya | Sistem Informasi |
| 3 | 20 | Tinggi | Tidak | Akuntansi |
| 4 | 21 | Sedang | Ya | Manajemen |
| 5 | 19 | Rendah | Tidak | Sistem Informasi |
| 6 | 22 | Tinggi | Ya | Akuntansi |
| 7 | 23 | Tinggi | Tidak | Manajemen |
| 8 | 24 | Sedang | Ya | Sistem Informasi |
| 9 | 20 | Rendah | Tidak | Akuntansi |
| 10 | ? | Sedang | Ya | Manajemen |

Pada data ke-10 terdapat **missing value pada atribut Usia**, sehingga perlu dilakukan estimasi nilai menggunakan **Euclidean Distance** dengan pendekatan **K-Nearest Neighbor (KNN)**.

Karena Euclidean Distance hanya dapat digunakan pada data numerik, maka atribut kategorikal perlu diubah menjadi bentuk numerik terlebih dahulu.

---

# Transformasi Data Kategorikal
Tingkat Kepuasan

| Kategori | Nilai |
|----------|------|
| Rendah | 1 |
| Sedang | 2 |
| Tinggi | 3 |

Status Beasiswa

| Kategori | Nilai |
|----------|------|
| Tidak | 0 |
| Ya | 1 |

Program Studi

| Program Studi | Nilai |
|---------------|------|
| Manajemen | 1 |
| Sistem Informasi | 2 |
| Akuntansi | 3 |

# Data Setelah Transformasi

| Data | Usia | Kepuasan | Beasiswa | Prodi |
|-----|------|---------|---------|------|
| 1 | 18 | 2 | 0 | 1 |
| 2 | 25 | 1 | 1 | 2 |
| 3 | 20 | 3 | 0 | 3 |
| 4 | 21 | 2 | 1 | 1 |
| 5 | 19 | 1 | 0 | 2 |
| 6 | 22 | 3 | 1 | 3 |
| 7 | 23 | 3 | 0 | 1 |
| 8 | 24 | 2 | 1 | 2 |
| 9 | 20 | 1 | 0 | 3 |
| 10 | ? | 2 | 1 | 1 |

Perhitungan jarak dilakukan dengan **mengabaikan atribut usia** karena nilainya hilang.

# Rumus Euclidean Distance

$
d(p,q) = \sqrt{(x_1-x_2)^2 + (x_2-x_2)^2 + ... + (x_n-x_n)^2}
$

Pada kasus ini atribut yang digunakan:

- Tingkat Kepuasan
- Status Beasiswa
- Program Studi

# Perhitungan Jarak Data ke-10 dengan Data Lain

#### Data 1

$
d = \sqrt{(2-2)^2 + (1-0)^2 + (1-1)^2}
$

$
d = \sqrt{0 + 1 + 0}
$

$
d = 1
$

---

#### Data 2

$
d = \sqrt{(2-1)^2 + (1-1)^2 + (1-2)^2}
$

$
d = \sqrt{1 + 0 + 1}
$

$
d = \sqrt{2} = 1.41
$

---

#### Data 3

$
d = \sqrt{(2-3)^2 + (1-0)^2 + (1-3)^2}
$

$
d = \sqrt{1 + 1 + 4}
$

$
d = \sqrt{6} = 2.45
$

---

#### Data 4

$
d = \sqrt{(2-2)^2 + (1-1)^2 + (1-1)^2}
$

$
d = \sqrt{0 + 0 + 0}
$

$
d = 0
$

---

#### Data 5

$
d = \sqrt{(2-1)^2 + (1-0)^2 + (1-2)^2}
$

$
d = \sqrt{1 + 1 + 1}
$

$
d = \sqrt{3} = 1.73
$

---

#### Data 6

$
d = \sqrt{(2-3)^2 + (1-1)^2 + (1-3)^2}
$

$
d = \sqrt{1 + 0 + 4}
$

$
d = \sqrt{5} = 2.23
$

---

#### Data 7

$
d = \sqrt{(2-3)^2 + (1-0)^2 + (1-1)^2}
$

$
d = \sqrt{1 + 1 + 0}
$

$
d = \sqrt{2} = 1.41
$

---

#### Data 8

$
d = \sqrt{(2-2)^2 + (1-1)^2 + (1-2)^2}
$

$
d = \sqrt{0 + 0 + 1}
$

$
d = 1
$

---

#### Data 9

$
d = \sqrt{(2-1)^2 + (1-0)^2 + (1-3)^2}
$

$
d = \sqrt{1 + 1 + 4}
$

$
d = \sqrt{6} = 2.45
$

---

# Hasil Perhitungan Jarak

| Data | Usia | Jarak |
|-----|------|------|
| 4 | 21 | 0 |
| 1 | 18 | 1 |
| 8 | 24 | 1 |
| 2 | 25 | 1.41 |
| 7 | 23 | 1.41 |
| 5 | 19 | 1.73 |
| 6 | 22 | 2.23 |
| 3 | 20 | 2.45 |
| 9 | 20 | 2.45 |

---

# Menentukan Nilai K

Misalkan digunakan **K = 3** tetangga terdekat.

Data terdekat:

| Data | Usia | Jarak |
|-----|------|------|
| 4 | 21 | 0 |
| 1 | 18 | 1 |
| 8 | 24 | 1 |

---

# Menghitung Estimasi Usia

$
Usia = \frac{21 + 18 + 24}{3}
$

$
Usia = \frac{63}{3}
$

$
Usia = 21
$

---

# Hasil Imputasi Missing Value

Nilai **Usia pada data ke-10** diperkirakan sebesar:

$
Usia = 21
$

Sehingga data yang telah diperbaiki menjadi:

| Data ke | Usia | Tingkat_Kepuasan | Status_Beasiswa | Program_Studi |
|--------|------|------------------|-----------------|---------------|
| 10 | **21** | Sedang | Ya | Manajemen |

---