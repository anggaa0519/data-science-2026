# 📊 Data Science 2026 — Jurnal Pembelajaran

> Repository ini berisi tugas praktikum mata kuliah **Pengantar Data Science** — merekam perjalanan belajar dari dasar Python hingga Machine Learning pertama.

---

## 👤 Identitas

| | |
|---|---|
| **Nama** | Angga Anggieanie |
| **NIM** | 250401020172 |
| **Kelas** | IF401 — PJJ Informatika |
| **Mata Kuliah** | Pengantar Data Science (200302305) |

---

## 🗺️ Peta Perjalanan Belajar

```
Pertemuan 1  →  Pertemuan 2  →  Pertemuan 3  →  Pertemuan 4
Python Dasar    EDA & Pandas    Data Cleaning   Statistika

Pertemuan 5  →  Pertemuan 6  →  Pertemuan 7
Visualisasi     Preprocessing   Machine Learning
```

---

## 📚 Ringkasan Per Pertemuan

### Pertemuan 1 — Python Dasar untuk Data Science
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

### Pertemuan 2 — Eksplorasi Data Awal (EDA) dengan Pandas
📄 [`Pertemuan2_ANGGA-ANGGIEANIE_250401020172.ipynb`](Pertemuan2_ANGGA-ANGGIEANIE_250401020172.ipynb)

Dataset: **Titanic** (891 penumpang, 12 kolom) — diakses langsung dari URL.

**Topik yang dipelajari:**
- Memuat dataset CSV dari URL dengan `pd.read_csv()`
- Inspeksi struktur data: `shape`, `columns`, `head()`
- Analisis *missing values* (jumlah & persentase): `Age` 19.9%, `Cabin` 77.1%
- Filtering data: wanita kelas 1 (`Sex == 'female'` & `Pclass == 1`)
- Agregasi dengan `groupby()` dan `mean()`
- Analisis tingkat keselamatan: Kelas 1 (63%) vs Kelas 3 (24%), wanita (74%) vs pria (19%)

**Library:** `pandas` · `numpy`

---

### Pertemuan 3 — Data Cleaning: Missing Values, Outlier & Ekstraksi Data
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

### Pertemuan 4 — Statistika Dasar & Analisis Data
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

### Pertemuan 5 — Visualisasi Data
📄 [`Pertemuan5_Angga_Anggieanie_250401020172.ipynb`](Pertemuan5_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Penguins** (344 baris, 3 spesies penguin di Kepulauan Palmer, Antarktika).

**Topik yang dipelajari:**
- Setup tema global Seaborn (`set_theme`, `whitegrid`, `Set2`)
- Membersihkan data dengan `dropna()` → 333 baris bersih
- **Bar Chart**: rata-rata massa tubuh per spesies (sumbu dari 0 — prinsip akurasi)
- **Scatter Plot**: hubungan panjang paruh vs panjang sirip per spesies
- **Histogram + KDE**: distribusi berat badan per spesies
- **Heatmap Korelasi**: matrix korelasi antar fitur numerik
- Dashboard multi-grafik dengan `GridSpec`

**Library:** `pandas` · `numpy` · `matplotlib` · `seaborn`

---

### Pertemuan 6 — Persiapan Data (End-to-End Preprocessing Pipeline)
📄 [`Pertemuan6_Angga_Anggieanie_250401020172.ipynb`](Pertemuan6_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Titanic** (dataset yang sama dari pertemuan 2, kali ini difokuskan untuk pemodelan ML).

**Topik yang dipelajari:**
- EDA singkat: 177 missing `age` (~20%), 2 missing `embarked`, target `survived` imbalanced (61.6% vs 38.4%)
- **Handling Missing Values**: median untuk `age` (28.0), modus 'S' untuk `embarked`
- **One-Hot Encoding** kolom nominal dengan `pd.get_dummies()` + `drop_first=True` (hindari dummy variable trap)
- **Train-Test Split** stratified 80:20 → 712 train / 179 test (`stratify=y`)
- **Feature Scaling** dengan `StandardScaler`: `fit_transform()` hanya pada train, `transform()` pada test
- Konsep penting: **mencegah data leakage** — split sebelum scaling, test set tidak pernah digunakan untuk fit

**Library:** `pandas` · `numpy` · `seaborn` · `sklearn`

---

### Pertemuan 7 — Pengantar Machine Learning: Regresi Linear
📄 [`Pertemuan7_Angga_Anggieanie_250401020172.ipynb`](Pertemuan7_Angga_Anggieanie_250401020172.ipynb)

Dataset: **Gaji Sintetis** (300 baris, dibuat dengan `np.random.seed(42)` untuk reproducibility).

**Formula dataset:**
```
gaji = 3.0 + 2.2×pengalaman + 1.5×edu + 4.0×(kota=='Jakarta') + noise
```

**Topik yang dipelajari:**
- Membuat dataset sintetis yang realistis dengan `numpy`
- Visualisasi scatter plot hubungan pengalaman vs gaji per kota
- Pipeline prediksi gaji end-to-end dengan **Linear Regression**
- Evaluasi model: MAE, MSE, RMSE, R²
- Interpretasi koefisien model

**Library:** `numpy` · `pandas` · `matplotlib` · `seaborn` · `sklearn`

---

## 🛠️ Stack Teknologi

| Kategori | Tools |
|---|---|
| Bahasa | Python 3 |
| Lingkungan | Google Colab · Jupyter Notebook |
| Data Manipulation | `pandas` · `numpy` |
| Visualisasi | `matplotlib` · `seaborn` |
| Statistik | `scipy` |
| Machine Learning | `scikit-learn` |
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

---

## 📂 Struktur Repository

```
data-science-2026/
│
├── Pertemuan1_ANGGA-ANGGIEANIE_250401020172.ipynb   # Python Dasar
├── Pertemuan2_ANGGA-ANGGIEANIE_250401020172.ipynb   # EDA & Pandas
├── Pertemuan3_angga_anggieanie_250401020172.ipynb   # Data Cleaning
├── Pertemuan4_Angga_Anggieanie_250401020172.ipynb   # Statistika
├── Pertemuan5_Angga_Anggieanie_250401020172.ipynb   # Visualisasi
├── Pertemuan6_Angga_Anggieanie_250401020172.ipynb   # Preprocessing
├── Pertemuan7_Angga_Anggieanie_250401020172.ipynb   # Regresi Linear
├── README.md
└── LICENSE
```

---

*Repository ini merupakan bagian dari tugas praktikum mata kuliah Pengantar Data Science, Program Studi PJJ Informatika, 2026.*

