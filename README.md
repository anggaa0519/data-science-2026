# 📊 Data Science 2026 — Jurnal Pembelajaran

> Repository ini berisi tugas praktikum mata kuliah ** Data Science** — merekam perjalanan belajar dari dasar Python hingga Machine Learning pertama.

---

## 👤 Identitas

| | |
|---|---|
| **Nama** | Angga Anggieanie |
| **NIM** | 250401020172 |
| **Kelas** | IF401 - PJJ Informatika |
| **Mata Kuliah** | Data Science (200302305) |

---

## 🗺️ Peta Perjalanan Belajar

```
Pertemuan 1  →  Pertemuan 2  →  Pertemuan 3  →  Pertemuan 4  →  Pertemuan 5
Python Dasar    EDA & Pandas    Data Cleaning   Statistika      Visualisasi

Pertemuan 6  →  Pertemuan 7  →  Pertemuan 9   →  Pertemuan 10  →  Pertemuan 11
Preprocessing   Regresi Linear  Klasifikasi 1    Klasifikasi 2    Clustering

Pertemuan 12  →  Pertemuan 13
Asosiasi Data    Deep Learning & NLP
```

---

## 📚 Ringkasan Per Pertemuan

### Pertemuan 1 : Python Dasar untuk Data Science
📄 [`Pertemuan1_ANGGA-ANGGIEANIE_250401020172.ipynb`](Pertemuan1_ANGGA-ANGGIEANIE_250401020172.ipynb)

Notebook pertama: berkenalan dengan Python sebagai alat utama Data Science.

**Topik yang dipelajari:**
- Output sederhana dengan `print()`
- Variabel dan tipe data dasar: `str`, `int`, `float`, `bool`
- F-string untuk menyisipkan variabel ke dalam teks
- List dan perulangan `for` dengan `enumerate()`
- Membuat fungsi dengan `def` dan `return`

**Tools yang diperkenalkan:** Python · Google Colab · Jupyter Notebook · GitHub

---

### Pertemuan 2 : Eksplorasi Data Awal (EDA) dengan Pandas
📄 [`Pertemuan2_ANGGA-ANGGIEANIE_250401020172.ipynb`](Pertemuan2_ANGGA-ANGGIEANIE_250401020172.ipynb)

Dataset: **Titanic** (891 penumpang, 12 kolom) diakses langsung dari URL.

**Topik yang dipelajari:**
- Memuat dataset CSV dari URL dengan `pd.read_csv()`
- Inspeksi struktur data: `shape`, `columns`, `head()`
- Analisis *missing values* (jumlah & persentase): `Age` 19.9%, `Cabin` 77.1%
- Filtering data: wanita kelas 1 (`Sex == 'female'` & `Pclass == 1`)
- Agregasi dengan `groupby()` dan `mean()`
- Analisis tingkat keselamatan: Kelas 1 (63%) vs Kelas 3 (24%), wanita (74%) vs pria (19%)

**Library:** `pandas` · `numpy`

---

### Pertemuan 3 : Data Cleaning: Missing Values, Outlier & Ekstraksi Data
📄 [`Pertemuan3_angga_anggieanie_250401020172.ipynb`](Pertemuan3_angga_anggieanie_250401020172.ipynb)

Dataset: **housing_dirty.csv** (properti dengan data kotor) + REST API JSONPlaceholder.

**Topik yang dipelajari:**
- Menghapus baris duplikat dengan `drop_duplicates()`
- Normalisasi string: `str.strip()`, `str.title()`, `str.lower()`
- Imputasi *missing values*: median untuk numerik, modus untuk kategorik
- Penanganan outlier dengan metode **IQR Fence** (`clip(lower, upper)`)
- Validasi data bersih dengan `assert`
- Mengakses **REST API** dengan `requests.get()` dan `pd.json_normalize()`
- Ekspor dataset bersih ke CSV

**Library:** `pandas` · `numpy` · `scipy` · `requests`

---

