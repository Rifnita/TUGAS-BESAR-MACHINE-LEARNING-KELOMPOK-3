# 🧠 **Perbandingan Algoritma K-Means dan DBSCAN untuk Segmentasi Pasien Berisiko Stroke pada Dataset Tidak Seimbang**

---

## 📋 **Deskripsi Singkat Proyek**

Proyek ini bertujuan untuk membandingkan dua algoritma clustering — **K-Means** dan **DBSCAN** — dalam mengelompokkan pasien berdasarkan tingkat risiko stroke, khususnya pada dataset dengan distribusi tidak seimbang.

Analisis dilakukan terhadap dataset **Stroke Prediction** dari Kaggle yang berisi informasi medis seperti usia, tekanan darah, glukosa, dan indeks massa tubuh. Dalam proyek ini, **tidak dilakukan balancing** seperti SMOTE atau undersampling, melainkan fokus pada bagaimana kedua algoritma bekerja secara alami pada data yang tidak seimbang.

Evaluasi dilakukan menggunakan metrik **Silhouette Score**, **Adjusted Rand Index (ARI)**, dan **Confusion Matrix**.

---

## 🧠 **Latar Belakang Masalah**

Stroke merupakan penyebab utama kematian dan kecacatan jangka panjang secara global, termasuk di Indonesia. Upaya deteksi dini menjadi penting agar penanganan dapat dilakukan lebih cepat.

Machine learning, khususnya metode **unsupervised learning** seperti clustering, memungkinkan identifikasi kelompok pasien berisiko stroke berdasarkan kemiripan karakteristik medis tanpa perlu label. Namun, tantangan besar muncul karena **data pasien stroke sangat tidak seimbang** — mayoritas pasien tidak mengalami stroke.

Melalui proyek ini, dilakukan perbandingan kinerja antara **K-Means** dan **DBSCAN** untuk mengetahui metode mana yang lebih efektif dalam kondisi distribusi data seperti ini.

---

## 📊 **Deskripsi Dataset**

Dataset berisi **5.110 entri pasien** dan memiliki 11 fitur utama:

- `age`: Usia pasien
- `hypertension`: Riwayat hipertensi (0 = tidak, 1 = ya)
- `heart_disease`: Riwayat penyakit jantung
- `avg_glucose_level`: Rata-rata kadar glukosa
- `bmi`: Indeks massa tubuh (nilai kosong diimputasi dengan median)
- `stroke`: Target label (0 = tidak stroke, 1 = stroke)

Fitur lain seperti `gender`, `smoking_status`, `work_type`, dll., diabaikan untuk fokus pada fitur numerik.  
**Distribusi stroke sangat tidak seimbang**: hanya 4.87% data yang menunjukkan pasien mengalami stroke.

---

## ⚙️ **Algoritma dan Teknik yang Digunakan**

### 🔹 K-Means Clustering  
- Mengelompokkan berdasarkan jarak ke centroid.
- Jumlah klaster ditentukan sebanyak **2** (stroke dan non-stroke).
- Perlu data dinormalisasi dan PCA digunakan sebelum clustering.

### 🔹 DBSCAN (Density-Based Spatial Clustering)  
- Tidak memerlukan jumlah cluster di awal.
- Mendeteksi **outlier** sebagai noise.
- Parameter: `eps = 3.5`, `min_samples = 3`.

### 🔹 PCA (Principal Component Analysis)  
- Reduksi dimensi ke 2D untuk visualisasi klaster.
- Menjelaskan **55.3%** variansi total data.

---

## 🧪 **Tahapan Eksperimen**

1. Imputasi nilai kosong (`bmi`) dengan **median**.
2. Normalisasi data menggunakan **StandardScaler**.
3. Reduksi dimensi dengan **PCA** menjadi 2 komponen.
4. Clustering dengan **K-Means** dan **DBSCAN**.
5. Evaluasi dengan **Silhouette Score**, **ARI**, dan **Confusion Matrix**.

---

## 📈 **Hasil Evaluasi dan Visualisasi**

### 🎯 Kinerja Model

| Metrik Evaluasi       | K-Means | DBSCAN (non-noise) |
|------------------------|---------|---------------------|
| Silhouette Score       | 0.5154  | 0.5657              |
| Davies-Bouldin Index   | 1.4056  | 0.7809              |
| Adjusted Rand Index    | 0.1312  | 0.1261              |

### 🔍 Confusion Matrix (K-Means)

|                      | Prediksi Stroke | Prediksi Tidak Stroke |
|----------------------|------------------|------------------------|
| Stroke (aktual)      |  44              | 205                    |
| Tidak Stroke (aktual)| 1125             | 3536                   |

### 🧯 Outlier

- DBSCAN mendeteksi beberapa data sebagai **noise** (label `-1`), tidak termasuk dalam cluster manapun.
- Hal ini membantu mengidentifikasi **kasus ekstrem atau anomali** dalam data pasien.

### 🧬 Visualisasi PCA

Scatter plot digunakan untuk memvisualisasikan hasil clustering oleh K-Means dan DBSCAN. DBSCAN menunjukkan **pemisahan yang lebih fleksibel dan outlier-aware**, sedangkan K-Means cenderung membentuk klaster bulat.

---

## 📝 **Kesimpulan**

- **DBSCAN** lebih unggul dalam memisahkan data yang tidak beraturan dan mendeteksi noise dibandingkan **K-Means**.
- **Ketidakseimbangan data** mempengaruhi kualitas clustering — DBSCAN sedikit lebih tahan terhadap efek ini.
- PCA sangat membantu dalam visualisasi hasil dan analisis dua dimensi.
- Model clustering ini berpotensi digunakan untuk **skrining awal pasien** dalam sistem kesehatan digital, meskipun dibutuhkan pengujian lebih lanjut.

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

Dataset tersedia di:  
https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset
