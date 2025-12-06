📝 Tujuan Proyek

Proyek ini bertujuan untuk membangun dan mengevaluasi model regresi pembelajaran mendalam menggunakan TensorFlow/Keras untuk memprediksi tahun rilis (kolom target) dari dataset midterm-regresi-dataset.csv berdasarkan 90 fitur akustik dan kontekstual lainnya.

🚀 Ringkasan Metodologi

    Pemuatan Data: Dataset dimuat tanpa header di mana kolom pertama (Tahun Rilis) ditetapkan sebagai variabel target (y) dan 90 kolom sisanya sebagai fitur (X).

    Pra-pemrosesan Data:

        Nilai NaN dan inf diisi menggunakan median (SimpleImputer).

        Outlier ditangani dengan metode IQR clipping (1.5 IQR).

        Data dibagi menjadi Train (80%) dan Test (20%).

        Fitur diskalakan menggunakan StandardScaler (Standarisasi: μ=0,σ=1).

    Pengembangan Model: Dua model regresi dibangun dan dilatih menggunakan Mean Squared Error (MSE) sebagai fungsi loss:

        Model Linier Sederhana: Model Dense dengan 1 layer keluaran.

        Model Dense Kecil: Multi-Layer Perceptron (MLP) sederhana dengan dua layer tersembunyi (64 dan 16 neuron, aktivasi ReLU) dan satu layer keluaran.

    Pelatihan dan Pencegahan Overfitting: Kedua model dilatih dengan Early Stopping yang memantau validation loss dengan patience (kesabaran) sebanyak 8 epoch.

📊 Hasil dan Evaluasi Model
Model	MSE (Mean Squared Error)	RMSE (Root Mean Squared Error)	MAE (Mean Absolute Error)	R² (Coefficient of Determination)
Model Linier	88.8267	9.4248	6.7161	0.2537
Model Dense Kecil	336.2930	18.3383	12.8039	-1.8256