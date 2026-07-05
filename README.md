# 📊 Data Science 2026 — Angga Anggieanie

> Repositori ini mendokumentasikan perjalanan belajar mata kuliah **Pengantar Data Science** semester genap 2025/2026.

| | |
|---|---|
| **Nama** | Angga Anggieanie |
| **NIM** | 250401020172 |
| **Kelas** | IF401 |
| **Mata Kuliah** | Pengantar Data Science (200302305) |
| **SKS** | 3 SKS |
| **Dosen makul** | Syahid Abdullah, S.Si, M.Kom |
| **Program Studi** | Informatika |

---

## 🗂️ Daftar Pertemuan

| Pertemuan | Topik | Dataset | Notebook |
|-----------|-------|---------|----------|
| 1 | Pengantar Python untuk Data Science | — | `Pertemuan1_*.ipynb` |
| 2 | NumPy & Pandas | — | `Pertemuan2_*.ipynb` |
| 3 | Data Cleaning | — | `Pertemuan3_*.ipynb` |
| 4 | Statistika Dasar & Analisis Data | Iris | `Pertemuan4_Angga_Anggieanie_250401020172.ipynb` |
| 5 | Visualisasi Data | Penguins | `Pertemuan5_Angga_Anggieanie_250401020172.ipynb` |
| 6 | Persiapan Data | Titanic | `Pertemuan6_Angga_Anggieanie_250401020172.ipynb` |
| 7 | Pengantar ML: Regresi Linear | Gaji Sintetis | `Pertemuan7_Angga_Anggieanie_250401020172.ipynb` |
| 9 | Algoritma Klasifikasi (Bagian 1) | Breast Cancer Wisconsin | `Pertemuan9_Angga_Anggieanie_250401020172.ipynb` |
| 10 | Algoritma Klasifikasi (Bagian 2) — Ensemble | Telco Customer Churn | `Pertemuan10_Angga_Anggieanie_250401020172.ipynb` |
| 11 | Unsupervised Learning: Clustering | Segmentasi Pelanggan | `Pertemuan11_Angga_Anggieanie_250401020172.ipynb` |

---

## 📚 Ringkasan Materi per Pertemuan

### Pertemuan 1 — Pengantar Python untuk Data Science
Materi dasar pemrograman Python yang relevan untuk data science: tipe data, struktur kontrol, fungsi, dan pengenalan ekosistem library (NumPy, Pandas, Matplotlib).

### Pertemuan 2 — NumPy & Pandas
Operasi array dengan NumPy (indexing, broadcasting, operasi vektor) dan manipulasi DataFrame dengan Pandas (seleksi kolom, filtering, groupby, merge).

### Pertemuan 3 — Data Cleaning
Penanganan data kotor di dunia nyata: deteksi dan penanganan missing values, duplikat, tipe data tidak konsisten, dan outlier menggunakan Pandas.

---

### Pertemuan 4 — Statistika Dasar & Analisis Data

**Dataset:** Iris (150 baris, 5 kolom — sepal_length, sepal_width, petal_length, petal_width, species)

**Topik yang dipelajari:**
- Ukuran pemusatan: mean, median, modus
- Ukuran penyebaran: varians, standar deviasi, IQR, kuartil
- Distribusi data: skewness & kurtosis
- Analisis univariat: histogram + KDE, boxplot, violin plot
- Analisis bivariat: scatter plot, korelasi Pearson & Spearman, heatmap

**Temuan utama:**
- `petal_length` ↔ `petal_width`: r = **0.963** (sangat kuat positif) — pasangan paling berkorelasi
- `sepal_width` ↔ `petal_length`: r = **−0.428** (negatif lemah) — pasangan terendah
- Distribusi bimodal pada kolom petal karena pemisahan *Setosa* vs dua spesies lain

**Tools:** `pandas`, `numpy`, `scipy`, `matplotlib`, `seaborn`

---

### Pertemuan 5 — Visualisasi Data

**Dataset:** Penguins (344 baris, 7 kolom; 333 setelah dropna) — 3 spesies dari Kepulauan Palmer, Antarktika

**Topik yang dipelajari:**
- 5 prinsip visualisasi efektif: Clarity, Accuracy, Efficiency, Aesthetics, Context
- Matplotlib: Figure/Axes architecture, bar chart, line chart, scatter plot
- Seaborn: histplot+KDE, boxplot, violin plot, scatter plot, pair plot
- Framework interpretasi: **What? / So what? / Now what?**
- Dashboard statis 2×2 dengan `GridSpec`

