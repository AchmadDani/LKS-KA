# LEMBAR KERJA SISWA (LKS)

# Naïve Bayes untuk Kategorikal

## Mata Kuliah: Kecerdasan Artificial

---

# Tujuan Pembelajaran

Setelah menyelesaikan LKS ini, mahasiswa mampu:

1. Memahami konsep probabilitas prior dan probabilitas bersyarat.
2. Menghitung Conditional Probability Table (CPT) dari data training.
3. Melakukan prediksi manual menggunakan algoritma Naive Bayes.
4. Memahami masalah zero probability.
5. Menggunakan Laplace smoothing untuk mengatasi zero probability.

---

# BAGIAN 1 — Memahami Prior dan Likelihood

## Studi Kasus: Play Tennis

Sebuah dataset digunakan untuk memprediksi apakah seseorang akan bermain tenis berdasarkan kondisi cuaca.

| No | Outlook | Temperature | Humidity | Wind | Play Tennis |
|----|----------|-------------|----------|------|-------------|
| 1 | Sunny | Hot | High | Weak | No |
| 2 | Sunny | Hot | High | Strong | No |
| 3 | Overcast | Hot | High | Weak | Yes |
| 4 | Rain | Mild | High | Weak | Yes |
| 5 | Rain | Cool | Normal | Weak | Yes |
| 6 | Rain | Cool | Normal | Strong | No |
| 7 | Overcast | Cool | Normal | Strong | Yes |
| 8 | Sunny | Mild | High | Weak | No |
| 9 | Sunny | Cool | Normal | Weak | Yes |
| 10 | Rain | Mild | Normal | Weak | Yes |
| 11 | Sunny | Mild | Normal | Strong | Yes |
| 12 | Overcast | Mild | High | Strong | Yes |
| 13 | Overcast | Hot | Normal | Weak | Yes |
| 14 | Rain | Mild | High | Strong | No |

---

# Aktivitas 1 — Menghitung Prior Probability

## Pertanyaan Pengamatan

### 1. Berapa jumlah data keseluruhan?

**Jawaban:**

..............................................................................

### 2. Berapa jumlah data dengan class Yes?

**Jawaban:**

..............................................................................

### 3. Berapa jumlah data dengan class No?

**Jawaban:**

..............................................................................

---

## Hitung Probabilitas Prior

$$
P(Yes)=
\frac{Jumlah\ Yes}{Total\ Data}
$$

**Jawaban:**

$$
P(Yes)=
$$

$$
P(No)=
\frac{Jumlah\ No}{Total\ Data}
$$

**Jawaban:**

$$
P(No)=
$$

---

# Aktivitas 2 — Menghitung Likelihood

## Feature: Outlook

Lengkapi tabel berikut.

| Outlook | Count pada Yes | P(Outlook \| Yes) | Count pada No | P(Outlook \| No) |
|----------|----------|----------|----------|----------|
| Sunny | | | | |
| Overcast | | | | |
| Rain | | | | |

---

# Refleksi

### 1. Nilai Outlook apa yang paling sering muncul pada class Yes?

**Jawaban:**

..............................................................................

### 2. Nilai Outlook apa yang paling sering muncul pada class No?

**Jawaban:**

..............................................................................

### 3. Menurut Anda, apakah Outlook cukup membantu untuk menentukan keputusan bermain tenis?

**Jawaban:**

..............................................................................

---

# BAGIAN 2 — Formula dan Perhitungan Lengkap

## Formula Naive Bayes

$$
P(C|X)
\propto
P(C)\times P(x_1|C)\times P(x_2|C)\times ... \times P(x_n|C)
$$

### Keterangan

- $P(C)$ = prior probability class
- $P(x_i|C)$ = likelihood feature terhadap class
- $X$ = data baru yang ingin diprediksi

---

# Aktivitas 3 — Lengkapi Conditional Probability Table (CPT)

## Feature: Temperature

| Temperature | P(Temperature \| Yes) | P(Temperature \| No) |
|------------|------------|------------|
| Hot | | |
| Mild | | |
| Cool | | |

---

## Feature: Humidity

| Humidity | P(Humidity \| Yes) | P(Humidity \| No) |
|----------|----------|----------|
| High | | |
| Normal | | |

---

## Feature: Wind

| Wind | P(Wind \| Yes) | P(Wind \| No) |
|------|------|------|
| Weak | | |
| Strong | | |

---

# Aktivitas 4 — Prediksi Manual

Diberikan data baru:

$$
X=(Sunny,Cool,Normal,Strong)
$$

---

## Langkah 1 — Hitung Probabilitas untuk Class Yes

$$
P(Yes|X)
\propto
P(Yes)
\times P(Sunny|Yes)
\times P(Cool|Yes)
\times P(Normal|Yes)
\times P(Strong|Yes)
$$

Isi nilai:

$$
P(Yes|X)\propto
.............................................................
.............................................................
.............................................................
$$

### Hasil

$$
P(Yes|X)=
$$

---

## Langkah 2 — Hitung Probabilitas untuk Class No

$$
P(No|X)
\propto
P(No)
\times P(Sunny|No)
\times P(Cool|No)
\times P(Normal|No)
\times P(Strong|No)
$$

Isi nilai:

$$
P(No|X)\propto
.............................................................
.............................................................
.............................................................
$$

### Hasil

$$
P(No|X)=
$$

---

## Langkah 3 — Tentukan Prediksi

Jika

$$
P(Yes|X)>P(No|X)
$$

maka class prediksi adalah:

**Jawaban:**

..............................................................................

---

# BAGIAN 3 — Laplace Smoothing

