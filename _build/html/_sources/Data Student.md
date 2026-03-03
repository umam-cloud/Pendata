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

# Data Student

Kumpulan data mahasiswa ini merupakan dataset multivariat yang dirancang untuk merepresentasikan kondisi akademik dan non-akademik mahasiswa dalam satu periode tertentu. Dataset ini digunakan untuk menganalisis berbagai faktor yang berpotensi memengaruhi performa akademik, seperti motivasi belajar, keterlibatan organisasi, status kerja, hingga kepemilikan beasiswa.

Dataset ini terdiri dari 150 data mahasiswa, di mana setiap baris merepresentasikan satu individu mahasiswa. Data yang dikumpulkan mencakup kombinasi variabel numerik dan kategorikal sehingga sangat cocok digunakan untuk analisis statistik maupun pengembangan model data mining.

Beberapa atribut yang terdapat dalam dataset ini antara lain:

- ID mahasiswa sebagai identitas unik
- Jenis kelamin
- Usia
- Program studi
- Semester aktif
- IPK (Indeks Prestasi Kumulatif)
- Jumlah organisasi yang diikuti
- Tingkat kepuasan mahasiswa
- Motivasi belajar
- Status beasiswa
- Status kerja

Variabel numerik dalam dataset ini meliputi usia, semester, IPK, dan jumlah organisasi. Sementara itu, variabel kategorikal mencakup jenis kelamin, program studi, tingkat kepuasan, motivasi belajar, status beasiswa, dan status kerja.

- Dataset ini memungkinkan berbagai jenis analisis, seperti:
- Analisis hubungan antara motivasi belajar dan IPK
- Pengaruh keaktifan organisasi terhadap prestasi akademik
- Dampak status kerja terhadap performa mahasiswa
- Prediksi kepuasan mahasiswa berdasarkan faktor akademik dan sosial

Karena memuat kombinasi data numerik dan kategorikal serta tidak memiliki nilai kosong (missing value), dataset ini sangat sesuai digunakan untuk latihan analisis data, klasifikasi, clustering, maupun eksplorasi pola dalam konteks pendidikan tinggi.

```{code-cell} python
:tags: [hide-input]

import pandas as pd

df = pd.read_csv("data/Dataset_Mahasiswa.csv")
df.head(20)
```

# Deskripsi Atribut

Berikut merupakan atribut/fitur yang terdapat dalam Dataset Mahasiswa:

| No | Atribut           | Deskripsi                                                    |
| -- | ----------------- | ------------------------------------------------------------ |
| 1  | ID                | Nomor identitas unik mahasiswa                               |
| 2  | Jenis_Kelamin     | Jenis kelamin mahasiswa (Laki-laki / Perempuan)              |
| 3  | Usia              | Usia mahasiswa (dalam tahun)                                 |
| 4  | Program_Studi     | Program studi/jurusan mahasiswa                              |
| 5  | Semester          | Semester aktif mahasiswa (1–8)                               |
| 6  | IPK               | Indeks Prestasi Kumulatif mahasiswa                          |
| 7  | Jumlah_Organisasi | Jumlah organisasi yang diikuti mahasiswa                     |
| 8  | Tingkat_Kepuasan  | Tingkat kepuasan mahasiswa (Rendah, Sedang, Tinggi)          |
| 9  | Motivasi_Belajar  | Tingkat motivasi belajar (Sangat Rendah – Sangat Tinggi)     |
| 10 | Status_Beasiswa   | Status penerimaan beasiswa (Ya / Tidak)                      |
| 11 | Status_Kerja      | Status kerja mahasiswa (Tidak Bekerja, Part Time, Full Time) |

---

# Karakteristik Dataset

Dataset ini memiliki tipe data campuran (mixed data), yaitu:

* **Numerik (Kontinu & Diskrit)**

  * Usia
  * Semester
  * IPK
  * Jumlah_Organisasi

* **Kategorikal Nominal**

  * ID
  * Jenis_Kelamin
  * Program_Studi
  * Status_Beasiswa
  * Status_Kerja

* **Kategorikal Ordinal**

  * Tingkat_Kepuasan
  * Motivasi_Belajar

---

# Informasi Umum Dataset

* **Jumlah Data (Baris)**: 150 mahasiswa
* **Jumlah Atribut (Kolom)**: 11 atribut
* **Tipe Dataset**: Multivariat
* **Jenis Data**: Campuran (Numerik dan Kategorikal)

---

# Statistik Deskriptif Singkat

## Variabel Numerik

| Atribut           | Min | Max | Mean |
| ----------------- | ------- | -------- | --------- |
| Usia              | 18      | 25       | ± 21,43   |
| Semester          | 1       | 8        | ± 4       |
| IPK               | 2.00    | 3.99     | ± 2,97    |
| Jumlah_Organisasi | 0       | 5        | ± 2–3     |

---

# Missing Value

Berdasarkan pemeriksaan data:

* Tidak terdapat nilai kosong (missing value) pada seluruh atribut.
* Dataset dalam kondisi lengkap dan siap untuk analisis lebih lanjut.

---

# Outlier

* Pada variabel **IPK**, nilai berada dalam rentang normal (2.00 – 3.99), sehingga tidak ditemukan outlier ekstrem.
* Pada variabel **Usia** dan **Semester**, seluruh data masih dalam rentang wajar mahasiswa aktif.
* Jumlah organisasi (0–5) juga masih dalam batas yang logis.

Secara umum, dataset ini tidak menunjukkan adanya outlier yang signifikan.

---