**Hasil utama:**
- Gentoo ≈ 5.076 g (rata-rata massa tubuh, ~37% lebih berat dari Adelie/Chinstrap)
- Distribusi massa tubuh: bimodal, skewness +0.47
- Panjang flipper Gentoo (median ≈ 216 mm) terpisah jelas dari dua spesies lain
- Korelasi flipper vs massa tubuh: **r = 0.873** (kuat positif)

**Output:** `dashboard_penguins.png` (dpi=150)

**Tools:** `matplotlib`, `seaborn`, `pandas`, `numpy`

---

### Pertemuan 6 — Persiapan Data

**Dataset:** Titanic (891 baris, target: `survived`)

**Topik yang dipelajari:**
- Pipeline preprocessing yang benar: EDA → handling missing → encoding → split → scaling
- One-Hot Encoding dengan `drop_first=True` (hindari dummy variable trap)
- Handling missing: `fillna(median)` untuk `age`, `fillna(mode)` untuk `embarked`
- Stratified train-test split: menjaga proporsi kelas di train dan test
- Feature scaling: StandardScaler — **fit hanya pada training set**, transform pada test
- **Prinsip anti data leakage:** split dulu, baru fit scaler pada X_train

**Hasil preprocessing:**
- `age` 177 NaN → diisi median **28.0**; `embarked` 2 NaN → diisi modus **'S'**
- Encoding: `sex` → `sex_male`; `embarked` → `embarked_Q`, `embarked_S`
- Split stratified: **712 train / 179 test**; proporsi survived ≈ 0.616:0.384 identik di keduanya
- Kolom numerik ter-scale: mean ≈ 0, std ≈ 1 pada training set

**Tools:** `pandas`, `seaborn`, `sklearn` (OHE, StandardScaler, train_test_split)

---

### Pertemuan 7 — Pengantar Machine Learning: Regresi Linear

**Dataset:** Gaji sintetis (300 baris, `np.random.seed(42)`)  
Formula: `gaji = 3.0 + 2.2×pengalaman + 1.5×edu + 4.0×(Jakarta) + N(0,2)`

**Topik yang dipelajari:**
- Supervised vs Unsupervised Learning; Classification vs Regression
- Persamaan regresi linear: ŷ = β₀ + β₁x₁ + … + βₙxₙ
- Cost function MSE dan Ordinary Least Squares (OLS)
- Implementasi scikit-learn: pola Fit → Predict → Evaluate
- Metrik evaluasi: MAE, RMSE, R²
- Visualisasi: Actual vs Predicted plot, Residual Plot

**Hasil model (Multiple Linear Regression):**

| Parameter | Nilai |
|-----------|-------|
| β₀ (intercept) | 27.514 |
| β pengalaman | 13.042 (dominan) |
| β kota_Jakarta | 1.837 |
| β edu | 1.188 |
| β kota_Surabaya | −0.292 |

| Metrik | Nilai |
|--------|-------|
| MAE | 1.649 juta Rp |
| RMSE | 2.123 juta Rp |
| **R²** | **0.974 (97.4%)** |

Residual plot acak → asumsi linearitas terpenuhi. Model sangat baik sebagai baseline.

**Output:** `evaluasi_regresi.png`

**Tools:** `numpy`, `pandas`, `matplotlib`, `seaborn`, `sklearn`

---

### Pertemuan 9 — Algoritma Klasifikasi (Bagian 1)

**Dataset:** Breast Cancer Wisconsin — bawaan scikit-learn  
569 sampel, 30 fitur numerik (ukuran & tekstur sel), target biner: 0 = Malignant (ganas), 1 = Benign (jinak)

**Topik yang dipelajari:**
- Klasifikasi vs Regresi: output kategori diskret vs nilai kontinu
- Binary vs Multiclass Classification
- **Logistic Regression:** fungsi Sigmoid σ(z) = 1/(1+e⁻ᶻ), decision boundary, threshold
- **Decision Tree:** Gini Impurity, Entropy, overfitting & max_depth, feature importance, plot_tree
- **Metrik evaluasi klasifikasi:** Confusion Matrix (TP/TN/FP/FN), Accuracy, Precision, Recall, F1-Score
- Kapan menggunakan metrik mana: Recall untuk diagnosis medis, Precision untuk spam filter

**Preprocessing:**
- Stratified split 80:20 → **455 train / 114 test**
- StandardScaler fit pada training set (untuk Logistic Regression); Decision Tree tanpa scaling

