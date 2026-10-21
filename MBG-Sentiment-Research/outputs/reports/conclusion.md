# Kesimpulan Penelitian MBG

Dataset awal memuat 4,968 komentar; setelah audit tersisa 4,847. Distribusi anotasi dataset siap olah: positif 5.41%, netral 43.59%, negatif 51.00%. Hasil ini mendeskripsikan korpus, bukan seluruh masyarakat Indonesia.

Ketiga algoritma menggunakan preprocessing, TF-IDF, split stratified, dan fold CV yang konsisten. Pemenang berdasarkan macro F1 validasi adalah **SVM**, dengan skor 0.6619. Setelah refit training+validation, model ini mendapat accuracy test 0.7404, precision macro 0.6479, recall macro 0.6888, dan F1 macro 0.6641.

Perbandingan macro F1 test: SVM 0.6641, KNN 0.4757, Naive Bayes 0.4853. Peringkat test dilaporkan deskriptif dan tidak mengubah pilihan model berdasarkan validasi. Perbedaan angka tidak otomatis membuktikan signifikansi statistik.

Keterbatasan: minoritas positif kecil, asal dan waktu sampling belum terverifikasi, reliabilitas anotator tidak tersedia, serta kebijakan eksklusi komentar dapat mengubah komposisi data. Audit menemukan 0 kelompok konflik mentah dan 0 kelompok konflik normalisasi. Duplikat setelah normalisasi dikeluarkan sehingga estimand berubah menjadi komentar unik yang dapat diproses. Kesamaan semantik/parafrasa dan komentar dari pengguna/thread yang sama belum dapat dipisahkan karena metadata tidak tersedia. Model bag-of-words terbatas untuk sarkasme, konteks, dan negasi kompleks. Peninjauan contoh salah klasifikasi dibutuhkan untuk menguji hipotesis ini.

Rekomendasi: audit dan anotasi ulang konflik dengan beberapa anotator, laporkan inter-annotator agreement, perluas kelas positif serta sumber/waktu sampling, lakukan pengujian eksternal/temporal dan interval ketidakpastian, lalu evaluasi representasi kontekstual. Perubahan berikutnya memerlukan test baru untuk menjaga independensi evaluasi.
