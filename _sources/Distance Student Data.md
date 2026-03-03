# Distance in Student Data

**perhitungan manual** menggunakan **2 mahasiswa dari dataset asli (misal diambil dari baris pertama dan kedua dataset)**:

* Numerik → Normalisasi (range)
* Nominal → Simple Matching
* Ordinal → Ranking + Normalisasi
* Binary → Simple Matching

## **Data Dua Mahasiswa**

Misalkan dari dataset diperoleh:

| Atribut            | Mahasiswa 1 | Mahasiswa 2 |
|--------------------|------------|------------|
| Usia               | 18         | 25         |
| Semester           | 5          | 3          |
| IPK                | 2.22       | 3.72       |
| Jumlah_Organisasi  | 1          | 4          |
| Jenis_Kelamin      | Perempuan  | Perempuan  |
| Program_Studi      | Manajemen  | Sistem Informasi |
| Tingkat_Kepuasan   | Sedang     | Rendah     |
| Motivasi_Belajar   | Rendah     | Sangat Tinggi |
| Status_Beasiswa    | Tidak      | Ya |
| Status_Kerja       | Part Time  | Full Time | 


## **Tentukan Rentang (Range) Numerik**

Dari dataset:

* Usia: 18 – 25 → Range = 7
* Semester: 1 – 8 → Range = 7
* IPK: 2.00 – 3.99 → Range = 1.99
* Jumlah_Organisasi: 0 – 5 → Range = 5

## **Hitung Jarak Tiap Atribut**

### **A. Atribut Numerik (Normalisasi)**

- ##### **Usia**

$$
|18 - 25| / 7 = 7/7 = 1
$$

- ##### **Semester**

$$
|5 - 3| / 7 = 2/7 = 0.29
$$

- ##### **IPK**

$$
|2.22 - 3.72| / 1.99 = 1.50 / 1.99 = 0.75
$$

- ##### **Jumlah Organisasi**

$$
|1 - 4| / 5 = 3/5 = 0.60
$$

### **B. Atribut Nominal (Simple Matching)**

- ##### **Jenis_Kelamin**

Sama → 0

- ##### **Program_Studi**

Berbeda → 1

- ##### **Status_Kerja**

Berbeda → 1

### **C. Atribut Binary**

##### **Status_Beasiswa**

Berbeda (Tidak vs Ya) → 1

### **D. Atribut Ordinal**

##### **Konversi Ranking**

Tingkat_Kepuasan:

- Rendah = 1
- Sedang = 2
- Tinggi = 3

Motivasi_Belajar:

- Sangat Rendah = 1
- Rendah = 2
- Sedang = 3
- Tinggi = 4
- Sangat Tinggi = 5

##### **Tingkat_Kepuasan**

Mahasiswa 1 = Sedang (2)  
Mahasiswa 2 = Rendah (1)  

Normalisasi:

$$
z = \frac{r - 1}{M - 1}
$$

Karena M = 3

Mahasiswa 1:

$$
(2 - 1)/(3 - 1) = 1/2 = 0.5
$$

Mahasiswa 2:

$$
(1 - 1)/(3 - 1) = 0/2 = 0
$$

Jarak:

$$
|0.5 - 0| = 0.5
$$

##### **Motivasi_Belajar**

Mahasiswa 1 = Rendah (2)  
Mahasiswa 2 = Sangat Tinggi (5)  

M = 5

Mahasiswa 1:

Mahasiswa 1:

$$
(2 - 1)/4 = 1/4 = 0.25
$$

Mahasiswa 2:

$$
(5 - 1)/4 = 4/4 = 1
$$

Jarak:

$$
|0.25 - 1| = 0.75
$$

## **Hitung Total Jarak (Metode Campuran / Gower)**

Jumlah atribut yang dihitung = 10

$$
D = \frac{\text{Total seluruh jarak}}{10}
$$

##### **Total Seluruh Jarak**

$$
1 + 0.29 + 0.75 + 0.60 + 0 + 1 + 1 + 1 + 0.5 + 0.75 = 6.89
$$

##### **Hitung Nilai Akhir**

$$
D = \frac{6.89}{10}
$$

$$
D = 0.689
$$

## **Interpretasi**

Nilai dissimilarity:

$$
D = 0.689
$$

Karena mendekati 1, maka kedua mahasiswa ini **cukup berbeda**.

Perbedaan terbesar terdapat pada:

- Usia
- IPK
- Motivasi Belajar
- Program Studi
- Status Beasiswa
- Status Kerja

Artinya tingkat kemiripan rendah dan karakteristik keduanya cukup berbeda.

## Implementasi Orange

```{figure} /img/Distance_Orange.png
---
width: 100%
fig-margin : 0
---
```

```{figure} /img/Distance.png
---
width: 50%
fig-margin : 0
---
```

Perbedaan nilai jarak antara perhitungan manual dan hasil pada Orange terjadi karena pada perhitungan manual digunakan konsep Gower Distance yang menormalisasi tiap atribut dan menghitung rata-rata jarak. Sedangkan pada Orange, data kategorikal terlebih dahulu diubah menjadi numerik menggunakan one-hot encoding melalui widget Continuize, kemudian jarak dihitung menggunakan Euclidean Distance. Perbedaan metode ini menyebabkan nilai jarak yang dihasilkan tidak identik.