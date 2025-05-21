# 🕵️‍♀️ Laporan Proyek Machine Learning - Salsabila Mahiroh

---

## 💼 Domain Proyek : Keuangan
Dalam bidang atau sektor keuangan, layanan kredit merupakan salah satu pilar utama yang menopang pertumbuhan ekonomi di dunia tetapi, tingginya angka gagal bayar (non-performing loan) dapat menimbulkan risiko serius bagi stabilitas lembaga keuangan. Oleh karena itu, diperlukan sistem penilaian kelayakan kredit yang akurat untuk meminimalkan risiko tersebut.

Masalah ini harus diselesaikan karena penilaian kredit yang tidak tepat dapat menyebabkan kerugian finansial dan melemahkan kepercayaan terhadap institusi keuangan. Metode konvensional cenderung lambat, subjektif, dan kurang efektif dalam mengolah data dalam jumlah besar.

Sebagai solusi, pendekatan berbasis **machine learning** menawarkan kemampuan untuk memproses data historis secara efisien dan mengidentifikasi pola risiko yang kompleks. Dengan membangun dan membandingkan model prediksi seperti **K-Nearest Neighbor, Random Forest**, dan **XGBoost**, proyek ini bertujuan membantu lembaga keuangan mengambil keputusan pinjaman yang lebih tepat, mengurangi risiko gagal bayar, serta meningkatkan efisiensi dan objektivitas dalam proses seleksi kredit.

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
2. Membangun model dengan menggunakan algoritma KNN, Random Forest, dan XGBoost dan melakukan evaluasi model menggunakan clasification report, confussion matrix, dan ROC-AUC untuk membandingkan keakuratan prediksi setiap model, dan memilih model yang memberikan akurasi tertinggi sebagai model terbaik untuk mempredisksi status pinjaman atau resiko kredit

---

## 📁 Data Understanding
1. **Sumber dataset** : https://www.kaggle.com/datasets/laotse/credit-risk-dataset
2. **Informasi dataset** : Dataset ini merupakan dataset yang digunakan dengan metode klasifikasi biner, dataset ini digunakan untuk menganalisis risiko kredit dengan pendekatan klasifikasi.
3. **Jumlah data** : Terdapat 32.581 data dan memiliki jumlah total 12 kolom, 4 untuk kolom kategori, dan 8 untuk kolom numerik (1 sebagai kolom target)
4. **Kondisi data** :
- Terdapat missing value
- Terdapat data duplikat
- Terdapat outlier pada fitur person_age, person_income, person_emp_length, loan_amnt, loan_int_rate, loan_percent_income, cb_person_cred_hist_length

### 🔗 Variabel pada Credit Risk Dataset adalah sebagai berikut :
- **Kolom Kategori** :
1. **person_age** : Usia calon peminjam
2. **person_income** : Pendapatan tahunan calon peminjam
3. **person_emp_length** : Lama masa kerja calom peminjam (dalam tahun)
4. **loan_amnt** : Jumlah pinjaman
5. **loan_int_rate** : Suku bunga pinjaman
6. **loan_percent_income** : Presentase pinjaman terhadap pendapatan
7. **cb_person_cred_hist_length** : Durasi riwayat kredit
8. **loan_status : Status pnjaman**, 0 = Tidak gagal bayar dan 1 = gagal bayar
- **Kolom Numerik** :
1. **person_home_ownership** : Status kepemilikan tempat tinggal peminjam
2. **loan_intent** : Tujuan pinjaman
3. **loan_grade** : Tingkat pinjaman
4. **cb_person_default_on_file** : Riwayat default atau gagal bayar (YES/NO)
### 📊 Exploratory Data Analysis (EDA)
#### **1. EDA - Deskripsi Variabel**
Pada tahap ini EDA deskripsi variabel ini digunakan untuk, memahami struktur dan karakteristik data (data understanding) yang digunakan untuk mengenali tipe data, mendeteksi nilai yang hilang atau duplikat, melihat adanya outlier, dsb. Tujuannya sebagai dasar dalam pengambilan keputusan untuk analisis selanjutnya.
#### **2. EDA - Univariate Analisis**
- **Fitur Kategorikal** :
Mayoritas peminjam tinggal di tempat sewa (Rent), dengan tujuan pinjaman terbanyak untuk pendidikan (Education). Grade pinjaman paling umum adalah A, dan sebagian besar peminjam tidak memiliki riwayat gagal bayar (kategori N pada cb_person_default_on_file).
- **Fitur Numerik** :
Berdasarkan distribusi fitur numerik, khususnya pada fitur loan_status yang sebagai target, bahwa Mayoritas pinjaman berstatus lancar (0),dan hanya sebagian kecil yang gagal bayar (1). Artinya, sebagian besar peminjam dalam data ini berhasil membayar pinjamannya dengan lancar, sementara hanya sebagian kecil yang mengalami gagal bayar.
#### **3. EDA - Multivariate Analisis**
- **Fitur Kategorikal** :
Fitur kategori seperti person_home_ownership, loan_intent, loan_grade, dan cb_person_default_on_file memiliki pengaruh signifikan terhadap loan_status. Risiko gagal bayar lebih tinggi pada kategori tertentu seperti sewa rumah, tujuan pinjaman untuk medis/debt consolidation, serta pada peminjam dengan grade rendah atau riwayat default sebelumnya. Hal ini menunjukkan bahwa fitur-fitur kategori berperan penting dalam menentukan status kelayakan pinjaman.
- **Fitur Numerik** :
**Visualisasi dengan Pairplot** : Berdasarkan visualisasi pairplot terlihat bahwa fitur loan_percent_income, loan_int_rate, dan person_income memiliki korelasi terhadap fitur loan_status. Sedangkan fitur lainnya memiliki korelasi yang lemah karena sebarannya tidak membentuk pola
**Visualisasi dengan headmap** : 
Fitur numerik dengan korelasi tertinggi terhadap loan_status adalah loan_percent_income, loan_int_rate, dan person_income. Sementara fitur lain seperti person_age, person_emp_length, dan cb_person_cred_hist_length memiliki korelasi sangat lemah atau hampir tidak ada, sehingga akan dipertimbangkan untuk dihapus pada tahap Data Preparation.

