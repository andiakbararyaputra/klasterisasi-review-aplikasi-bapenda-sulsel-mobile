# Klastering Topik Ulasan Pengguna Aplikasi Bapenda Sulsel Mobile Menggunakan Metode K-Means dan Optimasi Particle Swarm Optimization (PSO)

Repositori ini berisi notebook dan dataset untuk melakukan klastering topik pada ulasan pengguna aplikasi **Bapenda Sulsel Mobile** menggunakan **K-Means** yang inisialisasi pusat klasternya dioptimasi dengan **Particle Swarm Optimization (PSO)**.

## Struktur File

| File | Keterangan |
| --- | --- |
| `Klastering_Topik_Ulasan_Bapenda_Sulsel_Mobile_KMeans_PSO.ipynb` | Notebook utama (preprocessing, TF-IDF, LSA, K-Means, PSO, evaluasi, pelabelan topik) |
| `seluruh_review_Bapenda_Sulsel_Mobile.xlsx` | Data mentah ulasan (sheet `Review`) |
| `dataset_review_clean_final.xlsx` | Data ulasan hasil pembersihan (sheet `Sheet1`, kolom `review_clean_final`) |
| `hasil_pelabelan_topik_pso_kmeans.csv` / `.xlsx` | Hasil akhir pelabelan topik per ulasan |

## Alur Metode

1. Pemuatan dan validasi data (hapus data kosong dan duplikat).
2. Normalisasi teks (case folding, pembersihan simbol/URL, normalisasi kata tidak baku, stopword bahasa Indonesia).
3. Pembobotan **TF-IDF** (unigram + bigram) dan normalisasi L2.
4. Reduksi dimensi dengan **LSA (TruncatedSVD)**.
5. Klastering **K-Means** sebagai baseline.
6. Optimasi pusat klaster dengan **PSO** (30 partikel, 40 iterasi, w=0.72, c1=c2=1.49).
7. Evaluasi: **Silhouette Score**, **Davies-Bouldin Index**, **Calinski-Harabasz Index**.
8. Pelabelan topik berdasarkan kata kunci dominan tiap klaster.

## Menjalankan

```bash
pip install numpy pandas matplotlib scikit-learn openpyxl
jupyter notebook Klastering_Topik_Ulasan_Bapenda_Sulsel_Mobile_KMeans_PSO.ipynb
```

Jalankan seluruh sel notebook secara berurutan dari atas ke bawah. Pastikan file dataset berada pada folder yang sama dengan notebook.

## Reproduksibilitas

`RANDOM_STATE = 42` digunakan pada seluruh proses acak, dan eksperimen diulang pada 10 seed (`0-9`) untuk memastikan hasil stabil.

