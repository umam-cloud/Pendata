# Perhitungan WKNN

## 1. Dataset

Data yang digunakan terdiri dari atribut:

- **IPK**
- **PO**
- **JML (kelas)**

Data ke-7 merupakan **data uji** yang ingin diprediksi nilai **JML**.

| No | IPK | PO | JML |
|---|---|---|---|
|1|2|2000000|2|
|2|3|3000000|3|
|3|4|2000000|2|
|4|2|2000000|3|
|5|3|3000000|2|
|6|4|4000000|3|
|7|2|3000000|?|

---

# 2. Normalisasi Data (Min-Max)

Normalisasi dilakukan menggunakan metode **Min-Max Normalization** dengan rumus:

$
X' = \frac{X - X_{min}}{X_{max} - X_{min}}
$

Hasil normalisasi:

| No | IPK | PO | JML |
|---|---|---|---|
|1|0|0|0|
|2|0.5|0.5|1|
|3|1|0|0|
|4|0|0|1|
|5|0.5|0.5|0|
|6|1|1|1|
|7|0|0.5|?|

Data ke-7 adalah **data uji**:

```

IPK = 0
PO  = 0.5

```

---

# 3. Perhitungan Jarak (Euclidean Distance)

Rumus Euclidean Distance:

$
d(x,y) = \sqrt{(x_1-y_1)^2 + (x_2-y_2)^2}
$

Perhitungan jarak antara **data uji** dengan setiap data latih:

### Data 1
$
d = \sqrt{(0-0)^2 + (0.5-0)^2}
$

$
d = \sqrt{0 + 0.25}
$

$
d = 0.5
$

---

### Data 2
$
d = \sqrt{(0-0.5)^2 + (0.5-0.5)^2}
$

$
d = \sqrt{0.25 + 0}
$

$
d = 0.5
$

---

### Data 3
$
d = \sqrt{(0-1)^2 + (0.5-0)^2}
$

$
d = \sqrt{1 + 0.25}
$

$
d = 1.118
$

---

### Data 4
$
d = \sqrt{(0-0)^2 + (0.5-0)^2}
$

$
d = 0.5
$

---

### Data 5
$
d = \sqrt{(0-0.5)^2 + (0.5-0.5)^2}
$

$
d = 0.5
$

---

### Data 6
$
d = \sqrt{(0-1)^2 + (0.5-1)^2}
$

$
d = \sqrt{1 + 0.25}
$

$
d = 1.118
$

---

# 4. Tabel Jarak

| Data | Distance | JML |
|---|---|---|
|1|0.5|0|
|2|0.5|1|
|3|1.118|0|
|4|0.5|1|
|5|0.5|0|
|6|1.118|1|

---

# 5. Menentukan Nilai K

Misalkan digunakan **K = 3** tetangga terdekat.

Data dengan jarak terkecil:

| Data | Distance | JML |
|---|---|---|
|1|0.5|0|
|2|0.5|1|
|4|0.5|1|

---

# 6. Perhitungan Bobot WKNN

Rumus bobot:

$
w_i = \frac{1}{d_i}
$

Karena semua jarak = **0.5**

$
w = \frac{1}{0.5} = 2
$

| Data | JML | Bobot |
|---|---|---|
|1|0|2|
|2|1|2|
|4|1|2|

---

# 7. Voting Berbobot

| Kelas | Perhitungan | Total Bobot |
|---|---|---|
|0|2 × 1|2|
|1|2 + 2|4|

---

# 8. Hasil Prediksi

Karena **kelas 1 memiliki bobot terbesar**, maka hasil prediksi untuk **data ke-7** adalah:

$
JML = 1
$

---

# 9. Kesimpulan

Berdasarkan perhitungan menggunakan metode **Weighted K-Nearest Neighbor (WKNN)** dengan **K = 3**, diperoleh bahwa data ke-7 yang memiliki nilai:

- **IPK = 2**
- **PO = 3000000**

diprediksi memiliki nilai:

**JML = 1**

Metode WKNN memberikan bobot yang lebih besar pada data yang memiliki jarak lebih dekat terhadap data uji sehingga hasil klasifikasi menjadi lebih akurat.
