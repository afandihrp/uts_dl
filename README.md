1. 🎶 Proyek Regresi: Prediksi Tahun Rilis Musik

Proyek ini bertujuan untuk memprediksi tahun rilis lagu berdasarkan 90 fitur akustik.
Temuan Utama dan Kinerja Model

Hasil evaluasi menunjukkan bahwa Model Regresi Linier Sederhana jauh lebih unggul daripada Model Neural Network Dense Kecil. Model Linier mencapai RMSE (Root Mean Squared Error) sebesar 9.4248 dan MAE (Mean Absolute Error) sebesar 6.7161. Ini berarti, rata-rata prediksi tahun rilis meleset sekitar 6 hingga 7 tahun.

Sebaliknya, Model Dense Kecil berkinerja sangat buruk, dengan RMSE 18.3383 dan MAE 12.8039, serta menghasilkan nilai R2 yang negatif. R2 negatif menunjukkan bahwa model kompleks tersebut bahkan lebih buruk dalam memprediksi target dibandingkan jika hanya menggunakan nilai rata-rata dari seluruh data.
Pembelajaran

Hal ini menunjukkan bahwa kompleksitas data target tidak selalu memerlukan kompleksitas model. Untuk dataset ini, hubungan antara fitur dan tahun rilis kemungkinan besar bersifat linier, sehingga model Linier Sederhana sudah memadai dan lebih efektif secara komputasi. Model Linier Sederhana terpilih sebagai model final karena memberikan akurasi terbaik dan terbukti stabil.

2. 💳 Proyek Klasifikasi: Deteksi Fraud Transaksi

Proyek kedua berfokus pada masalah klasifikasi biner yang sangat tidak seimbang (imbalanced)—mendeteksi transaksi fraud dari yang normal.
Temuan Utama dan Kinerja Model

Anda menggunakan Model Neural Network (MLP) yang sederhana (dua hidden layer) dan hanya mengandalkan 379 fitur numerik.

Untuk mengatasi ketidakseimbangan kelas yang parah, strategi Class Weights diterapkan selama pelatihan. Bobot kelas Fraud (1) diberi nilai jauh lebih tinggi (≈14.29) daripada bobot kelas Non-Fraud (0) (≈0.518).

Hasil evaluasi pada test set menunjukkan bahwa model berhasil mencapai skor ROC AUC sebesar 0.8840.
Pembelajaran

Nilai ROC AUC sebesar 0.8840 adalah indikator yang baik untuk kemampuan diskriminatif model dalam membedakan kedua kelas, terutama dalam skenario imbalanced seperti deteksi fraud. Keberhasilan ini menegaskan bahwa penggunaan strategi penanganan class imbalance yang tepat (seperti Class Weights) sangat krusial agar model dapat belajar dari kelas minoritas tanpa bias terhadap kelas mayoritas.