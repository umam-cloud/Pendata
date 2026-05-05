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

# Analisis Data Menggunakan Naive Bayes
## Dataset
Dataset yang digunakan untuk klasifikasi menggunakan metode Naive Bayes adalah `Heart Failure Prediction Dataset`. Dataset ini berisi data klinis dari pasien yang dikumpulkan dari berbagai rumah sakit di Eropa dan Amerika. Setiap data pasien diidentifikasi apakah mengidap penyakit jantung atau tidak.

link dataset yang diambil : [Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)

Dataset ini memiliki **918 baris data**, **11 fitur** (campuran numerik dan kategorikal), dan **1 label** bernama `HeartDisease` yang memiliki 2 nilai, yaitu `0` atau _Normal_ yang berarti pasien tidak memiliki penyakit jantung dan `1` atau _Heart Disease_ yang berarti pasien terdiagnosis penyakit jantung.

Berikut seluruh fitur beserta keterangannya:

| No | Nama Fitur        | Tipe Data  | Deskripsi                                      | Nilai / Rentang                                      |
|----|-------------------|------------|------------------------------------------------|------------------------------------------------------|
| 1  | Age               | Numerik    | Umur pasien (tahun)                            | Angka bulat                                          |
| 2  | Sex               | Kategorikal| Jenis kelamin pasien                           | M: Male (Pria), F: Female (Wanita)                  |
| 3  | ChestPainType     | Kategorikal| Tipe nyeri dada                                | TA, ATA, NAP, ASY                                   |
| 4  | RestingBP         | Numerik    | Tekanan darah saat istirahat (mm Hg)           | Angka bulat                                          |
| 5  | Cholesterol       | Numerik    | Kadar kolesterol serum (mm/dl)                 | Angka bulat                                          |
| 6  | FastingBS         | Numerik    | Gula darah puasa (> 120 mg/dl)                 | 1: Ya, 0: Tidak                                     |
| 7  | RestingECG        | Kategorikal| Hasil EKG saat istirahat                       | Normal, ST, LVH                                     |
| 8  | MaxHR             | Numerik    | Detak jantung maksimum yang dicapai            | Angka antara 60 – 202                               |
| 9  | ExerciseAngina    | Kategorikal| Angina akibat olahraga                         | Y: Ya, N: Tidak                                     |
| 10 | Oldpeak           | Float      | Depresi segmen ST saat olahraga                | Angka desimal                                        |
| 11 | ST_Slope          | Kategorikal| Kemiringan segmen ST puncak olahraga           | Up: naik, Flat: datar, Down: turun                  |
| 12 | HeartDisease      | **Label**  | Hasil diagnosis penyakit jantung               | 0: Normal, 1: Heart Disease                         |

Keterangan tipe nyeri dada (ChestPainType):
- **TA** = Typical Angina (Angina Tipikal)
- **ATA** = Atypical Angina (Angina Atipikal)
- **NAP** = Non-Anginal Pain (Nyeri Non-Anginal)
- **ASY** = Asymptomatic (Tidak Ada Gejala)

## Transformasi Data
Karena `Heart Failure Prediction Dataset` memiliki beberapa kolom bertipe **kategorikal**, maka pada tahap preprocessing dilakukan proses **encoding** menggunakan node **Category to Number** di KNIME. Encoding merupakan proses mengubah data dari format kategorikal menjadi format numerik agar dapat dipahami oleh algoritma machine learning.

Kolom yang dilakukan proses encoding adalah:
- `Sex` → diubah dari M/F menjadi angka
- `ChestPainType` → diubah dari TA/ATA/NAP/ASY menjadi angka
- `RestingECG` → diubah dari Normal/ST/LVH menjadi angka
- `ExerciseAngina` → diubah dari Y/N menjadi angka
- `ST_Slope` → diubah dari Up/Flat/Down menjadi angka

Berikut merupakan dataset sebelum dilakukan proses encoding:

![Dataset sebelum encoding](img/naive-bayes/pre-encoding.png)

