# K-Nearest Neighbor (KNN)

## 1. K-Nearest Neighbor (KNN)

**K-Nearest Neighbor (KNN)** merupakan salah satu algoritma dalam *machine learning* yang digunakan untuk melakukan **klasifikasi** maupun **regresi**. Algoritma ini bekerja berdasarkan prinsip bahwa suatu data baru dapat ditentukan nilai atau kelasnya dengan melihat **data lain yang memiliki kemiripan paling tinggi**.

Kemiripan antar data ditentukan berdasarkan **jarak antar data** pada ruang fitur (*feature space*). Data yang memiliki jarak paling kecil dianggap sebagai **tetangga terdekat**.

Huruf **K** pada KNN menunjukkan **jumlah tetangga terdekat** yang digunakan dalam proses pengambilan keputusan.

---

## 2. Cara Kerja Algoritma KNN

Secara umum, langkah-langkah kerja algoritma KNN adalah sebagai berikut:

1. Menentukan nilai **K** (jumlah tetangga terdekat).
2. Menghitung jarak antara data yang akan diprediksi dengan seluruh data dalam dataset.
3. Mengurutkan hasil perhitungan jarak dari yang **terkecil hingga terbesar**.
4. Memilih **K data dengan jarak paling dekat**.
5. Menentukan hasil prediksi:
   - Pada **klasifikasi**, menggunakan voting dari kelas yang paling banyak muncul.
   - Pada **regresi**, menggunakan rata-rata nilai dari K tetangga.

---

## 3. Euclidean Distance

Untuk mengukur tingkat kedekatan antar data dalam algoritma KNN, salah satu metode yang paling sering digunakan adalah **Euclidean Distance**.

Euclidean Distance merupakan metode pengukuran jarak antara dua titik dalam ruang berdimensi banyak (*multidimensional space*). Metode ini menghitung jarak garis lurus antara dua titik berdasarkan nilai atributnya.

Rumus Euclidean Distance:

$
d(p,q) = \sqrt{\sum_{i=1}^{n} (p_i - q_i)^2}
$

Keterangan:
- \(d(p,q)\) = jarak antara data \(p\) dan \(q\)
- \(p_i\) = nilai atribut ke-i pada data \(p\)
- \(q_i\) = nilai atribut ke-i pada data \(q\)
- \(n\) = jumlah atribut

Semakin kecil nilai jarak yang dihasilkan, maka semakin tinggi tingkat kemiripan antara kedua data tersebut.

---

## 4. Missing Value pada Data Numerik

Dalam proses analisis data, sering ditemukan **missing value** atau nilai yang hilang pada suatu atribut. Missing value dapat terjadi karena berbagai faktor, seperti kesalahan pencatatan data, data yang tidak lengkap, atau kesalahan pada proses pengumpulan data.

Jika tidak ditangani dengan baik, missing value dapat mempengaruhi hasil analisis dan menurunkan kualitas model yang dihasilkan.

Salah satu metode yang dapat digunakan untuk mengatasi missing value pada data numerik adalah **KNN Imputation**.

---

## 5. KNN Imputation

**KNN Imputation** adalah teknik pengisian missing value dengan memanfaatkan konsep tetangga terdekat dari algoritma KNN. Prinsip dari metode ini adalah bahwa nilai yang hilang pada suatu data dapat diperkirakan berdasarkan nilai dari data lain yang memiliki karakteristik paling mirip.

Kemiripan antar data dihitung menggunakan metode pengukuran jarak, salah satunya adalah **Euclidean Distance**.

---

## 6. Langkah-Langkah Mengisi Missing Value Menggunakan KNN

Proses pengisian missing value menggunakan KNN dilakukan melalui beberapa tahapan berikut:

1. Mengidentifikasi data yang memiliki **missing value** pada atribut tertentu.
2. Menghitung **jarak Euclidean** antara data yang memiliki missing value dengan data lain yang tidak memiliki nilai kosong.
3. Mengurutkan data berdasarkan **jarak terkecil**.
4. Memilih sejumlah **K data dengan jarak terdekat** sebagai tetangga.
5. Menghitung nilai estimasi dengan menggunakan **rata-rata nilai atribut** dari tetangga terdekat tersebut.
6. Menggunakan hasil perhitungan tersebut untuk **menggantikan missing value** pada data.

---

## 7. Kelebihan dan Kekurangan KNN dalam Imputasi Data

### Kelebihan
- Metode yang sederhana dan mudah dipahami.
- Dapat menghasilkan estimasi nilai yang cukup akurat karena menggunakan data yang paling mirip.
- Dapat diterapkan pada berbagai jenis dataset numerik.

### Kekurangan
- Proses perhitungan jarak dapat menjadi lambat jika dataset berukuran besar.
- Sensitif terhadap perbedaan skala data sehingga sering memerlukan proses normalisasi.
- Pemilihan nilai **K** dapat mempengaruhi hasil imputasi yang diperoleh.

---

## 8. Kesimpulan

K-Nearest Neighbor merupakan algoritma berbasis kedekatan data yang banyak digunakan dalam berbagai bidang analisis data. Dengan menggunakan metode pengukuran jarak seperti **Euclidean Distance**, algoritma ini tidak hanya dapat digunakan untuk klasifikasi dan regresi, tetapi juga untuk menangani **missing value pada data numerik** melalui teknik **KNN Imputation**. Metode ini bekerja dengan mencari data yang paling mirip dan menggunakan nilai dari tetangga terdekat tersebut untuk memperkirakan nilai yang hilang.