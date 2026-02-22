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
Berikut ini adalah data iris flower yang di ambil dari Kaggle, data yang ditampilkan hanya beberapa dari semua data
