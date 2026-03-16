# Preprocessing

## 1. Pengertian Preprocessing
**Preprocessing data** adalah proses awal dalam data mining yang bertujuan untuk menyiapkan data mentah agar menjadi data yang bersih, terstruktur, dan siap dianalisis.  

Data yang diperoleh dari berbagai sumber biasanya memiliki masalah seperti:
- Data tidak lengkap (missing value)
- Data tidak konsisten
- Data memiliki skala yang berbeda
- Data mengandung noise atau kesalahan

Oleh karena itu, preprocessing dilakukan agar kualitas data meningkat sehingga hasil analisis atau model yang dihasilkan menjadi lebih akurat.

---

## 2. Tujuan Data Preprocessing
Beberapa tujuan utama preprocessing adalah:

- **Meningkatkan kualitas data**
- **Mengurangi noise atau kesalahan pada data**
- **Menyesuaikan format data agar mudah diproses algoritma**
- **Meningkatkan akurasi hasil data mining**
- **Mempercepat proses analisis data**

---

## 3. Tahapan dalam Data Preprocessing

### 3.1 Data Cleaning
Data cleaning adalah proses membersihkan data dari kesalahan atau ketidakkonsistenan.

Contoh masalah yang diperbaiki:
- Missing value
- Data duplikat
- Kesalahan penulisan
- Outlier

Contoh penanganan:
- Menghapus data yang kosong
- Mengisi nilai kosong dengan mean atau median
- Menghapus data duplikat

Contoh:

| Nama | Umur | IPK |
|-----|-----|-----|
| Andi | 20 | 3.5 |
| Budi | - | 3.2 |

Nilai umur yang kosong dapat diisi dengan rata-rata umur.

---

### 3.2 Data Integration
Data integration adalah proses menggabungkan data dari berbagai sumber menjadi satu dataset yang terintegrasi.

Contoh:
- Data mahasiswa dari **database akademik**
- Data kehadiran dari **sistem presensi**
- Data kegiatan dari **organisasi kampus**

Semua data tersebut digabungkan untuk analisis yang lebih lengkap.

---

### 3.3 Data Transformation
Data transformation adalah proses mengubah format atau skala data agar sesuai untuk analisis.

Contoh teknik transformasi:
- **Normalisasi**
- **Standarisasi**
- **Encoding data kategorikal**
- **Agregasi data**

Contoh normalisasi:

| Umur | Setelah Normalisasi |
|-----|---------------------|
| 18 | 0.2 |
| 25 | 0.9 |

Tujuannya agar nilai memiliki skala yang sama.

---

### 3.4 Data Reduction
Data reduction bertujuan untuk mengurangi jumlah data tanpa menghilangkan informasi penting.

Beberapa teknik yang digunakan:
- Feature selection
- Sampling
- Dimensionality reduction
- Aggregation

Contoh:
Dataset dengan 100 atribut dapat dipilih menjadi hanya 10 atribut yang paling relevan.

---

### 3.5 Data Discretization
Data discretization adalah proses mengubah data numerik menjadi kategori.

Contoh:

| Nilai | Kategori |
|------|----------|
| 85 | Tinggi |
| 70 | Sedang |
| 50 | Rendah |

Hal ini sering digunakan pada algoritma klasifikasi tertentu.

---

## 4. Contoh Alur Preprocessing

1. Mengumpulkan data dari berbagai sumber  
2. Membersihkan data dari missing value  
3. Mengubah format data  
4. Melakukan normalisasi atau standarisasi  
5. Mengurangi atribut yang tidak diperlukan  

Setelah proses ini selesai, data siap digunakan untuk proses **data mining** seperti:
- Klasifikasi
- Clustering
- Prediksi
- Association rule

---

## 5. Kesimpulan
Preprocessing merupakan tahap penting dalam data mining karena kualitas data sangat mempengaruhi hasil analisis. Dengan melakukan proses seperti **data cleaning, data integration, data transformation, data reduction, dan data discretization**, data mentah dapat diubah menjadi data yang lebih siap untuk dianalisis sehingga menghasilkan model yang lebih akurat dan efektif.