## Masalah Zero Probability

Perhatikan contoh berikut:

Misalkan terdapat kondisi data baru:

$$
Temperature=Cold
$$

Namun pada data training, nilai tersebut tidak pernah muncul pada class tertentu.

Akibatnya:

$$
P(Cold|Yes)=0
$$

Karena Naive Bayes mengalikan semua probabilitas, maka hasil akhir juga menjadi 0.

---

## Solusi: Laplace Smoothing

$$
P(x_i|C)
=
\frac
{
count(x_i,C)+1
}
{
count(C)+|x_i\ values|
}
$$

### Keterangan

- $count(x_i,C)$ = jumlah kemunculan feature pada class
- $count(C)$ = jumlah data pada class
- $|x_i\ values|$ = jumlah kemungkinan nilai feature

---

# Aktivitas 5 — Perbandingan Tanpa dan Dengan Smoothing

## Contoh Kasus

Feature Temperature memiliki 3 kemungkinan nilai:

- Hot
- Mild
- Cool

Misalkan:

- $count(C=No)=5$
- $count(Hot,No)=0$

---

### Tanpa Smoothing

$$
P(Hot|No)
=
\frac{0}{5}
=
0
$$

---

### Dengan Laplace Smoothing

$$
P(Hot|No)
=
\frac{0+1}{5+3}
$$

Hitung hasilnya:

**Jawaban:**

..............................................................................

---

# Aktivitas 6 — Prediksi dengan Smoothing

Diberikan data baru:

$$
X=(Overcast,Hot,Normal,Weak)
$$

## Perhitungan Class Yes

..............................................................................

..............................................................................

..............................................................................

---

## Perhitungan Class No

..............................................................................

..............................................................................

..............................................................................

---

# Kesimpulan

Mengapa smoothing penting?

**Jawaban:**

..............................................................................

..............................................................................

---

# BAGIAN 4 — Prediksi Mandiri

## Studi Kasus: Smartphone Recommendation

Tujuan: Memprediksi apakah sebuah smartphone direkomendasikan atau tidak.

---

# Dataset Training

| No | Battery | RAM | Storage | Camera | Price | Recommend |
|----|---------|------|---------|--------|--------|-----------|
| 1 | High | 8GB | 128GB | 16MP | Expensive | Yes |
| 2 | Medium | 4GB | 64GB | 12MP | Medium | Yes |
| 3 | Low | 2GB | 32GB | 8MP | Cheap | No |
| 4 | High | 8GB | 128GB | 16MP | Medium | Yes |
| 5 | Medium | 4GB | 64GB | 8MP | Cheap | No |
| 6 | High | 8GB | 64GB | 12MP | Expensive | Yes |
| 7 | Low | 2GB | 32GB | 8MP | Cheap | No |
| 8 | Medium | 4GB | 128GB | 12MP | Medium | Yes |
| 9 | High | 8GB | 128GB | 16MP | Expensive | Yes |
| 10 | Medium | 2GB | 32GB | 8MP | Cheap | No |
| 11 | High | 4GB | 64GB | 12MP | Medium | Yes |
| 12 | Low | 2GB | 64GB | 8MP | Cheap | No |
| 13 | Medium | 8GB | 128GB | 16MP | Expensive | Yes |
| 14 | High | 4GB | 128GB | 12MP | Medium | Yes |
| 15 | Low | 2GB | 32GB | 8MP | Cheap | No |

---

# Tugas Mandiri

## Tugas 1 — Hitung Prior Probability

Hitung:

$$
P(Yes)=
$$

dan

$$
P(No)=
$$

---

## Tugas 2 — Lengkapi CPT dengan Laplace Smoothing

Lengkapi conditional probability table untuk seluruh feature:

- Battery
- RAM
- Storage
- Camera
- Price

### Feature: Battery

| Battery | P(Battery \| Yes) | P(Battery \| No) |
|----------|----------|----------|
| High | | |
| Medium | | |
| Low | | |

---

### Feature: RAM

| RAM | P(RAM \| Yes) | P(RAM \| No) |
|------|------|------|
| 8GB | | |
| 4GB | | |
| 2GB | | |

---

### Feature: Storage

| Storage | P(Storage \| Yes) | P(Storage \| No) |
|----------|----------|----------|
| 128GB | | |
| 64GB | | |
| 32GB | | |

---

### Feature: Camera

| Camera | P(Camera \| Yes) | P(Camera \| No) |
|----------|----------|----------|
| 16MP | | |
| 12MP | | |
| 8MP | | |

---

### Feature: Price

| Price | P(Price \| Yes) | P(Price \| No) |
|--------|--------|--------|
| Expensive | | |
| Medium | | |
| Cheap | | |

---

## Tugas 3 — Prediksi Data Baru dengan Laplace Smoothing

### Data Uji 1

$$
X_1=(Medium,4GB,64GB,8MP,Medium)
$$

Langkah perhitungan dan Prediksi Akhir:

..............................................................................

---

### Data Uji 2

$$
X_2=(Low,4GB,128GB,8MP,Expensive)
$$

Langkah perhitungan dan Prediksi Akhir:

..............................................................................

---

# Refleksi

### 1. Menurut Anda, feature mana yang paling menentukan keputusan rekomendasi smartphone?

**Jawaban:**

..............................................................................

### 2. Mengapa Naive Bayes masih bisa bekerja dengan baik meskipun asumsi independence antar feature tidak selalu benar?

**Jawaban:**

..............................................................................

### 3. Apa kelebihan utama Naive Bayes dibanding metode lain?

**Jawaban:**

..............................................................................
