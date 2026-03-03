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

# Data Iris

Kumpulan data bunga Iris adalah kumpulan data multivariat yang diperkenalkan oleh ahli statistik dan biologi Inggris, Ronald Fisher, dalam makalahnya tahun 1936 yang berjudul "The use of multiple measurements in taxonomic problems". Kumpulan data ini terkadang disebut sebagai kumpulan data Iris Anderson karena Edgar Anderson mengumpulkan data tersebut untuk mengukur variasi morfologi bunga Iris dari tiga spesies yang berkerabat. Kumpulan data ini terdiri dari 50 sampel dari masing-masing tiga spesies Iris (Iris Setosa, Iris virginica, dan Iris versicolor). Empat fitur diukur dari setiap sampel: panjang dan lebar sepal dan petal, dalam sentimeter.

```{code-cell} python
:tags: [hide-input]

import pandas as pd

df = pd.read_csv("data/IRIS.csv")
df.head(20)
```
```{note}
Berikut ini adalah data iris flower yang di ambil dari Kaggle, data yang ditampilkan hanya beberapa dari semua data
```

## Deskripsi Dataset

Dataset IRIS memiliki lima atribut sebagai berikut:

| No | Atribut        | Tipe Data     | Deskripsi |
|----|---------------|--------------|-----------|
| 1  | sepal length  | Numerik (cm) | Panjang kelopak bunga |
| 2  | sepal width   | Numerik (cm) | Lebar kelopak bunga |
| 3  | petal length  | Numerik (cm) | Panjang mahkota bunga |
| 4  | petal width   | Numerik (cm) | Lebar mahkota bunga |
| 5  | species       | Kategorikal  | Jenis bunga iris |

Dataset terdiri dari tiga kelas:

- Iris-setosa
- Iris-versicolor
- Iris-virginica

Masing-masing kelas berjumlah 50 data sehingga dataset bersifat seimbang (balanced dataset).

## Deteksi Outlier

Deteksi outlier dilakukan menggunakan widget Outliers pada Orange Data Mining. Berdasarkan hasil analisis, teridentifikasi 15 data yang dikategorikan sebagai outlier oleh model.

Namun, perlu diperhatikan bahwa metode yang digunakan bersifat berbasis model (misalnya One-Class SVM atau Isolation Forest), sehingga data yang dianggap outlier merupakan data yang memiliki pola berbeda dari mayoritas distribusi global, bukan karena kesalahan pencatatan.

Dataset IRIS secara umum tidak memiliki outlier ekstrem berdasarkan analisis statistik klasik (misalnya metode IQR). Oleh karena itu, data yang terdeteksi lebih merepresentasikan perbedaan karakteristik antar kelas daripada anomali data.

![alt text](img/outliers.png)
