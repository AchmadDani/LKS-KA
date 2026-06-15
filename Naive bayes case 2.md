# LEMBAR KERJA MAHASISWA (LKM)

**Mata Kuliah:** Machine Learning

**Topik:** Regresi Linear (Univariat & Multivariat) dan Regresi Logistik

**Metode:** Hybrid Learning (Manual Komputasi & Visualisasi Interaktif)

**Nama Mahasiswa:** _______________________________________

**NIM:** _______________________________________

---

# Tujuan Pembelajaran

1. Memahami proses perhitungan manual untuk mencari Best Fit Line menggunakan metode Least Square Error.
2. Memahami cara mentransformasi data menjadi bentuk operasi matriks aljabar linier untuk Regresi Multivariat.
3. Membangun intuisi mengenai fungsi aktivasi Sigmoid dan Cost Function pada Regresi Logistik.

---

# Persiapan Aplikasi & Dataset

1. Buka link ini https://ka-linear-regression.streamlit.app di browser Anda.
2. Pada panel sebelah kiri (Sidebar), masukkan NIM Anda.
3. Aplikasi akan secara otomatis membuat dataset unik yang dikunci menggunakan NIM Anda. Gunakan data tersebut untuk mengisi tabel-tabel di LKM ini!

---

# BAGIAN 1: Regresi Linear Univariat

## Studi Kasus

Memprediksi Nilai Ujian berdasarkan Jam Belajar.

---

## Langkah 0: Salin Data dari Aplikasi (Menu Modul 1)

Salin 5 buah data (Jam Belajar dan Nilai Ujian) milik Anda ke dalam dua kolom pertama tabel di bawah ini.

### Tabel Data Latihan

| | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| Jam Belajar $(x)$ | 2 | 4 | 6 | 8 | 10 |
| Nilai Ujian $(y)$ | 27 | 29 | 35 | 52 | 59 |

---

# Langkah 1: Perhitungan Manual

## 1. Hitung Rata-rata

- $\bar{x}$ = ________

- $\bar{y}$ = ________

---

## 2. Lengkapi tabel di atas, kemudian hitung total Varians X dan total Kovarians X,Y.

- Variance$(X)$

$$
=\sum (x-\bar{x})^2
$$

= ________

- Covariance$(X,Y)$

$$
=\sum (x-\bar{x})(y-\bar{y})
$$

= ________

---

## 3. Hitung Parameter Garis

Gunakan rumus persamaan regresi

$$
f(x)=wx+a
$$

### Bobot $(w)$

$$
w=
\frac
{Covariance(X,Y)}
{Variance(X)}
$$

= ________

### Bias $(a)$

$$
a=\bar y-(w\cdot \bar x)
$$

= ________

---

# Langkah 2: Hitung Sum Squared Error data Latih

| x | y | $\hat y$ | $(y-\hat y)^2$ |
|---|---|---|---|
| 2 | 51 | | |
| 4 | 46 | | |
| 6 | 60 | | |
| 8 | 85 | | |
| 10 | 96 | | |
| SUM | | | |

### Jawaban

$$
SSE=\sum (y-\hat y)^2
$$

SSE = __________

---

# Langkah 3: Validasi Jawaban

1. Buka menu **"1. Univariate Visualizer"** di aplikasi.

2. Masukkan nilai bobot $(w)$ dan bias $(a)$ yang Anda hitung di Langkah 1 ke dalam kolom input. Berikan screenshoot layar nya.

   **Screenshoot:** ________

3. Catat nilai Sum Square Error (SSE) yang muncul di layar:

   ________

   bandingkan dengan jawaban anda di Langkah 2.

4. Eksperimen Analitis:

   Cobalah ubah angka $w$ dan $a$ secara bebas di aplikasi. Amati perubahan garis dan nilai SSE.

5. Kesimpulan:

   Berdasarkan eksperimen Anda, jelaskan mengapa rumus manual di Langkah 1 disebut sebagai metode Least Square Error!

   **Jawaban:**

   ___________________________________________

   ___________________________________________

   ___________________________________________

---

# BAGIAN 2: Regresi Linear Multivariat

## Studi Kasus

Memprediksi Nilai Ujian berdasarkan Jam Belajar $(x_1)$ dan Jumlah Latihan Soal $(x_2)$.

---

# Langkah 0: Salin Data dari Aplikasi (Menu Modul 2)

- Data 1: Jam $(x_1)$ = _____, Latihan $(x_2)$ = _____, Nilai $(y)$ = _____

