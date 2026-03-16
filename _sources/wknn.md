# Weighted K-Nearest Neighbor(WKNN)

## Pengertian WKNN

**Weighted K-Nearest Neighbor (WKNN)** adalah metode klasifikasi yang merupakan pengembangan dari algoritma **K-Nearest Neighbor (KNN)** dalam bidang data mining dan machine learning. Metode ini digunakan untuk menentukan kelas suatu data berdasarkan kedekatannya dengan sejumlah data lain yang berada paling dekat (tetangga terdekat).

Perbedaan utama antara KNN dan WKNN terletak pada cara menentukan pengaruh setiap tetangga terhadap hasil klasifikasi. Pada KNN, setiap tetangga memiliki pengaruh yang sama dalam proses pengambilan keputusan. Sedangkan pada WKNN, setiap tetangga diberikan **bobot berdasarkan jaraknya terhadap data uji**.

Data yang memiliki jarak lebih dekat dengan data uji akan mendapatkan bobot yang lebih besar, sehingga pengaruhnya dalam menentukan hasil klasifikasi juga lebih besar. Sebaliknya, data yang memiliki jarak lebih jauh akan memiliki bobot yang lebih kecil.

Dengan pendekatan ini, WKNN mampu menghasilkan keputusan yang lebih akurat karena mempertimbangkan tingkat kedekatan antar data secara lebih detail.

---

## Konsep Dasar WKNN

Algoritma WKNN bekerja berdasarkan asumsi bahwa data yang memiliki karakteristik serupa cenderung berada pada jarak yang berdekatan dalam ruang data. Oleh karena itu, untuk menentukan kelas suatu data baru, metode ini akan mencari sejumlah data yang memiliki jarak paling dekat terhadap data tersebut.

Setelah tetangga terdekat ditemukan, setiap tetangga akan diberikan bobot berdasarkan jaraknya. Semakin kecil jarak antara data uji dan data latih, maka semakin besar bobot yang diberikan. Selanjutnya, proses klasifikasi dilakukan dengan menghitung total bobot untuk setiap kelas dan memilih kelas dengan bobot terbesar sebagai hasil prediksi.

---

## Rumus Perhitungan pada WKNN

### 1. Rumus Euclidean Distance

Rumus ini digunakan untuk menghitung jarak antara data uji dan data latih.

$
d(x,y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}
$

Keterangan:

- \( d(x,y) \) = jarak antara dua data  
- \( x_i \) = nilai atribut pada data uji  
- \( y_i \) = nilai atribut pada data latih  
- \( n \) = jumlah atribut yang digunakan  

---

### 2. Rumus Bobot pada WKNN

Setelah jarak dihitung, setiap tetangga akan diberikan bobot berdasarkan jaraknya.

$
w_i = \frac{1}{d_i}
$

Keterangan:

- \( w_i \) = bobot tetangga ke-i  
- \( d_i \) = jarak tetangga ke-i terhadap data uji  

Semakin kecil nilai jarak, maka bobot yang dihasilkan akan semakin besar.

---

### 3. Rumus Voting Berbobot

Untuk menentukan kelas akhir, dilakukan penjumlahan bobot berdasarkan kelas masing-masing tetangga.

$
V_j = \sum (w_i \times y_i)
$

Keterangan:

- \( V_j \) = total bobot untuk kelas ke-j  
- \( w_i \) = bobot tetangga  
- \( y_i \) = label kelas dari tetangga  

Kelas dengan **nilai total bobot terbesar** akan dipilih sebagai hasil klasifikasi.

---

## Tahapan Proses WKNN

Secara umum, proses kerja algoritma WKNN terdiri dari beberapa tahap:

1. Menyiapkan dataset yang akan digunakan.
2. Melakukan preprocessing data seperti normalisasi agar skala atribut menjadi seragam.
3. Menghitung jarak antara data uji dan seluruh data latih menggunakan metode pengukuran jarak.
4. Mengurutkan jarak dari yang paling kecil.
5. Menentukan jumlah tetangga terdekat (nilai **K**).
6. Menghitung bobot setiap tetangga berdasarkan jaraknya.
7. Melakukan proses voting berbobot.
8. Menentukan kelas dengan total bobot terbesar sebagai hasil prediksi.

---

## Kelebihan WKNN

Metode WKNN memiliki beberapa kelebihan dibandingkan dengan metode KNN biasa. Salah satu kelebihannya adalah kemampuannya dalam memberikan pengaruh yang lebih besar kepada data yang benar-benar dekat dengan data uji. Hal ini dapat meningkatkan akurasi hasil klasifikasi karena data yang lebih relevan memiliki kontribusi yang lebih besar dalam proses pengambilan keputusan.

Selain itu, WKNN juga mampu mengurangi pengaruh dari data yang memiliki jarak jauh sehingga hasil prediksi menjadi lebih stabil.

---

## Kekurangan WKNN

Meskipun memiliki beberapa kelebihan, metode WKNN juga memiliki beberapa keterbatasan. Salah satunya adalah kebutuhan komputasi yang lebih tinggi karena proses perhitungan bobot harus dilakukan untuk setiap tetangga yang dipilih. Selain itu, performa algoritma ini juga sangat dipengaruhi oleh pemilihan nilai **K** yang digunakan dalam proses klasifikasi.

Jika nilai K terlalu kecil, hasil klasifikasi dapat menjadi sensitif terhadap noise pada data. Sebaliknya, jika nilai K terlalu besar, maka pengaruh dari data yang kurang relevan dapat meningkat dan menurunkan akurasi prediksi.

---

## Kesimpulan

Weighted K-Nearest Neighbor (WKNN) merupakan metode klasifikasi berbasis jarak yang memberikan bobot pada setiap tetangga berdasarkan tingkat kedekatannya dengan data uji. Pendekatan ini memungkinkan proses klasifikasi menjadi lebih akurat dibandingkan metode KNN biasa karena mempertimbangkan kontribusi yang berbeda dari setiap tetangga dalam menentukan hasil akhir.