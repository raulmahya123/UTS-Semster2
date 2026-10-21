# Penelitian Sentimen MBG

Buka `notebooks/MBG_Sentiment_Analysis.ipynb`, pilih kernel Python dengan dependensi pada `requirements.txt`, lalu gunakan **Run All**. Pasang dependensi menggunakan `pip install -r requirements.txt` pada lingkungan Python 3.12. Semua source penelitian berada di notebook; tidak ada helper `.py`.

Dataset asli disalin tanpa modifikasi ke `dataset/MBG-label.csv`. Tabel audit, split manifest, hasil grid search, metrik, contoh kesalahan, dan demo prediksi ada di `outputs/tables/`. Grafik PNG ada di `outputs/figures/`. Ringkasan kesimpulan dan audit ada di `outputs/reports/`. Pipeline terbaik ada di `outputs/models/best_pipeline.joblib`.

Notebook mencari folder proyek dari working directory proyek, folder notebook, atau folder induk proyek. Dependensi dikunci ke versi eksperimen setelah eksekusi. Notebook memakai tokenisasi NLTK berbasis regex dan stopword Sastrawi tanpa unduhan korpus tambahan. CV berjalan satu proses agar kompatibel dengan fungsi notebook dan membatasi penggunaan memori; full grid dapat membutuhkan beberapa menit atau lebih.

Pemilihan model memakai macro F1 validasi. Semua model di-refit ke training+validation sebelum satu evaluasi test. Data ambigu berlabel konflik dan duplikat representasi dinormalisasi menurut kebijakan eksplisit notebook. Jumlah baris pada output merupakan hasil aktual. Temuan hanya berlaku untuk korpus ini; jangan digeneralisasi tanpa desain sampling yang memadai.

Untuk prediksi baru, jalankan sel pemuatan joblib dan ubah daftar `new_comments`. Pipeline menyertakan fungsi preprocessing melalui wrapper cloudpickle; fungsi tidak perlu dipindah ke file Python terpisah. Gunakan versi pustaka yang tercatat dan hanya muat artefak terpercaya.

## Optimasi lanjutan

Bagian 13–17 notebook menambahkan RandomizedSearchCV dengan 24 kandidat per algoritma dan fold yang sama. Ubah `OPT_N_ITER` untuk memperbesar budget pencarian. Eksperimen mencakup fitur kata/karakter, bobot fitur, stemming, pengaturan TF-IDF, C dan class_weight SVM, jumlah tetangga/metric/weights KNN, serta alpha dan fit_prior MultinomialNB.

Hasil tambahan disimpan terpisah di `outputs/optimization/`. `tables/validation_before_after.csv` membandingkan validasi konfigurasi awal dan baru; `reports/selection_locked.json` mencatat pilihan sebelum audit test; `models/best_pipeline_optimized.joblib` berisi pipeline pilihan lanjutan. Konfigurasi awal tetap dipertahankan bila skor validasinya lebih baik.

Test yang sama sudah digunakan pada studi awal, sehingga evaluasi lanjutan diberi status eksploratif. Dibutuhkan data baru yang belum dilihat untuk konfirmasi independen. Menaikkan budget tuning tidak menjamin kenaikan performa.

## Target accuracy di atas 70%

Bagian 18–26 menambahkan eksperimen yang memilih parameter berdasarkan accuracy. Bagian awal berbasis macro F1 tetap disimpan sebagai riwayat. Jalankan sel import bagian 1 lalu bagian 18–26 bila ingin mengulang hanya eksperimen accuracy dengan file split/historis yang sudah tersedia. Run All tetap menjalankan seluruh penelitian.

Hasil akhir accuracy ada di `outputs/accuracy_optimization/final/tables/final_accuracy.csv`, laporan di `outputs/accuracy_optimization/final/reports/final_accuracy_summary.md`, dan tiga pipeline di `outputs/accuracy_optimization/final/models/`. Hasil fase awal/refinement tidak ditimpa.

KNN dan MultinomialNB dapat memakai proyeksi SVD–LDA dan/atau diskretisasi sebagai varian ekstraksi fitur. Cantumkan varian yang dipakai di metodologi; perbandingan pipeline yang memakai fitur berbeda tidak mengisolasi pengaruh classifier saja. Semua transformasi terawasi dilatih hanya di fold training. Accuracy dan recall positif harus dibaca bersama. Test lama tetap bersifat eksploratif karena telah dipakai sebelumnya.
