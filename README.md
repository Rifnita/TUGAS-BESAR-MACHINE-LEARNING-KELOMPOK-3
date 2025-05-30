# 🧠 **Perbandingan Algoritma K-Means dan DBSCAN dalam Segmentasi Pasien Berisiko Stroke dengan Penanganan Ketidakseimbangan Data**

---

## 📋 **Deskripsi Singkat Proyek**

Proyek ini bertujuan membandingkan performa dua algoritma clustering, yaitu **K-Means** dan **DBSCAN**, dalam segmentasi pasien yang berisiko stroke. Dataset yang digunakan bersumber dari **Kaggle**, dengan fitur-fitur seperti usia, jenis kelamin, kadar glukosa darah, BMI, dan riwayat kesehatan.

Untuk mengatasi masalah **ketidakseimbangan data** yang umum dalam data medis, digunakan dua pendekatan:
- **SMOTE Tomek**: Kombinasi oversampling dan pembersihan noise.
- **Random Undersampling**: Mengurangi jumlah data dari kelas mayoritas.

Model juga dievaluasi menggunakan **Random Forest Classifier** dan metrik seperti **Silhouette Score** serta **Confusion Matrix**.

---

## 🧠 **Latar Belakang Masalah**

Stroke adalah penyebab utama kematian dan kecacatan jangka panjang di Indonesia dan dunia. Deteksi dini menjadi sangat penting dalam upaya pencegahan.  
Dengan kemajuan **machine learning**, khususnya metode **clustering**, kita dapat mengelompokkan pasien berdasarkan risiko stroke tanpa perlu label. Namun, tantangan besar muncul saat data tidak seimbang — pasien yang tidak mengalami stroke jauh lebih banyak daripada yang mengalaminya.

Dengan membandingkan dua algoritma clustering dan menerapkan teknik penyeimbangan data, proyek ini berupaya menghasilkan model segmentasi pasien yang lebih adil dan akurat.

---

## 📊 **Deskripsi Dataset**

Dataset yang digunakan mencakup **5.110 data pasien**, dengan atribut:

- `gender`: Jenis kelamin  
- `age`: Usia  
- `hypertension`: Riwayat hipertensi  
- `heart_disease`: Riwayat penyakit jantung  
- `ever_married`: Status pernikahan  
- `work_type`: Jenis pekerjaan  
- `Residence_type`: Tinggal di Urban atau Rural  
- `avg_glucose_level`: Rata-rata kadar glukosa  
- `bmi`: Indeks massa tubuh (dilakukan imputasi nilai kosong dengan median)  
- `smoking_status`: Status merokok  
- `stroke`: Target variabel (0: tidak stroke, 1: stroke)

---

## ⚙️ **Algoritma dan Teknik yang Digunakan**

### 🔹 K-Means Clustering  
Mengelompokkan data berdasarkan jarak ke pusat cluster (centroid).  
Sensitif terhadap jumlah cluster dan skala data.

### 🔹 DBSCAN (Density-Based Spatial Clustering)  
Mengelompokkan berdasarkan kepadatan data. Mampu menangani outlier dan bentuk cluster yang tidak beraturan.

### 🔹 SMOTE Tomek  
Membuat data sintetis untuk kelas minoritas dan menghapus pasangan Tomek (data borderline).

### 🔹 Random Undersampling  
Menghapus sebagian data dari kelas mayoritas secara acak.

### 🔹 PCA (Principal Component Analysis)  
Digunakan untuk reduksi dimensi dan visualisasi 2D hasil clustering.

### 🔹 Random Forest Classifier  
Digunakan untuk menguji hasil clustering menggunakan supervised learning dan evaluasi performa klasifikasi.

---

## 🚀 **Langkah-langkah Menjalankan Proyek**

### Prasyarat:
- Python 3.7+
- Jupyter Notebook / VSCode
- Dataset CSV (`stroke-data.csv`)

### Instalasi dependensi:
```bash
pip install numpy pandas matplotlib seaborn scikit-learn imbalanced-learn
```

### Folder penting:
- 📂 `notebooks/` – berisi eksperimen clustering
- 📂 `data/` – letakkan dataset di sini (`stroke-data.csv`)
- 📂 `visualisasi/` – menyimpan output gambar PCA dan confusion matrix

### Tahapan Eksperimen:
1. Pra-pemrosesan: Imputasi nilai kosong, encoding variabel kategorikal, dan normalisasi.
2. Penerapan K-Means dan DBSCAN pada data asli.
3. Penyeimbangan data menggunakan SMOTE Tomek dan Random Undersampling.
4. Clustering ulang pada data yang telah diseimbangkan.
5. Evaluasi hasil menggunakan Silhouette Score dan Confusion Matrix dari Random Forest.
6. Visualisasi hasil clustering dengan PCA.

---

## 📈 **Contoh Output dan Visualisasi**

### 🔍 Clustering dengan K-Means dan DBSCAN

- **Distribusi K-Means (tanpa balancing):**  
  `Counter({0: 400, 1: 250, 2: 120, 3: 80, 4: 50})`

- **Distribusi DBSCAN (tanpa balancing):**  
  `Counter({0: 470, -1: 200, 1: 50})`  
  (*-1 menunjukkan outlier*)

### 📊 Distribusi Setelah SMOTE Tomek dan Undersampling

- K-Means + SMOTETomek: `Counter({0: 350, 1: 350})`  
- DBSCAN + Undersampling: `Counter({0: 100, 1: 100})`

### 🎯 Confusion Matrix (Random Forest)

| Prediksi vs Aktual | Stroke (1) | Tidak Stroke (0) |
|--------------------|------------|------------------|
| Stroke (1)         | 942        | 116              |
| Tidak Stroke (0)   | 28         | 859              |

### 🔍 Evaluasi

- **Silhouette Score:** digunakan untuk mengevaluasi kualitas cluster  
- **PCA Scatter Plot:** digunakan untuk visualisasi distribusi cluster

---

## 📝 **Kesimpulan**

- **DBSCAN** unggul dalam mendeteksi noise dan pola tidak beraturan dibanding **K-Means**.
- Penyeimbangan data (**SMOTE Tomek** dan **Random Undersampling**) meningkatkan kualitas clustering dan klasifikasi.
- Hasil clustering membantu dalam **segmentasi pasien berisiko stroke** yang lebih akurat, yang berpotensi digunakan untuk skrining awal dalam sistem medis.

---

## 👥 **Anggota Tim**

- Raditya Ezra Farandi (122140209) – Project Leader  
- Femmy Aprillia Putri (122140006) – Data Analyst  
- Yohana Anzelika Sitepu (122140010) – Data Engineer  
- Joshia Fernandes Sectio Purba (122140170) – ML Engineer  
- Nasya Aulia Efendi (122140016) – ML Engineer  
- Zulfa Puri Anjani (122140023) – Evaluator & Visualisasi  
- Rifnita Cahyani Hidayat (122140031) – Dokumentasi & GitHub

---

## 📂 **Referensi Dataset**

https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset
