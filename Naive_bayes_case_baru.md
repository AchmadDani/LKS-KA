# LEMBAR KERJA MAHASISWA (LKM) - KASUS BARU NAÏVE BAYES

**Mata Kuliah:** Machine Learning
**Topik:** Naïve Bayes Classifier (Spam Email & Klasifikasi Kontinu)
**Metode:** Hybrid Learning (Manual Komputasi & Visualisasi Interaktif)

**Nama Mahasiswa:** Achmad Dani Saputra
**NIM:** 103012580004

---

# Tujuan Pembelajaran
1. Memahami klasifikasi Naïve Bayes kategorikal dengan Laplace Smoothing untuk menangani *Zero Frequency Problem*.
2. Memahami model Gaussian Naïve Bayes untuk data kontinu.
3. Melakukan perhitungan posterior score MAP untuk mengambil keputusan klasifikasi.

---

# BAGIAN 1: Naïve Bayes Kategorikal (Klasifikasi Spam Email)

## Dataset Latihan
Diberikan 10 data email historis dengan label **Spam** dan **Ham**:

| No | Ada Link Promo | Domain Anonim | Urgent Subject | Kelas Target |
|----|----------------|---------------|----------------|--------------|
| 1  | Yes            | Yes           | Yes            | Spam         |
| 2  | Yes            | Yes           | No             | Spam         |
| 3  | Yes            | No            | Yes            | Spam         |
| 4  | Yes            | Yes           | Yes            | Spam         |
| 5  | Yes            | No            | No             | Spam         |
| 6  | No             | Yes           | No             | Spam         |
| 7  | Yes            | No            | Yes            | Ham          |
| 8  | No             | No            | No             | Ham          |
| 9  | No             | No            | Yes            | Ham          |
| 10 | No             | No            | No             | Ham          |

---

## Langkah 1: Perhitungan Prior Probability
Hitung probabilitas awal kemunculan masing-masing kelas:
* $P(\text{Spam}) = $ ________
* $P(\text{Ham}) = $ ________

---

## Langkah 2: Likelihood & Zero Frequency Problem
Diberikan data email baru ($X_{new}$):
* **Ada Link Promo** = Yes
* **Domain Anonim** = Yes
* **Urgent Subject** = No

Hitung likelihood berikut **tanpa** Laplace Smoothing:
* $P(\text{Domain Anonim} = \text{Yes} \mid \text{Ham}) = $ ________ (Terjadi Zero Frequency!)

---

## Langkah 3: Penerapan Laplace Smoothing (k=2)
Gunakan Laplace Smoothing untuk semua fitur (di mana jumlah nilai unik fitur $k = 2$, yaitu Yes dan No):

$$
P(x_i \mid c) = \frac{n_{ic} + 1}{n_c + 2}
$$

Hitung nilai likelihood baru:
* $P(\text{Link}=\text{Yes} \mid \text{Spam}) = $ ________
* $P(\text{Domain}=\text{Yes} \mid \text{Spam}) = $ ________
* $P(\text{Urgent}=\text{No} \mid \text{Spam}) = $ ________
* $P(\text{Link}=\text{Yes} \mid \text{Ham}) = $ ________
* $P(\text{Domain}=\text{Yes} \mid \text{Ham}) = $ ________
* $P(\text{Urgent}=\text{No} \mid \text{Ham}) = $ ________

---

## Langkah 4: Hitung MAP Posterior Score & Keputusan Akhir
Kalikan Prior dengan semua Likelihood Laplace yang telah dihitung:
* $\text{Score}(\text{Spam}) = P(\text{Spam}) \times P(\text{Link}=\text{Yes} \mid \text{Spam}) \times P(\text{Domain}=\text{Yes} \mid \text{Spam}) \times P(\text{Urgent}=\text{No} \mid \text{Spam}) = $ ________
* $\text{Score}(\text{Ham}) = P(\text{Ham}) \times P(\text{Link}=\text{Yes} \mid \text{Ham}) \times P(\text{Domain}=\text{Yes} \mid \text{Ham}) \times P(\text{Urgent}=\text{No} \mid \text{Ham}) = $ ________

**Keputusan Klasifikasi Akhir:** Email diprediksi sebagai [Spam / Ham]
