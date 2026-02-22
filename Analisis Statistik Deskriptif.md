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

# Analisis Statistik Deskriptif
metode untuk meringkas, mengatur, dan menyajikan data mentah agar menjadi informasi yang mudah dipahami, biasanya melalui nilai rata-rata (mean), median, modus, standar deviasi, maksimum, dan minimum

## Visualisasi Orange
```{figure} /img/Analisis_Statistik_Deskriptif.png
---
width: 100%
fig-margin : 0
---
```

```{figure} /img/Analisis_Statistik_Deskriptif2.png
---
width: 100%
fig-margin : 0
---
Analisis Statistik Deskriptif Fitur sepal_length
```

## Source Code

```{code-cell}
import pandas as pd
from scipy import stats

# Membaca data
df = pd.read_csv("data/IRIS.csv", usecols=[0])
df.columns = ['sepal_length']

# Statistik deskriptif
print("Jumlah data      :", df['sepal_length'].count())
print("Rata-rata        :", df['sepal_length'].mean())
print("Nilai minimum    :", df['sepal_length'].min())
print("Q1               :", df['sepal_length'].quantile(0.25))
print("Median (Q2)      :", df['sepal_length'].quantile(0.5))
print("Q3               :", df['sepal_length'].quantile(0.75))
print("Nilai maksimum   :", df['sepal_length'].max())

# Modus
mode = stats.mode(df['sepal_length'], keepdims=True)
print("Modus            :", mode.mode[0])
print("Frekuensi modus  :", mode.count[0])

# Variasi data
print("Standar deviasi  :", df['sepal_length'].std())
print("Variansi         :", df['sepal_length'].var())
```
## Keterangan Hasil

- **Jumlah data** menunjukkan banyaknya sampel yang dianalisis.
- **Rata-rata (mean)** merupakan nilai pemusatan data.
- **Nilai minimum dan maksimum** menunjukkan rentang data.
- **Q1, Median (Q2), dan Q3** membagi data menjadi empat bagian sama besar.
- **Modus** adalah nilai yang paling sering muncul dalam data.
- **Standar deviasi** menunjukkan tingkat penyebaran data dari rata-rata.
- **Variansi** merupakan kuadrat dari standar deviasi.

## Kesimpulan

Berdasarkan analisis statistik deskriptif, atribut **sepal_length**
pada dataset Iris memiliki sebaran data yang relatif stabil.
Nilai standar deviasi yang tidak terlalu besar menunjukkan bahwa
data tidak menyebar jauh dari nilai rata-ratanya.