---

## 🧮 Data Preparation
1. Menghapus kolom yang tidak memiliki korelasi dengan loan_status. Proses ini dilakukan untuk mengurangi kompleksitas data dan meningkatkan performa model, agar hanya fitur yang relevan saja yang digunakan dalam proses pelatihan.
2. Menangani missing value dengan metode imputasi. Proses ini digunakan untuk mengisi nilai kosong pada data, agar model dapat memproses semua data tanpa terganggu oleh nilai yang hilang.
3. Menangani data duplikat. Proses ini digunakan untuk menghapus entri data yang sama secara identik, agar analisis dan pelatihan model tidak bias karena pengaruh data yang berulang.
4. Menangani outlier dengan metode IQR. Proses ini digunakan untuk mengidentifikasi dan mengatasi data ekstrem di luar rentang normal, agar model tidak terdistorsi oleh nilai-nilai yang menyimpang jauh dari pola umum data.
5. Mengubah fitur kategorikal menjadi variabel numerik melalui One-Hot Encoding. Proses ini digunakan untuk mengonversi data kategorikal menjadi bentuk numerik yang bisa dipahami oleh algoritma machine learning, agar semua fitur dapat digunakan dalam pelatihan model tanpa kehilangan makna kategorinya.
6. Membagi data menjadi data latih dan data uji menggunakan train_test_split dengan porsi 80%:20%. Proses ini digunakan untuk memisahkan data yang digunakan untuk melatih model dan mengevaluasinya, agar model dapat diuji performanya pada data yang belum pernah dilihat sebelumnya.
7. Menormalisasi fitur numerik dengan StandardScaler. Proses ini digunakan untuk mengubah skala data numerik agar memiliki distribusi yang seragam (mean 0 dan standar deviasi 1), agar algoritma machine learning dapat belajar lebih efektif dan cepat, terutama untuk model yang sensitif terhadap skala fitur seperti SVM atau KNN.

---

## 💹 Modeling
1. **K-Nearest Neighbor** : Model K-Nearest Neighbors dibangun menggunakan KNeighborsClassifier dari library scikit-learn dengan parameter n_neighbors=5, yang berarti model akan mempertimbangkan 5 tetangga terdekat untuk menentukan kelas dari sebuah data baru. Model ini kemudian dilatih (fit) menggunakan data pelatihan X_train dan y_train.
- **kelebihan** : Mudah dipahami dan diimplementasikan, tidak memerlukan proses pelatihan.
- **kekurangan** : Lambat saat prediksi pada dataset besar karena harus menghitung jarak ke semua data latih.
2. **Random Forest** : Model Random Forest dibangun menggunakan RandomForestClassifier dari scikit-learn. Dengan parameter n_estimators=100, berarti model menggunakan 100 pohon keputusan (decision trees). Parameter random_state=42 digunakan agar hasil model bersifat reproducible (konsisten setiap kali dijalankan). Model ini kemudian dilatih menggunakan data pelatihan X_train dan y_train.
- **kelebihan** : Akurat dan tahan terhadap overfitting karena menggabungkan banyak pohon keputusan.
- **kekurangan** : Model relatif sulit diinterpretasikan karena merupakan kumpulan banyak pohon (black box).
3. **XGBoost** : Model XGBoost dibangun menggunakan XGBClassifier dengan parameter use_label_encoder=False, dan eval_metric='logloss' sebagai metrik evaluasi. Parameter random_state=42 digunakan untuk menjaga konsistensi hasil. Model ini kemudian dilatih menggunakan data pelatihan X_train dan y_train.
- **kelebihan** : Performa sangat tinggi dalam prediksi dan efisien untuk dataset besar.
- **kekurangan** : Lebih kompleks dan memerlukan waktu untuk tuning hyperparameter agar hasil optimal.

