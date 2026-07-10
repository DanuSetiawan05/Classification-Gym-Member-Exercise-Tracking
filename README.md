# Gym Member Experience Level Classification

Klasifikasi tingkat pengalaman (Experience Level) anggota gym berdasarkan data aktivitas dan fisik menggunakan algoritma **Decision Tree Classifier**.

## 📌 Latar Belakang

Gym dan pusat kebugaran modern semakin banyak memanfaatkan data untuk memahami perilaku dan kebutuhan anggotanya. Salah satu informasi yang berguna adalah **tingkat pengalaman (Experience Level)** anggota — apakah mereka pemula, menengah, atau mahir — karena informasi ini dapat digunakan untuk personalisasi program latihan, rekomendasi kelas, hingga strategi retensi member.

Namun, tidak semua member secara eksplisit mencantumkan tingkat pengalamannya. Proyek ini bertujuan membangun model klasifikasi yang dapat memprediksi Experience Level berdasarkan data yang lebih mudah didapat, seperti kebiasaan latihan dan atribut fisik.

## 🎯 Rumusan Masalah

1. Faktor apa saja — baik atribut fisik (usia, berat badan, tinggi badan, BPM, dll.) maupun kebiasaan latihan (durasi, frekuensi) — yang paling berpengaruh dalam menentukan Experience Level seorang gym member?
2. Seberapa akurat model Decision Tree dapat mengklasifikasikan Experience Level berdasarkan faktor-faktor tersebut?

## 🎯 Tujuan Project

- Membangun model klasifikasi Experience Level menggunakan Decision Tree.
- Mengidentifikasi fitur yang paling berkontribusi terhadap prediksi (feature importance).
- Mengevaluasi performa model secara valid menggunakan data uji yang benar-benar terpisah dari data latih, dibandingkan dengan baseline model.

## 💡 Manfaat

**Untuk Bisnis/Gym:**
- Membantu pengelola gym melakukan **segmentasi member otomatis** tanpa perlu member mengisi survei tingkat pengalaman secara manual.
- Mendukung **personalisasi program latihan** — member pemula dan mahir bisa diarahkan ke jenis program/kelas yang lebih sesuai.
- Menjadi dasar untuk **strategi retensi**, misalnya menargetkan member pemula dengan konten edukasi tambahan agar lebih konsisten berlatih.

**Untuk Individu/Trainer:**
- Personal trainer dapat memahami lebih cepat profil member baru berdasarkan pola aktivitas awal mereka, tanpa menunggu asesmen manual yang panjang.

## 📊 Dataset

Dataset berisi data aktivitas dan atribut fisik anggota gym, dengan kolom antara lain: `Age`, `Gender`, `Weight`, `Height`, `Max_BPM`, `Avg_BPM`, `Resting_BPM`, `Session_Duration`, `Calories_Burned`, `Workout_Type`, `Fat_Percentage`, `Water_Intake`, `Workout_Frequency`, `BMI`, dan target `Experience_Level` (1 = Pemula, 2 = Menengah, 3 = Mahir).

## 🔬 Metodologi

Project ini mengikuti tahapan metodologi data science secara berurutan:

1. **Problem Statement** — perumusan masalah dan tujuan analisis
2. **Data Understanding** — eksplorasi struktur data, pengecekan missing value & duplikat, distribusi target
3. **Data Preparation** — pembersihan data (missing value, duplikat), penghapusan outlier menggunakan Z-score, encoding fitur kategorikal
4. **Exploratory Data Analysis (EDA)** — correlation heatmap dan visualisasi hubungan antar fitur terhadap target, dilakukan sebelum modeling
5. **Data Splitting** — pembagian data latih (80%) dan data uji (20%)
6. **Modeling** — baseline model sebagai pembanding, serta pemilihan `max_depth` optimal melalui 5-fold cross-validation
7. **Evaluation** — evaluasi performa menggunakan data uji yang terpisah dari data latih, confusion matrix, classification report, dan cross-validation
8. **Feature Importance & Interpretasi** — analisis fitur yang paling berpengaruh terhadap hasil prediksi
9. **Kesimpulan & Rekomendasi**

## 📈 Hasil Utama

| Metrik | Nilai |
|---|---|
| Baseline Accuracy (prediksi kelas mayoritas) | 41.2% |
| max_depth optimal (hasil cross-validation) | 4 |
| Akurasi Data Train | 89.3% |
| Akurasi Data Test | 93.8% |
| Cross-Validation Accuracy (5-fold) | 89.1% ± 3.4% |

**Insight utama:** Feature importance menunjukkan bahwa **`Session_Duration` (durasi latihan)** dan **`Workout_Frequency` (frekuensi latihan)** adalah dua faktor yang paling dominan dalam menentukan Experience Level, sementara atribut fisik/demografis seperti usia, berat badan, tinggi badan, dan BPM memiliki kontribusi yang sangat kecil. Artinya, **kebiasaan latihan lebih menentukan tingkat pengalaman dibanding karakteristik fisik bawaan seseorang.**

## 🛠️ Tools & Library

- Python
- Pandas, NumPy — manipulasi data
- Matplotlib, Seaborn — visualisasi data
- Scikit-learn — modeling, evaluasi, dan cross-validation
- Joblib — menyimpan model

## 📂 Struktur Project

```
├── Gym_Member_Exercise_Tracking.ipynb   # Notebook analisis lengkap
├── gym_members_exercise_tracking.csv    # Dataset mentah
├── data_bersih.csv                      # Dataset hasil cleaning
└── decision_tree_model.pkl              # Model hasil training (siap deploy)
```

## 🚀 Cara Menjalankan

```bash
# 1. Clone repository
git clone https://github.com/DanuSetiawan05/Classification-Gym-Member-Exercise-Tracking.git
cd Classification-Gym-Member-Exercise-Tracking

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn joblib

# 3. Jalankan notebook
jupyter notebook Gym_Member_Exercise_Tracking.ipynb
```

## 🔮 Pengembangan Selanjutnya

- Membandingkan performa dengan algoritma lain seperti Random Forest atau KNN untuk memvalidasi konsistensi feature importance.
- Menambahkan penanganan class imbalance (misalnya `class_weight='balanced'`) karena kelas "mahir" memiliki jumlah data lebih sedikit.
- Menambahkan fitur turunan (misalnya progres latihan dari waktu ke waktu) untuk menguji apakah atribut fisik dapat lebih berkontribusi jika direpresentasikan secara berbeda.

## 👤 Author

**Muhammad Danu Setiawan**
[LinkedIn](https://www.linkedin.com/in/muhammaddanusetiawan/) · [GitHub](https://github.com/DanuSetiawan05)
