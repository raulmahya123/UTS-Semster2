# Hasil Optimasi Lanjutan MBG

Pencarian tambahan memakai RandomizedSearchCV: 24 kandidat untuk masing-masing dari tiga algoritma, dengan 5 fold identik (360 fit CV tambahan). Ruang fitur mencakup TF-IDF kata dan karakter, unigram sampai trigram kata, document frequency, batas vocabulary, bobot fitur, stemming, serta parameter classifier dan penanganan prior/bobot kelas.

Macro F1 validasi terbaik awal: **0.6619**. Pilihan lanjutan: **SVM (Awal)**, macro F1 validasi **0.6619**, perubahan **+0.0000** (setara +0.00 poin persentase). Pilihan ini sudah dikunci sebelum audit test lanjutan. Konfigurasi awal boleh tetap menang bila pencarian baru tidak membaik.

Audit pada test lama: accuracy **0.7404**, macro F1 **0.6641**, recall positif **0.5750**. Angka ini **eksploratif**, karena test yang sama telah dilihat pada penelitian awal. Jangan mengklaimnya sebagai estimasi independen baru. Dibutuhkan test eksternal yang belum dilihat untuk konfirmasi.

Variasi karakter berpotensi menangani ejaan/slang, tetapi kombinasi fitur dan parameter berubah bersamaan sehingga tidak membuktikan satu penyebab peningkatan. Bobot/prior kelas dapat menambah recall positif sekaligus mengurangi precision; lihat tabel per kelas. Selisih kecil juga belum membuktikan signifikansi. Dataset masih memiliki minoritas positif kecil dan validasi telah dipakai berulang.

Pipeline terbaik disimpan terpisah di `outputs/optimization/models/best_pipeline_optimized.joblib`; pipeline dan laporan awal tidak ditimpa. Seluruh ruang pencarian, kandidat, fold scores, perbandingan validasi, prediksi test, contoh kesalahan, grafik, serta laporan optimasi tersedia di folder `outputs/optimization/`.

Langkah berikutnya: tambah anotasi positif yang representatif, audit kasus salah/ambigu bersama beberapa anotator, validasi pada sumber/waktu baru, serta jalankan nested CV bila sumber daya memadai. Menaikkan OPT_N_ITER memperluas pencarian dan biaya komputasi, tanpa menjamin perbaikan.