Dataset setelah dilakukan encoding:

![Dataset setelah encoding](img/naive-bayes/encoding.png)

## Partisi
Sebelum dilakukan perhitungan Naive Bayes, diperlukan partisi untuk membagi data menjadi **data training** dan **data testing** menggunakan node **Table Partitioner** di KNIME. Data training digunakan sebagai 80% dari dataset untuk melatih model, dan sisanya 20% digunakan sebagai data testing untuk menguji performa model.

![Partisi Data](img/naive-bayes/partisi.png)

## Implementasi KNIME Menggunakan Library scikit-learn
Implementasi dilakukan menggunakan tools KNIME dengan memanfaatkan library **scikit-learn** untuk perhitungan metode Naive Bayes. `df_train` merupakan data training (80%) yang berada di port bagian atas dan `df_test` merupakan data testing (20%) yang berada di port bagian bawah dari node **Table Partitioner**. Script yang digunakan adalah sebagai berikut:

### Script Python

```{code-cell}
:tags: [skip-execution]
import knime.scripting.io as knio
from sklearn.naive_bayes import GaussianNB
# GaussianNB digunakan karena dataset memiliki fitur numerik kontinu
# seperti Age, RestingBP, Cholesterol, MaxHR, dan Oldpeak

# ============================================================
# AMBIL DATA DARI KNIME (hasil Table Partitioner)
# ============================================================
# Data Training (port atas)
df_train = knio.input_tables[0].to_pandas()

# Data Testing (port bawah)
df_test = knio.input_tables[1].to_pandas()

# ============================================================
# DEFINISI FITUR DAN TARGET
# Kolom bertanda "(to number)" adalah hasil node Category to Number
# ============================================================
fitur = [
    'Age',
    'Sex (to number)',
    'ChestPainType (to number)',
    'RestingBP',
    'Cholesterol',
    'FastingBS',
    'RestingECG (to number)',
    'MaxHR',
    'ExerciseAngina (to number)',
    'Oldpeak',
    'ST_Slope (to number)'
]

# Kolom target: 0 = Normal, 1 = Heart Disease
target = 'HeartDisease'

# ============================================================
# PISAHKAN FITUR (X) DAN TARGET (y)
# ============================================================
X_train = df_train[fitur].values   # fitur training
y_train = df_train[target].values  # target training

X_test  = df_test[fitur].values    # fitur testing

# ============================================================
# TRAINING MODEL GAUSSIAN NAIVE BAYES
# ============================================================
model = GaussianNB()
model.fit(X_train, y_train)

# ============================================================
# PREDIKSI DATA TESTING
# ============================================================
predictions = model.predict(X_test)

# Tambahkan kolom hasil prediksi ke tabel testing
# Kolom ini akan dibaca oleh node Scorer di KNIME
df_test['Prediction'] = predictions

# ============================================================
# KIRIM HASIL KE KNIME (output ke node Scorer)
# ============================================================
knio.output_tables[0] = knio.Table.from_pandas(df_test)
```

### Implementasi Workflow KNIME
Berikut tampilan workflow KNIME yang digunakan dalam implementasi Naive Bayes pada dataset Heart Disease:

![Implementasi KNIME](img/naive-bayes/knime.png)

### Hasil Prediksi
Setelah script tersebut dijalankan, maka akan menghasilkan tabel prediksi sebagai berikut:

![Hasil Prediksi](img/naive-bayes/hasil.png)

### Confusion Matrix
Confusion matrix digunakan untuk melihat perbandingan antara nilai aktual dan nilai prediksi dari model Naive Bayes. Baris menunjukkan kelas aktual dan kolom menunjukkan kelas prediksi.

![Confusion Matrix](img/naive-bayes/confusion.png)

### Nilai Akurasi
Nilai akurasi diperoleh dari node **Scorer** di KNIME yang membandingkan kolom `HeartDisease` (nilai asli) dengan kolom `Prediction` (hasil prediksi model).

![Nilai Akurasi](img/naive-bayes/akurasi.png)