---

## 📋 Evaluasi
### 📈 Metrik Evaluasi 
Pada proyek ini, clasification report, confussion matrix, dan ROC-AUC digunakan sebagai metrik evaluasi untuk mengukur seberapa akurat model dalam memprediksi status peminjaman atau resiko kredit berdasarkan riwayat calon peminjam.

Penjelasan metrik evaluasi yang digunakan :
1. **Classification Report** :
- Precision : metrik evaluasi yang mengukur seberapa baik model membuat prediksi yang benar untuk kelas positif dari total prediksi positif yang dilakukan.
- Recall : metrik evaluasi yang menggambarkan seberapa baik suatu model dalam mengidentifikasi kelas positif dengan benar.
- f1-Score : metrik evaluasi yang mencerminkan keseimbangan antara Presisi (Precision) dan Sensitivitas (Recall)
2. **Confussion matrix** : alat yang digunakan untuk menggambarkan kinerja model klasifikasi pada data uji yang sudah diketahui hasil sebenarnya.
3. **ROC-AUC** : metrik evaluasi yang digunakan untuk mengukur kinerja model klasifikasi, terutama dalam konteks biner (dua kelas). Metrik ini fokus pada kemampuan model untuk membedakan antara kelas positif dan negatif dengan memperhatikan trade-off antara tingkat True Positive Rate (TPR) dan tingkat False Positive Rate (FPR).
### 💡 Hasil Evaluasi Berdasarkan Metrik Evaluasi

| Model              | Accuracy | F1 Score | ROC-AUC |
| ------------------ | -------- | -------- | ------- |
| K-Nearest Neighbor | 0.893    | 0.715    | 0.871   |
| Random Forest      | 0.915    | 0.773    | 0.915   |
| XGBoost            | 0.920    | 0.787    | 0.941   |

1. **K-Nearest Neighbor (KNN):**
- Akurasi cukup tinggi, namun bukan yang terbaik karena lebih rendah dari random forest dan XGBoost.
- F1 Score relatif rendah, mengindikasikan bahwa model kurang optimal dalam menangani ketidakseimbangan antara precision dan recall—khususnya untuk memprediksi nasabah gagal bayar.
- ROC-AUC juga merupakan yang paling rendah dari ketiga model, menunjukkan bahwa kemampuan diskriminatifnya terhadap dua kelas (gagal vs tidak gagal bayar) masih kurang.
2. **Random Forest:**
- Akurasi meningkat menunjukan model cukup baik
- F1 Score lebih baik dibanding KNN, menunjukkan keseimbangan yang lebih baik dalam mengklasifikasikan kelas minoritas (nasabah gagal bayar).
- ROC-AUC juga tinggi, menandakan performa baik dalam membedakan kedua kelas.
3. **XGBoost:**
- Memiliki performa terbaik di semua metrik evluasi
- F1 Score tertinggi, menunjukkan Keseimbangan precision & recall sangat baik
- ROC-AUC tertinggi, menunjukan sangat baik dalam membedakan nasabah gagal bayar dan tidak
### 💡 Hasil Evaluasi Berdasarkan Data Aktual 
1. **K-Nearest Neighbor (KNN)**: 1
2. **Random Forest (RF)**: 1
3. **XGBoost (Boosting)**: 1

Dalam hal ini, ketiga model dapat memprediksi dengan benar bahwa pelanggan dalam sampel ini adalah gagal membayar pinjaman.

---

Secara keseluruhan, **XGBoost** adalah algoritma yang dapat dipilih untuk melakukan suatu prediksi karena, memiliki akurasi yang tinggi yang dapat memberikan hasil yang paling akurat.

---

## 📑 Referensi

