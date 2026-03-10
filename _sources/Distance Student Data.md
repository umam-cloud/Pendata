---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---


# Distance in Student Data

**perhitungan manual** menggunakan **2 mahasiswa dari dataset asli (misal diambil dari baris pertama dan kedua dataset)**:

* Numerik → Normalisasi
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


## **Hitung Jarak Tiap Atribut**

### **A. Atribut Numerik (Normalisasi)**
### **Euclidean**

Kita ambil sampel data pertama dan kedua untuk menghitung jarak dari kedua data tersebut. Fitur yang merupakan tipe data numerik adalah `Usia`, `Semester`, `IPK`, `Jumlah_Organisasi`.
Dari fitur Tersebut, diambil data pertama dan kedua untuk dihitung jaraknya, dan didapatkan hasilnya sebagai berikut 

$$
d(\mathbf{p}, \mathbf{q}) = \sqrt{\sum_{i=1}^{n} (p_i - q_i)^2}
$$

$$
d(\mathbf{1}, \mathbf{2}) = \sqrt{(18-25)^2 + (5-3)^2 + (2.22-3.72)^2 + (1-4)^2}
$$

$$
d(\mathbf{1}, \mathbf{2}) = \sqrt{49+4+2.25+9}
$$

$$
d(\mathbf{1}, \mathbf{2}) = \sqrt{64.25} = 8.02
$$

### Implementasi Euclidean Orange

```{figure} /img/euclidean_numerik.png
---
width: 40%
fig-margin : 0
---
```


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

## **Hitung Total Jarak**
$$
8.016+ 0 + 1 + 1 + 1 + 0.5 + 0.75 = 12.266
$$

Hitung Nilai Akhir : 

$$
\sqrt{12.266}
$$

Hasil akhir jarak Euclidean antara data 1 dan data 2 adalah sekitar :

$$
3.501
$$


## Implementasi Orange

```{figure} /img/Distance_Orange.png
---
width: 100%
fig-margin : 0
---
```

```{figure} /img/Distance.png
---
width: 40%
fig-margin : 0
---
```

Perbedaan nilai jarak antara perhitungan manual dan hasil pada Orange terjadi karena pada perhitungan manual digunakan konsep Gower Distance yang menormalisasi tiap atribut dan menghitung rata-rata jarak. Sedangkan pada Orange, data kategorikal terlebih dahulu diubah menjadi numerik menggunakan one-hot encoding melalui widget Continuize, kemudian jarak dihitung menggunakan Euclidean Distance. Perbedaan metode ini menyebabkan nilai jarak yang dihasilkan tidak identik.