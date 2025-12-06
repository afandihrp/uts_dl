Customer Segmentation using K-Means Clustering
🎯 Tujuan Proyek

Proyek ini bertujuan untuk melakukan segmentasi pelanggan (Customer Segmentation) menggunakan algoritma K-Means clustering pada data perilaku kredit. Tujuannya adalah mengidentifikasi kelompok pelanggan yang homogen (serupa) untuk strategi pemasaran atau manajemen risiko yang lebih terfokus.

💾 Dataset

    Nama File: clusteringmidterm.csv

    Ukuran Data: 8950 entri dengan 18 kolom fitur (termasuk ID pelanggan).

    Fitur Kunci: Berbagai metrik perilaku kartu kredit seperti BALANCE, PURCHASES, CASH_ADVANCE, CREDIT_LIMIT, PAYMENTS, dan frekuensi transaksi terkait.

⚙️ Metodologi dan Pre-processing

Proses ini mengikuti langkah-langkah standar untuk analisis clustering berbasis jarak:

    Penanganan Nilai Hilang (Missing Values)

        Kolom CREDIT_LIMIT dan MINIMUM_PAYMENTS memiliki nilai yang hilang.

        Nilai yang hilang diimputasi (diisi) menggunakan median dari masing-masing kolom, menjamin data lengkap untuk analisis.

    Penskalaan Fitur (Feature Scaling)

        Semua fitur numerik (kecuali CUST_ID) distandardisasi menggunakan StandardScaler.

        Standarisasi (Z-score normalization) memastikan bahwa semua fitur berkontribusi sama dalam perhitungan jarak oleh K-Means, mencegah fitur dengan skala besar mendominasi hasil.

    Reduksi Dimensi (PCA)

        Principal Component Analysis (PCA) diterapkan pada data yang sudah diskalakan.

        Dimensi data dikurangi menjadi 2 Principal Components (PC1 dan PC2).

        Kedua komponen ini secara kolektif menjelaskan sekitar 47.6% dari total varians data asli (PC1≈27.3% dan PC2≈20.3%). Reduksi ini penting untuk visualisasi dan efisiensi clustering.

🧠 K-Means Clustering
Penentuan Jumlah Cluster (K)

    Metode: Elbow Method (Siku) digunakan dengan memplot WCSS (Within-Cluster Sum of Squares) terhadap jumlah cluster (K).

    Optimal K: Berdasarkan plot yang dihasilkan, titik 'siku' (elbow point) yang menunjukkan berkurangnya diminishing returns ditemukan pada K = 4.

Pelatihan Model

    Model K-Means dilatih menggunakan data yang telah direduksi dimensinya (df_pca) dengan 4 clusters.

    Setiap pelanggan diberi label cluster (cluster_label) dari 0 hingga 3.

📊 Visualisasi Hasil

Hasil clustering divisualisasikan dalam plot 2D menggunakan PC1 dan PC2.

    Plot menunjukkan 4 kelompok pelanggan yang berbeda yang tersebar di sepanjang dua komponen utama, mengindikasikan adanya segmentasi yang cukup jelas.