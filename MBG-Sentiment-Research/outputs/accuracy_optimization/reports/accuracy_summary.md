# Optimasi Berbasis Accuracy MBG

Kriteria CV dan validasi pada eksperimen ini adalah accuracy. Macro F1 dan recall positif tetap dilaporkan. Sasaran >70% diperiksa secara terpisah pada validasi dan test lama yang bersifat eksploratif.

| Model | Varian | Accuracy validasi | Accuracy test eksploratif | Macro F1 test | Recall positif test |
|---|---|---:|---:|---:|---:|
| SVM | Accuracy Randomized | 80.74% | 82.69% | 0.6848 | 30.00% |
| KNN | Accuracy SVD | 70.01% | 70.74% | 0.6092 | 32.50% |
| Naive Bayes | Accuracy Randomized | 67.26% | 67.72% | 0.5511 | 20.00% |

Seluruh model >70% pada validasi: **False**. Seluruh model >70% pada audit test lama: **False**.

Tidak ada jaminan bahwa target dapat dicapai untuk semua algoritma hanya dengan tuning. Skor test ini bukan evaluasi independen baru karena sampelnya sudah dilihat sebelumnya; data eksternal yang belum pernah digunakan diperlukan untuk konfirmasi. Validasi juga telah dipakai berulang sehingga dapat optimistis.

KNN dengan proyeksi SVD–LDA memakai ekstraktor fitur terawasi tambahan, dan harus diberi nama varian yang tepat. Seleksi chi-square dan proyeksi tersebut dipelajari hanya di fold training. Tiga classifier akhir tetap LinearSVC, KNeighborsClassifier, dan MultinomialNB.

Accuracy tinggi dapat bersamaan dengan recall positif rendah karena kelas positif minoritas. Untuk penelitian sentimen tiga kelas, laporkan keduanya dan audit komentar salah, bukan hanya satu angka accuracy.

Pipeline lengkap ketiga model tersedia di outputs/accuracy_optimization/models/. Semua hasil historis dipertahankan. Target yang belum tercapai dilaporkan tanpa mengganti label, membuang contoh test sulit, atau memilih ulang seed berdasarkan test.