### Pertemuan 4 : Statistika Dasar & Analisis Data
📄 [`Pertemuan4_Angga_Anggieanie_250401020172.ipynb`](Pertemuan4_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Iris** (150 sampel bunga, 4 fitur numerik, 3 spesies) via `seaborn`.

**Topik yang dipelajari:**
- Statistik deskriptif lengkap: mean, median, std, varians, **skewness**, **kurtosis**
- Interpretasi distribusi: `petal_length` dan `petal_width` menunjukkan distribusi bimodal (kurtosis ≈ -1.4)
- Analisis distribusi dengan **Histogram + KDE**, garis mean & median
- Analisis korelasi antar fitur numerik
- Uji statistik **t-test** (scipy) untuk membandingkan antar kelompok
- Visualisasi **boxplot** per spesies

**Library:** `pandas` · `numpy` · `matplotlib` · `seaborn` · `scipy`

---

### Pertemuan 5 : Visualisasi Data
📄 [`Pertemuan5_Angga_Anggieanie_250401020172.ipynb`](Pertemuan5_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Penguins** (344 baris, 3 spesies penguin di Kepulauan Palmer, Antarktika).

**Topik yang dipelajari:**
- Setup tema global Seaborn (`set_theme`, `whitegrid`, `Set2`)
- Membersihkan data dengan `dropna()` → 333 baris bersih
- **Bar Chart**: rata-rata massa tubuh per spesies (sumbu dari 0 - prinsip akurasi)
- **Scatter Plot**: hubungan panjang paruh vs panjang sirip per spesies
- **Histogram + KDE**: distribusi berat badan per spesies
- **Heatmap Korelasi**: matrix korelasi antar fitur numerik
- Dashboard multi-grafik dengan `GridSpec`

**Library:** `pandas` · `numpy` · `matplotlib` · `seaborn`

---

### Pertemuan 6 : Persiapan Data (End-to-End Preprocessing Pipeline)
📄 [`Pertemuan6_Angga_Anggieanie_250401020172.ipynb`](Pertemuan6_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Titanic** (dataset yang sama dari pertemuan 2, kali ini difokuskan untuk pemodelan ML).

**Topik yang dipelajari:**
- EDA singkat: 177 missing `age` (~20%), 2 missing `embarked`, target `survived` imbalanced (61.6% vs 38.4%)
- **Handling Missing Values**: median untuk `age` (28.0), modus 'S' untuk `embarked`
- **One-Hot Encoding** kolom nominal dengan `pd.get_dummies()` + `drop_first=True` (hindari dummy variable trap)
- **Train-Test Split** stratified 80:20 → 712 train / 179 test (`stratify=y`)
- **Feature Scaling** dengan `StandardScaler`: `fit_transform()` hanya pada train, `transform()` pada test
- Konsep penting: **mencegah data leakage** - split sebelum scaling, test set tidak pernah digunakan untuk fit

**Library:** `pandas` · `numpy` · `seaborn` · `sklearn`

---

### Pertemuan 7 : Pengantar Machine Learning: Regresi Linear
📄 [`Pertemuan7_Angga_Anggieanie_250401020172.ipynb`](Pertemuan7_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Gaji Sintetis** - 300 baris, 4 kolom, dibuat dengan `np.random.seed(42)` untuk reproducibility.

| Fitur | Tipe | Keterangan |
|---|---|---|
| `pengalaman` | Numerik | Uniform 0-20 tahun |
| `edu` | Kategorik | 0=SMA · 1=D3 · 2=S1 |
| `kota` | Kategorik | Jakarta / Surabaya / Bandung |
| `gaji` | Target (juta) | mean=27.40 · std=13.41 · range 1.67–54.22 |

**Formula pembangkit dataset:**
```
gaji = 3.0 + 2.2×pengalaman + 1.5×edu + 4.0×(kota=='Jakarta') + noise(0, 2)
```

**Pipeline end-to-end yang dibangun:**
1. **Pembuatan dataset sintetis** - `np.random` dengan seed untuk reproducibility
2. **Eksplorasi visual** - scatter plot pengalaman vs gaji, diwarnai per kota
3. **Preprocessing** - One-Hot Encoding `kota` (`drop_first=True`), train-test split 80:20
4. **Pemodelan** - `LinearRegression` dari `sklearn`
5. **Evaluasi model** - MAE, MSE, RMSE, R²
6. **Interpretasi koefisien** - memverifikasi koefisien hasil model mendekati nilai formula asli (≈2.2, ≈1.5, ≈4.0)

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `sklearn`

---

### Pertemuan 9 : Algoritma Klasifikasi (Bagian 1) - Logistic Regression & Decision Tree
📄 [`Pertemuan9_Angga_Anggieanie_250401020172.ipynb`](Pertemuan9_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Breast Cancer Wisconsin** (built-in sklearn) - 569 sampel, 30 fitur numerik.

| Kelas | Label | Jumlah | Persentase |
|---|---|---|---|
| Malignant (Ganas) | 0 | 212 | 37.3% |
| Benign (Jinak) | 1 | 357 | 62.7% |

**Topik yang dipelajari:**
- **Logistic Regression**: model linear untuk klasifikasi biner, interpretasi probabilitas output
- **Decision Tree**: model berbasis aturan if-else, visualisasi pohon keputusan
- **Evaluasi Klasifikasi**: Accuracy, Precision, Recall, F1-Score, Confusion Matrix
- **ROC Curve & AUC**: mengukur kemampuan diskriminasi model di berbagai threshold
- Perbandingan performa Logistic Regression vs Decision Tree

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `sklearn`

---

### Pertemuan 10 : Algoritma Klasifikasi (Bagian 2) - Random Forest & Imbalanced Dataset
📄 [`Pertemuan10_Angga_Anggieanie_250401020172.ipynb`](Pertemuan10_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Telco Customer Churn** (sintetis) - 7.043 baris, 12 kolom.

| Kolom | Keterangan |
|---|---|
| `tenure`, `MonthlyCharges`, `TotalCharges` | Fitur numerik |
| `SeniorCitizen`, `Partner`, `Dependents` | Fitur demografis |
| `PhoneService`, `InternetService`, `Contract` | Fitur layanan |
| `PaperlessBilling`, `PaymentMethod` | Fitur billing |
| `Churn` | Target: 0=No (5.529, 78.5%) · 1=Yes (1.514, 21.5%) |

Dataset ini **imbalanced** - kelas minoritas (Churn=Yes) hanya 21.5%.

**Topik yang dipelajari:**
- **Random Forest**: ensemble learning dengan banyak Decision Tree, konsep bagging
- **Feature Importance**: mengidentifikasi fitur paling berpengaruh terhadap churn
- **Penanganan Imbalanced Dataset**: strategi class weighting dan teknik resampling
- Perbandingan model baseline vs model yang sudah disesuaikan untuk imbalanced data
- Evaluasi dengan metrik yang tepat untuk imbalanced data (Precision, Recall, F1)

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `sklearn`

---

### Pertemuan 11 : Unsupervised Learning - Segmentasi Pelanggan dengan K-Means & Hierarchical Clustering
📄 [`Pertemuan11_Angga_Anggieanie_250401020172.ipynb`](Pertemuan11_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Data Pelanggan Sintetis** - 300 baris, 4 kolom, 3 kelompok tersembunyi.

| Kolom | Keterangan |
|---|---|
| `pendapatan_tahunan` | mean=69.96, std=33.82 |
| `skor_belanja` | mean=53.23, std=27.41 |
| `usia` | mean=42.07 |
| `gender` | Kategorik |

**3 Kelompok Tersembunyi:**
| Segmen | Pendapatan | Skor Belanja |
|---|---|---|
| Hemat | rendah (~30) | rendah (~20) |
| Menengah | sedang (~70) | sedang (~55) |
| Boros | tinggi (~110) | tinggi (~85) |

**Topik yang dipelajari:**
- **K-Means Clustering**: algoritma iteratif berbasis centroid, inisialisasi k-means++
- **Elbow Method**: menentukan jumlah cluster optimal dengan melihat titik siku pada grafik inertia
- **Silhouette Score**: mengukur kualitas cluster (seberapa mirip objek dengan clusternya sendiri)
- **Hierarchical Clustering**: membangun dendrogram untuk memvisualisasikan hirarki cluster
- **Agglomerative Clustering**: pendekatan bottom-up untuk hierarchical clustering
- Visualisasi 2D dan 3D hasil segmentasi pelanggan

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `sklearn` · `mpl_toolkits`

---

### Pertemuan 12 : Asosiasi Data & Sistem Rekomendasi - Market Basket Analysis & Content-Based Filtering
📄 [`Pertemuan12_Angga_Anggieanie_250401020172.ipynb`](Pertemuan12_Angga_Anggieanie_250401020172.ipynb)

**Bagian 1 - Market Basket Analysis (Apriori)**

Dataset: **Transaksi Belanja Sintetis** — 50 transaksi, 10 produk.

Produk: Roti · Selai · Susu · Sereal · Telur · Keju · Kopi · Gula · Teh · Mentega

Pola yang disuntikkan: **Roti sering dibeli bersama Selai** (dalam 20 transaksi).

**Topik yang dipelajari:**
- **TransactionEncoder** (`mlxtend`): mengubah list transaksi menjadi format one-hot matrix
- **Algoritma Apriori**: menemukan frequent itemsets berdasarkan minimum support
- **Association Rules**: menurunkan aturan asosiasi dengan metrik Support, Confidence, dan Lift
- Interpretasi aturan: `{Roti} → {Selai}` sebagai contoh aturan dengan Lift > 1

**Bagian 2 - Content-Based Filtering**

**Topik yang dipelajari:**
- Membangun sistem rekomendasi sederhana berbasis kemiripan konten (fitur produk)
- Menghitung skor kemiripan antar item
- Menghasilkan rekomendasi item yang relevan berdasarkan item yang sudah disukai pengguna

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `mlxtend`

---

### Pertemuan 13 : Pengantar Topik Lanjutan — Deep Learning & NLP Dasar
📄 [`Pertemuan13_Angga_Anggieanie_250401020172.ipynb`](Pertemuan13_Angga_Anggieanie_250401020172.ipynb)

**Bagian 1 : Klasifikasi Non-Linear dengan Neural Network**

Dataset: **make_moons** (sklearn) - dua kelas berbentuk bulan sabit yang saling bertautan.

Dataset ini **linearly non-separable** - tidak bisa dipisahkan dengan satu garis lurus, sehingga membutuhkan model non-linear seperti Neural Network.

**Topik yang dipelajari:**
- **Neural Network**: arsitektur layer input → hidden layer(s) → output, konsep forward propagation
- **Activation Function Non-Linear**: ReLU, Sigmoid - mengapa activation function non-linear dibutuhkan
- **Backpropagation**: cara Neural Network belajar dari error dengan gradient descent
- Perbandingan batas keputusan (decision boundary) Logistic Regression vs Neural Network pada data non-linear
- Visualisasi decision boundary untuk memahami kemampuan model

**Bagian 2 : Analisis Sentimen dengan TF-IDF**

**Topik yang dipelajari:**
- **TF-IDF (Term Frequency - Inverse Document Frequency)**: mengubah teks menjadi representasi numerik berbobot
- **Analisis Sentimen**: mengklasifikasikan teks sebagai positif / negatif / netral
- Pipeline NLP: teks mentah → preprocessing → TF-IDF → klasifikasi
- Evaluasi model teks dengan metrik klasifikasi standar

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `sklearn`

---

## 🛠️ Stack Teknologi

| Kategori | Tools |
|---|---|
| Bahasa | Python 3 |
| Lingkungan | Google Colab · Jupyter Notebook |
| Data Manipulation | `pandas` · `numpy` |
| Visualisasi | `matplotlib` · `seaborn` · `mpl_toolkits` |
| Statistik | `scipy` |
| Machine Learning | `scikit-learn` |
| Association Rules | `mlxtend` |
| Data Akses | `requests` (REST API) |
| Version Control | Git · GitHub |

---

## 📈 Progres Pembelajaran

| # | Pertemuan | Topik Utama | Dataset | Status |
|---|---|---|---|---|
| 1 | Pertemuan 1 | Python Dasar | — | ✅ Selesai |
| 2 | Pertemuan 2 | EDA & Pandas | Titanic | ✅ Selesai |
| 3 | Pertemuan 3 | Data Cleaning | Housing Dirty + API | ✅ Selesai |
| 4 | Pertemuan 4 | Statistika Dasar | Iris | ✅ Selesai |
| 5 | Pertemuan 5 | Visualisasi Data | Penguins | ✅ Selesai |
| 6 | Pertemuan 6 | Data Preprocessing | Titanic | ✅ Selesai |
| 7 | Pertemuan 7 | Regresi Linear | Gaji Sintetis | ✅ Selesai |
| 9 | Pertemuan 9 | Klasifikasi: Logistic Regression & Decision Tree | Breast Cancer Wisconsin | ✅ Selesai |
| 10 | Pertemuan 10 | Random Forest & Imbalanced Dataset | Telco Customer Churn | ✅ Selesai |
| 11 | Pertemuan 11 | Clustering: K-Means & Hierarchical | Data Pelanggan Sintetis | ✅ Selesai |
| 12 | Pertemuan 12 | Asosiasi Data & Sistem Rekomendasi | Transaksi Belanja Sintetis | ✅ Selesai |
| 13 | Pertemuan 13 | Deep Learning & NLP Dasar | make_moons + Teks Sentimen | ✅ Selesai |

---

## 📂 Struktur Repository

```
data-science-2026/
│
├── Pertemuan1_ANGGA-ANGGIEANIE_250401020172.ipynb    # Python Dasar
├── Pertemuan2_ANGGA-ANGGIEANIE_250401020172.ipynb    # EDA & Pandas
├── Pertemuan3_angga_anggieanie_250401020172.ipynb    # Data Cleaning
├── Pertemuan4_Angga_Anggieanie_250401020172.ipynb    # Statistika
├── Pertemuan5_Angga_Anggieanie_250401020172.ipynb    # Visualisasi
├── Pertemuan6_Angga_Anggieanie_250401020172.ipynb    # Preprocessing
├── Pertemuan7_Angga_Anggieanie_250401020172.ipynb    # Regresi Linear 
├── Pertemuan9_Angga_Anggieanie_250401020172.ipynb    # Klasifikasi Bag.1 
├── Pertemuan10_Angga_Anggieanie_250401020172.ipynb   # Klasifikasi Bag.2 
├── Pertemuan11_Angga_Anggieanie_250401020172.ipynb   # Clustering 
├── Pertemuan12_Angga_Anggieanie_250401020172.ipynb   # Asosiasi & Rekomendasi 
├── Pertemuan13_Angga_Anggieanie_250401020172.ipynb   # Deep Learning & NLP 
├── README.md
└── LICENSE
```

---

*Repository ini merupakan bagian dari tugas praktikum mata kuliah Pengantar Data Science, Program Studi PJJ Informatika, 2026.*