**Perbandingan hasil dua model pada test set:**

| Model | Accuracy | Precision | Recall | F1-Score | FN (terlewat) |
|-------|----------|-----------|--------|----------|---------------|
| **Logistic Regression** | **98.2%** | **98.6%** | **98.6%** | **98.6%** | **1** |
| Decision Tree (depth=4) | 92.1% | 94.4% | 93.1% | 93.7% | 5 |

**Kesimpulan kritis:** Recall adalah metrik paling penting untuk diagnosis kanker — False Negative (kanker terlewat) berakibat fatal. Logistic Regression unggul dengan hanya **1 kasus terlewat** vs 5 pada Decision Tree. Fitur `worst radius` (importance 75.1%) adalah pembeda utama pada Decision Tree.

**Output:** `evaluasi_klasifikasi.png`, `decision_tree_viz.png`

**Tools:** `sklearn` (LogisticRegression, DecisionTreeClassifier, confusion_matrix, classification_report), `matplotlib`, `seaborn`, `pandas`, `numpy`

---

### Pertemuan 10 — Algoritma Klasifikasi (Bagian 2): Ensemble Learning & Imbalanced Dataset

**Dataset:** Telco Customer Churn (sintetis, ~7.043 pelanggan, 19 fitur) — target `Churn` (Yes/No), proporsi churn ~21.5% (imbalanced)

**Topik yang dipelajari:**
- **Ensemble Learning:** menggabungkan banyak model (weak learners) untuk prediksi lebih kuat; Bagging (paralel, turunkan variance) vs Boosting (sekuensial, turunkan bias)
- **Random Forest:** bootstrap sampling, random feature selection (√fitur), majority voting/aggregation, Out-of-Bag estimation
- **Accuracy Paradox:** akurasi tinggi dapat menyembunyikan kegagalan total mendeteksi kelas minoritas
- **Penanganan Imbalanced Dataset:** level data (Oversampling, **SMOTE**, Undersampling) vs level algoritma (`class_weight`, threshold tuning)
- Metrik: Precision, Recall, F1-Score, ROC-AUC

**Perbandingan 3 skenario penanganan imbalance (test set 1.409 sampel, fokus kelas Churn):**

| Skenario | Accuracy | Recall | F1-Score | ROC-AUC |
|---|---|---|---|---|
| Baseline (tanpa penanganan) | 77.5% | 16.5% | 0.240 | 0.733 |
| class_weight="balanced" | 77.6% | 15.5% | 0.230 | 0.734 |
| **SMOTE** | 73.8% | **38.9%** | **0.390** | 0.721 |
| class_weight + threshold=0.35 | — | **42.6%** | **0.417** | — |

**Kesimpulan kritis:** Accuracy paradox terkonfirmasi — baseline berakurasi 77.5% namun melewatkan >80% churner nyata. SMOTE dan threshold tuning sama-sama efektif meningkatkan Recall. Fitur pendorong utama churn: `MonthlyCharges`, `TotalCharges`, `tenure` — pelanggan baru dengan tagihan tinggi paling berisiko.

**Output:** `evaluasi_churn.png`, `feature_importance_churn.png`

**Tools:** `sklearn` (RandomForestClassifier, roc_auc_score), `imbalanced-learn` (SMOTE), `matplotlib`, `seaborn`, `pandas`, `numpy`

---

### Pertemuan 11 — Unsupervised Learning: Clustering (K-Means & Hierarchical)

**Dataset:** Segmentasi Pelanggan sintetis (300 sampel, 3 kelompok tersembunyi) — fitur `pendapatan_tahunan`, `skor_belanja`, `usia`, `gender`

**Topik yang dipelajari:**
- Transisi dari Supervised ke **Unsupervised Learning** — menemukan struktur data tanpa label (y)
- **K-Means Clustering:** fungsi objektif WCSS, algoritma iteratif Assignment-Update, inisialisasi `k-means++`
- **Metode Elbow:** menentukan K optimal dari grafik WCSS vs K
- **Silhouette Score:** validasi K optimal secara kuantitatif (rentang −1 hingga +1)
- **Hierarchical Clustering:** Agglomerative vs Divisive, metode linkage (Single, Complete, Average, **Ward**), membaca dendrogram

**Hasil penentuan K optimal:**
- Metode Elbow: penurunan WCSS melandai tajam di **K=3**
- Silhouette Score tertinggi: **K=3 (0.695)** — mengonfirmasi hasil Elbow

