# Hasil Final Accuracy MBG

| Model | Varian fitur | Accuracy validasi | Accuracy test eksploratif | Macro F1 test | Recall positif test |
|---|---|---:|---:|---:|---:|
| SVM | Ronde pertama: Accuracy Randomized | 80.74% | 82.69% | 0.6848 | 30.00% |
| KNN | KNN proyeksi bersama SVD-LDA | 80.74% | 82.28% | 0.7442 | 55.00% |
| Naive Bayes | Refinement NB_projected | 79.78% | 79.26% | 0.6587 | 25.00% |

Seluruh model >70% pada validasi: **True**. Seluruh model >70% pada test eksploratif: **True**.

Pipeline memakai classifier akhir LinearSVC, KNeighborsClassifier, dan MultinomialNB. KNN/Naive Bayes yang memakai SVD-LDA/diskretisasi harus dijelaskan sesuai varian fiturnya, bukan disebut classifier TF-IDF polos. Semua fitur terawasi dipelajari di fold training. Perbandingan pipeline dengan ekstraktor berbeda tidak mengisolasi pengaruh classifier saja.

Kriteria CV dan validasi adalah accuracy. Hasil historis dan kandidat yang lebih lemah tetap disimpan. Tidak ada perubahan label, pemilihan seed berdasarkan test, atau penghapusan komentar test sulit.

Test telah dipakai pada eksperimen sebelumnya sehingga hasil lanjutan bersifat eksploratif. Validasi juga digunakan berulang dan dapat optimistis. Konfirmasi independen memerlukan data baru yang belum digunakan. Accuracy tinggi tidak menghilangkan keterbatasan recall kelas positif.

Pipeline lengkap final ketiga algoritma disimpan di outputs/accuracy_optimization/final/models/.