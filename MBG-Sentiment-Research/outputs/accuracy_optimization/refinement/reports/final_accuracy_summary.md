# Hasil Final Optimasi Accuracy

| Model | Varian | Validasi | Test eksploratif | Macro F1 test | Recall positif test |
|---|---|---:|---:|---:|---:|
| SVM | Ronde pertama: Accuracy Randomized | 80.74% | 82.69% | 0.6848 | 30.00% |
| Naive Bayes | Refinement NB_projected | 79.78% | 79.26% | 0.6587 | 25.00% |
| KNN | Refinement KNN | 70.98% | 72.53% | 0.6441 | 40.00% |

Seluruh model melampaui 70% pada validasi: **True**; pada test eksploratif: **True**.

Pemilihan memakai accuracy validasi setelah tuning CV accuracy. Tidak ada penggantian label, pemilihan seed, atau penghapusan komentar test sulit untuk mencapai target. Pipeline kelas akhirnya tetap LinearSVC, KNeighborsClassifier, dan MultinomialNB.

Varian SVD/LDA/diskretisasi menggunakan representasi tambahan dan harus dilaporkan sebagai pipeline tersebut, bukan classifier TF-IDF polos. Semua transformasi terawasi di-fit di dalam training fold. Perbedaan pipeline tidak mengisolasi pengaruh algoritma classifier saja.

Test telah dipakai pada eksperimen terdahulu sehingga angka lanjutan bersifat eksploratif. Validasi digunakan berulang dan dapat optimistis. Gunakan data eksternal baru untuk konfirmasi. Recall positif yang rendah tetap merupakan keterbatasan walaupun accuracy mencapai sasaran.

Hasil tahap sebelumnya dipertahankan. Model final ketiga algoritma berada di outputs/accuracy_optimization/refinement/models/.