**Hasil segmentasi (K-Means, K=3):**

| Segmen | Pendapatan Tahunan | Skor Belanja | Jumlah |
|---|---|---|---|
| Hemat | ~29 juta | ~20 | 100 |
| Menengah | ~71 juta | ~55 | 99 |
| Boros/Premium | ~109 juta | ~84 | 101 |

**Validasi silang:** Hierarchical Clustering (Ward linkage) menghasilkan pembagian 3 cluster yang sangat konsisten dengan K-Means — **Adjusted Rand Index = 0.99** (hampir identik sempurna).

**Output:** `segmentasi_kmeans.png`, `dendrogram_pelanggan.png`

**Tools:** `sklearn` (KMeans, AgglomerativeClustering, silhouette_score, adjusted_rand_score), `scipy.cluster.hierarchy` (dendrogram, linkage), `matplotlib`, `seaborn`, `pandas`, `numpy`

---

## 🛠️ Tech Stack

```
Python 3.10+
├── NumPy          — komputasi numerik & array
├── Pandas         — manipulasi DataFrame
├── Matplotlib     — visualisasi dasar (Figure/Axes)
├── Seaborn        — visualisasi statistik
├── SciPy          — uji statistik (Pearson, Spearman)
└── scikit-learn   — preprocessing & machine learning
    ├── datasets: load_breast_cancer
    ├── preprocessing: StandardScaler, OneHotEncoder
    ├── model_selection: train_test_split
    ├── linear_model: LinearRegression, LogisticRegression
    ├── tree: DecisionTreeClassifier, plot_tree
    ├── ensemble: RandomForestClassifier
    ├── cluster: KMeans, AgglomerativeClustering
    └── metrics: MAE, MSE, R², confusion_matrix, accuracy, precision, recall, F1,
                 roc_auc_score, silhouette_score, adjusted_rand_score
imbalanced-learn (imblearn)
└── over_sampling: SMOTE
scipy.cluster.hierarchy
└── dendrogram, linkage (Ward)
```

---

## 📁 Struktur Repositori

```
data-science-2026/
├── README.md
├── Pertemuan4_Angga_Anggieanie_250401020172.ipynb   # Statistika & Analisis Data (Iris)
├── Pertemuan5_Angga_Anggieanie_250401020172.ipynb   # Visualisasi Data (Penguins)
├── Pertemuan6_Angga_Anggieanie_250401020172.ipynb   # Persiapan Data (Titanic)
├── Pertemuan7_Angga_Anggieanie_250401020172.ipynb   # Regresi Linear (Gaji Sintetis)
├── Pertemuan9_Angga_Anggieanie_250401020172.ipynb   # Klasifikasi (Breast Cancer)
├── Pertemuan10_Angga_Anggieanie_250401020172.ipynb  # Random Forest & Imbalanced (Churn)
├── Pertemuan11_Angga_Anggieanie_250401020172.ipynb  # Clustering (Segmentasi Pelanggan)
```

---

## 📖 Referensi

- Fisher, R. A. (1936). The use of multiple measurements in taxonomic problems.
- McKinney, W. (2022). *Python for Data Analysis* (3rd ed.). O'Reilly.
- VanderPlas, J. (2016). *Python Data Science Handbook*. O'Reilly.
- Waskom, M. L. (2021). Seaborn: Statistical data visualization. *JOSS*, 6(60).
- Knaflic, C. N. (2015). *Storytelling with Data*. Wiley.
- Géron, A. (2022). *Hands-On Machine Learning* (3rd ed.). O'Reilly. [Bab 3, 6 & 9]
- James, G., et al. (2021). *An Introduction to Statistical Learning* (2nd ed.). Springer. [Bab 4 & 12]
- Breiman, L. (2001). Random Forests. *Machine Learning*, 45(1), 5–32.
- Chawla, N. V., et al. (2002). SMOTE: Synthetic Minority Over-sampling Technique. *JAIR*, 16, 321–357.
- MacQueen, J. (1967). Some methods for classification and analysis of multivariate observations.
- Rousseeuw, P. J. (1987). Silhouettes: A graphical aid to cluster analysis. *J. Computational and Applied Mathematics*, 20, 53–65.
- Arthur, D., & Vassilvitskii, S. (2007). k-means++: The Advantages of Careful Seeding.
- scikit-learn Developers. (2024). *scikit-learn Documentation*.

---

*Repositori ini dibuat sebagai bagian dari tugas perkuliahan Pengantar Data Science, Program Studi Informatika.*
