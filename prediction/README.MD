💳 Deteksi Fraud Transaksi Menggunakan Neural Network
🚀 Ringkasan Proyek

Proyek ini bertujuan untuk membangun dan melatih model Neural Network (Jaringan Saraf Tiruan) sederhana menggunakan TensorFlow/Keras untuk mengidentifikasi transaksi yang berpotensi fraud (penipuan) dari data transaksi historis. Karena data transaksi fraud sangat tidak seimbang, proyek ini secara khusus menerapkan pembobotan kelas (class weighting) untuk mencegah model bias.

Setelah pelatihan, model dievaluasi menggunakan metrik Area Under the ROC Curve (AUC) pada data uji, dan kemudian digunakan untuk memprediksi label fraud pada set data baru (test_transaction.csv).
🛠️ Metode dan Implementasi
1. Pra-pemrosesan Data (Pre-processing)

    Pemilihan Fitur: Hanya fitur dengan tipe data numerik yang dipertahankan. Fitur non-numerik (kategorikal) tidak digunakan dalam model ini.

    Penanganan Nilai Hilang (Missing Values): Nilai yang hilang (NaN) pada fitur numerik diatasi menggunakan imputasi median (SimpleImputer(strategy="median")).

    Normalisasi Fitur: Semua fitur dinormalisasi menggunakan StandardScaler agar seluruh data berada pada skala yang seragam, sebuah langkah penting untuk melatih Neural Network secara efektif.

    Pembagian Data: Data dibagi menjadi set pelatihan (X_train, y_train) dan set pengujian (X_test, y_test) dengan rasio 80:20 dan menggunakan stratify=y untuk menjaga proporsi kelas.

2. Penanganan Ketidakseimbangan Kelas (Class Imbalance)

    Target variabel (isFraud) menunjukkan ketidakseimbangan kelas yang parah (jumlah transaksi fraud jauh lebih sedikit daripada non-fraud).

    Untuk mengatasinya, bobot kelas (class weights) dihitung menggunakan compute_class_weight(class_weight="balanced"). Bobot ini digunakan selama proses pelatihan (model.fit) untuk memberikan penalti yang lebih besar kepada kesalahan prediksi pada kelas minoritas (fraud), sehingga model menjadi tidak bias.

        Bobot Kelas yang Dihitung: {0: 0.518, 1: 14.29} (Angka 14.29 menunjukkan bahwa kelas fraud (1) diberi bobot sekitar 14 kali lipat dari kelas non-fraud (0)).

3. Arsitektur dan Pelatihan Model

    Model: Neural Network Sequential sederhana. * Lapisan: Tiga lapisan Dense:

        Lapisan Tersembunyi (Hidden Layer): 64 neuron dengan aktivasi ReLU.

        Lapisan Tersembunyi (Hidden Layer): 32 neuron dengan aktivasi ReLU.

        Lapisan Output: 1 neuron dengan aktivasi Sigmoid (untuk output probabilitas antara 0 dan 1).

    Kompilasi: Menggunakan Adam optimizer dan binary cross-entropy loss (cocok untuk klasifikasi biner). Metrik evaluasi utama adalah AUC.

    Pelatihan: Model dilatih selama 5 epoch dengan batch_size=2048 dan diterapkan class weights.

4. Hasil dan Evaluasi

    Test ROC AUC: Setelah 5 epoch, model mencapai skor ROC AUC sebesar 0.8840 pada data pengujian.

    Kurva ROC: Kurva ROC (roc_curve.png) menunjukkan kinerja model dalam membedakan antara kelas positif dan negatif.

🎯 Prediksi

    Model yang telah dilatih (best_fraud_model.h5), bersama dengan objek pra-pemrosesan yang disimpan (imputer.pkl, scaler.pkl), dimuat kembali.

    Data test_transaction.csv dipra-proses dengan cara yang sama (imputasi, scaling, penyesuaian kolom fitur).

    Model menghasilkan probabilitas fraud, yang kemudian dikonversi menjadi label biner (0 atau 1) menggunakan ambang batas (threshold) 0.5.

    Hasil akhir prediksi disimpan dalam file submission.csv dengan kolom TransactionID dan isFraud.