- Data 2: Jam $(x_1)$ = _____, Latihan $(x_2)$ = _____, Nilai $(y)$ = _____

- Data 3: Jam $(x_1)$ = _____, Latihan $(x_2)$ = _____, Nilai $(y)$ = _____

---

# Langkah 1: Desain Matriks Manual

Aturan regresi multivariat:

Wajib menyisipkan satu kolom berisi angka 1 di sisi paling kiri matriks $X$ sebagai representasi fitur pengali bias $(w_0)$.

Tuliskan bentuk Matriks $X$ dan Vektor $y$ Anda di bawah ini:

$$
X=
\begin{bmatrix}
1 & x_{11} & x_{21}\\
1 & x_{12} & x_{22}\\
1 & x_{13} & x_{23}
\end{bmatrix}
\qquad
y=
\begin{bmatrix}
y_1\\
y_2\\
y_3
\end{bmatrix}
$$

---

# Langkah 2: Hitung Invers & Matriks $w$

Rumus

$$
w=(X^TX)^{-1}X^Ty
$$

### 1. Hitung

$$
X^TX=
$$

---

### 2. Hitung invers dari matriks hasil perhitungan sebelumnya

$$
(X^TX)^{-1}=
$$

---

### 3. Hitung

$$
(X^TX)^{-1}X^T=
$$

---

### 4. Hitung

$$
(X^TX)^{-1}X^Ty=
$$

---

# Langkah 3: Validasi Jawaban

1. Buka menu **"2. Matrix Engine"** di aplikasi.

2. Masukkan Matriks $X$ dan Vektor $y$ yang telah Anda desain di atas.

3. Klik tombol **Hitung Invers & Bobot Matriks**.

   (Aplikasi mengeksekusi rumus

$$
w=(X^TX)^{-1}X^Ty
$$

)

4. Salin Vektor Bobot akhir $(w)$ yang dihasilkan computer, bandingkan dengan jawaban anda:

- $w_0$ (Bias) = ________

- $w_1$ (Jam) = ________

- $w_2$ (Latihan) = ________

---

# Langkah 3: Prediksi Manual

Berdasarkan bobot di atas, tuliskan persamaan linear lengkapnya:

$$
f(x)
=
\_\_\_\_\_\_
+
(\_\_\_\_\_\_ \cdot x_1)
+
(\_\_\_\_\_\_ \cdot x_2)
$$

Diberikan data mahasiswa baru:

Budi belajar selama 5 jam dan mengerjakan latihan soal sebanyak 2.5 set.

Hitung prediksi Nilai Ujian Budi secara manual!

- Tuliskan proses hitung : ________

- Prediksi Nilai Budi = ________

---

# BAGIAN 3: Regresi Logistik

## Studi Kasus

Memprediksi probabilitas kelulusan (Lulus = 1, Gagal = 0) berdasarkan Jam Belajar.

---

# Langkah 1: Simulasi Pencarian Parameter (Gunakan Streamlit)

1. Buka menu **"3. Logistic Explorer"** di aplikasi.

   Pastikan NIM Anda sudah terisi di sidebar.

2. Perhatikan persebaran titik biru/merah pada grafik *scatter plot*.

3. Bertindaklah sebagai algoritma *Gradient Descent*.

   Geser slider **Bobot $(w)$** dan **Bias $(a)$** secara perlahan untuk mencari pemisah terbaik.

4. Tujuan Anda adalah membuat nilai **Cost (Log Loss)** sekecil mungkin (mencapai batas hijau/optimal).

5. Catat parameter terbaik yang berhasil Anda temukan:

- Bobot $(w)$ terbaik = ________

- Bias $(a)$ terbaik = ________

- Nilai Cost terendah yang dicapai = ________

---

# Langkah 2: Prediksi Probabilitas Manual

Diberikan mahasiswa baru:

Siti belajar selama 8 jam

$$
x=8
$$

Menggunakan $w$ dan $a$ terbaik yang Anda temukan dari simulasi Langkah 1, hitunglah:

---

## 1. Hitung nilai kombinasi linier

$$
v=wx+a
$$

- Tulis perhitungan : ________

- $v$ = ________

---

## 2. Masukkan nilai $v$ ke dalam rumus Fungsi Sigmoid

$$
\sigma(v)
=
\frac{1}
{1+e^{-v}}
$$

- Tulis perhitungan : ________

- Probabilitas = ________

---

## 3. Berdasarkan threshold standar (0.5), apakah Siti diprediksi Lulus atau Gagal?

- Keputusan: ______________________________
