# 🕵️‍♀️ Laporan Proyek Machine Learning - Salsabila Mahiroh

---

## 💼 Domain Proyek
  bb

---

## 🔍 Business Understanding
### 👩🏽‍🔧 Problem Statement
1. Fitur apa saja yang paling berpengaruh terhadap status pinjaman (loan_status)?
2. Bagaimana memilih model prediksi yang paling akurat untuk memprediksi apakah seseorang mengalami gagal bayar atau tidak dengan menggunakan beberapa model seperti KNN, Random Forest, dan XGBoost?
### 👩🏽‍🏫 Goals
1. Melakukan proses Exploratory Data Analysis (EDA) untuk mengetahui fitur atau variabel yang paling berkorelasi terhadap loan_status
2. Melakukan analisis dan membandingkan performa beberapa model prediksi seperti KNN, Random Forest, dan XGBoost untuk memilih model dengan kinerja terbaik dalam memprediksi status pinjaman berdasarkan riwayat calon peminjam.
### 👩🏽‍💻 Solution Statements
1. Melakukan proses Exploratory Data Analysis (EDA) terhadap dataset pinjaman dengan langkah-langkah seperti memahami anatar variabel, visualisasi distribusi fitur, analisis korelasi antar variabel, serta penggunaan teknik statistik dan grafik (seperti heatmap korelasi, boxplot, dan pairplot). Analisis ini bertujuan untuk mengidentifikasi fitur-fitur yang memiliki hubungan yang signifikan terhadap loan_status, sehingga dapat memberikan wawasan awal sebelum dilakukan pemodelan atau pengambilan keputusan lebih lanjut.
2. Melakukan evaluasi model menggunakan clasification report, confussion matrix, dan ROC-AUC untuk membandingkan keakuratan prediksi setiap model, dan memilih model yang memberikan akurasi tertinggi sebagai model terbaik untuk mempredisksi status pinjaman atau resiko kredit

---

## 📁 Data Understanding
1. Sumber data :
2. Jumlah data :
3. Kondisi data :
- Terdapat missing value
- Terdapat data duplikat
- Terdapat outlier pada fitur person_age, person_income, person_emp_length, loan_amnt, loan_int_rate, loan_percent_income, cb_person_cred_hist_length

### 🔗 Variabel pada Credit Risk Dataset adalah sebagai berikut :
1. person_age : Usia calon peminjam
2. person_income : Pendapatan tahunan calon peminjam
3. person_home_ownership : Status kepemilikan tempat tinggal peminjam
4. person_emp_length : Lama masa kerja calom peminjam (dalam tahun)
5. loan_intent : Tujuan pinjaman
6. loan_grade : Tingkat pinjaman
7. loan_amnt : Jumlah pinjaman
8. loan_int_rate : Suku bunga pinjaman
9. loan_percent_income
10. cb_person_default_on_file : Riwayat default atau gagal bayar (YES/NO)
11. cb_person_cred_hist_length : Durasi riwayat kredit
12. loan_status : Status pnjaman, 0 = Tidak gagal bayar dan 1 = gagal bayar

### 📊 Exploratory Data Analysis (EDA)
#### **1. EDA - Deskripsi Variabel**
#### **2. EDA - Univariate Analisis**
- Fitur Kategorikal 
- Fitur Numerik
#### **3. EDA - Multivariate Analisis**
- Fitur Kategori
- Fitur Numerik

---

## 🧮 Data Preparation
1. Menghapus kolom yang tidak memiliki korelasi dengan loan_status 
2. Menangani missing value dengan metode imputasi
3. Menangani data duplikat
4. Menangani outlier dengan metode IQR
5. Fitur kategorikal diubah menjadi variabel numerik melalui one-hot encoding.
6. Data dibagi menjadi data latih dan data uji menggunakan train_test_split dengan porsi 80% untuk data latih dan 20% untuk data uji
7. Fitur numerik di normalisasi dengan StandardScaler

---

## 💹 Modeling
1. K-Nearest Neighbor : Model K-Nearest Neighbors dibangun menggunakan KNeighborsClassifier dari library scikit-learn dengan parameter n_neighbors=5, yang berarti model akan mempertimbangkan 5 tetangga terdekat untuk menentukan kelas dari sebuah data baru. Model ini kemudian dilatih (fit) menggunakan data pelatihan X_train dan y_train.
2. Random Forest : Model Random Forest dibangun menggunakan RandomForestClassifier dari scikit-learn. Dengan parameter n_estimators=100, berarti model menggunakan 100 pohon keputusan (decision trees). Parameter random_state=42 digunakan agar hasil model bersifat reproducible (konsisten setiap kali dijalankan). Model ini kemudian dilatih menggunakan data pelatihan X_train dan y_train.
3. XGBoost : Model XGBoost dibangun menggunakan XGBClassifier dengan parameter use_label_encoder=False, dan eval_metric='logloss' sebagai metrik evaluasi. Parameter random_state=42 digunakan untuk menjaga konsistensi hasil. Model ini kemudian dilatih menggunakan data pelatihan X_train dan y_train.

---

## 📋 Evaluasi
### 📈 Metrik Evaluasi 
Pada proyek ini, clasification report, confussion matrix, dan ROC-AUC digunakan sebagai metrik evaluasi untuk mengukur seberapa akurat model dalam memprediksi status peminjaman atau resiko kredit berdasarkan riwayat calon peminjam.

Penjelasan metrik evaluasi yang digunakan :
1. Classification Report :
- Precision : metrik evaluasi yang mengukur seberapa baik model membuat prediksi yang benar untuk kelas positif dari total prediksi positif yang dilakukan.
- Recall : metrik evaluasi yang menggambarkan seberapa baik suatu model dalam mengidentifikasi kelas positif dengan benar.
- f1-Score : metrik evaluasi yang mencerminkan keseimbangan antara Presisi (Precision) dan Sensitivitas (Recall)
2. Confussion matrix : alat yang digunakan untuk menggambarkan kinerja model klasifikasi pada data uji yang sudah diketahui hasil sebenarnya.
3. ROC-AUC : metrik evaluasi yang digunakan untuk mengukur kinerja model klasifikasi, terutama dalam konteks biner (dua kelas). Metrik ini fokus pada kemampuan model untuk membedakan antara kelas positif dan negatif dengan memperhatikan trade-off antara tingkat True Positive Rate (TPR) dan tingkat False Positive Rate (FPR).

### 💡 Hasil Evaluasi Berdasarkan Metrik Evaluasi

| Model              | Accuracy | F1 Score | ROC-AUC |
| ------------------ | -------- | -------- | ------- |
| K-Nearest Neighbor | 0.893    | 0.715    | 0.871   |
| Random Forest      | 0.915    | 0.773    | 0.915   |
| XGBoost            | 0.920    | 0.787    | 0.941   |

### 💡 Hasil Evaluasi Berdasarkan Data Aktual 
1. K-Nearest Neighbor (KNN): 1
2. Random Forest (RF): 1
3. XGBoost (Boosting): 1
Dalam hal ini, ketiga model dapat memprediksi dengan benar bahwa pelanggan dalam sampel ini adalah gagal membayar pinjaman.

---

Secara keseluruhan, XGBoost adalah algoritma yang dapat dipilih untuk melakukan suatu prediksi karena, dapat memberikan hasil yang paling akurat.