# Laporan Proyek Machine Learning - Arif Hendrawan Priliyanto

## Project Overview

Dengan berkembangnya industri hiburan dan meningkatnya akses ke berbagai pilihan film dan acara televisi, pengguna seringkali menghadapi kesulitan dalam memilih film yang sesuai dengan preferensi mereka. Penilaian film oleh pengguna lain dan rekomendasi berbasis data adalah alat yang berguna dalam membantu pengguna menemukan film yang mereka nikmati.

Sistem rekomendasi film telah menjadi fitur penting di berbagai platform streaming video dan layanan media digital. Mereka membantu meningkatkan pengalaman pengguna dengan menawarkan film yang relevan dengan preferensi individu. Untuk mengembangkan sistem rekomendasi yang efektif, diperlukan dataset yang kaya dan informatif yang mencakup informasi tentang film, penilaian pengguna, dan atribut lainnya.

Dataset "Movie Recommendation Data" yang tersedia menawarkan kesempatan untuk membangun model rekomendasi yang lebih akurat dan personal, yang pada gilirannya dapat meningkatkan kepuasan pengguna dalam menemukan film yang sesuai dengan selera mereka.

Oleh karena itu, proyek ini bertujuan untuk menggali potensi dataset ini dan mengembangkan solusi yang dapat memberikan rekomendasi film yang lebih baik kepada pengguna berdasarkan data historis mereka. Hal ini akan membantu meningkatkan pengalaman menonton film dan membantu platform streaming video untuk mempertahankan dan menarik lebih banyak pengguna.

## Business Understanding

Bagian laporan ini mencakup:

### Problem Statements

- Bagaimana kita dapat membangun sistem rekomendasi film yang efektif untuk memberikan rekomendasi film kepada pengguna berdasarkan preferensi mereka dan informasi yang tersedia dalam dataset, sehingga meningkatkan pengalaman menonton film dan meningkatkan retensi pengguna pada platform streaming video?

### Goals

- Dengan cara Mengembangkan algoritma rekomendasi film yang akurat dan personal yang memanfaatkan informasi dalam dataset, seperti data penilaian pengguna, informasi film (judul, genre, dll.)

### Solution Approach
Untuk mengatasi Problem Statement dalam mengembangkan sistem rekomendasi film yang efektif, dengan cara teknik Content-Based Filtering dan Collaborative Filtering
1. Content-Based Filtering:
   Content-Based Filtering menggunakan informasi konten atau atribut dari item (dalam konteks ini, film) untuk membuat profil dan rekomendasi. Ini berfokus pada kemiripan antara preferensi pengguna dengan atribut konten item.
2. Collaborative Filtering:
   Collaborative Filtering berfokus pada pola penilaian pengguna terhadap item dan mengidentifikasi kesamaan preferensi pengguna atau kesamaan item untuk memberikan rekomendasi. Ini tidak memerlukan informasi konten.
3. Root Mean Squared Error (RMSE)
   Root Mean Squared Error (RMSE) adalah salah satu metrik evaluasi yang umum digunakan untuk mengukur sistem rekomendasi. RMSE mengukur rata-rata dari kuadrat error antara nilai prediksi dan nilai aktual. Semakin kecil nilai RMSE, semakin baik sistem rekomendasi tersebut.

## Data Understanding
Data yang digunakan dalam proyek machine learning ini berasal dari dataset Movie Recommendation Data yang diambil dari platform Kaggle.
[Link Kaggle Dataset](https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data).

Variabel-variabel pada Movie Recommendation Data dataset adalah sebagai berikut:
- MovieID: ID atau kode unik yang mengidentifikasi setiap film.
- Title: Judul film.
- Genres: Genre-genre atau kategori film.
- UserID: ID pengguna yang memberikan penilaian atau ulasan.
- IMDbID: identifikasi unik yang digunakan oleh IMDb
- TMDbID: identifikasi unik yang digunakan oleh TMDb
- Rating: Penilaian yang diberikan oleh pengguna terhadap film (biasanya dalam skala tertentu, misalnya 1 hingga 5).
- Timestamp: Waktu ketika penilaian atau ulasan diberikan.
- Tags: Kata kunci atau label yang terkait dengan film.
- Links: Tautan atau URL ke informasi lebih lanjut tentang film.

### Exploratory Data Analysis
   Tahap awal dalam analisis data yang bertujuan untuk memahami dataset dengan lebih baik. Dalam konteks dataset film dan penilaian pengguna, berikut adalah beberapa langkah yang dilakukan dalam EDA:
   - Memahami variabel-variabel pada data seperti tipe data, jumlah data dan distribusi data.
   - Menggabungkan variabel-variabel
   - Membersihkan data dari kesalahan dan anomali
   - Menghapus data duplikat 

## Data Preparation

   - Mengatasi Missing Value
     Mengecek apakah terdapat nilai yang null atau tidak. Setelah dicek ternyata banyak nilai yang null / nan di fitur title dan genre. Mengatasi nya dengan cara mengisi data dengan data title dan genre yang memiliki nilai 'movieId' sama.
   - Membuat variabel baru bernama fix_movie untuk menyimpan dataframe dan juga membuat variabel preparation
   - Karena hanya akan menggunakan data unik untuk dimasukkan ke dalam proses pemodelan maka menghapus data duplikat pada kolom 'movieId'
   - Untuk memudahkan pemrosesan data melakukan konversi data series menjadi list. Karena List adalah struktur data yang lebih sederhana daripada series, sehingga lebih mudah untuk diproses oleh komputer.

## Modeling and Result
Model sisten rekomendasi di buat untuk menyelesaikan permasalahan menggunakan dua model yaitu :
### Content Based Filtering
   Model pengembangan dengan Content-Based Filtering adalah salah satu pendekatan dalam sistem rekomendasi yang digunakan untuk memberikan rekomendasi berdasarkan karakteristik atau konten dari item yang dijelaskan oleh fitur-fiturnya. Model ini bekerja dengan menganalisis item yang disukai pengguna sebelumnya dan mencoba untuk merekomendasikan item serupa berdasarkan fitur-fitur item tersebut. Untuk membuat sistem rekomendasi berbasis konten, kita perlu menggunakan konsep vektorisasi, TF-IDF, dan Cosine Similarity. Data atau teks perlu dikonversi menjadi vektor terlebih dahulu sebelum dapat dianalisis.
   
   Kelebihan content-based filtering:
   - Efektif untuk item yang memiliki deskripsi yang kaya.
   - Dapat merekomendasikan film baru kepada pengguna, bahkan jika film tersebut belum pernah dinilai atau ditonton oleh pengguna sebelumnya.
   - Dapat merekomendasikan film yang tidak terlalu populer, yang mungkin tidak direkomendasikan oleh sistem rekomendasi lainnya.
     
   Kekurangan content-based filtering:
   - Membutuhkan deskripsi film yang lengkap dan akurat.
   - Dapat merekomendasikan film yang tidak relevan dengan preferensi pengguna, jika deskripsi item tidak akurat atau tidak lengkap.
   - Dapat merekomendasikan film yang sudah dinilai oleh pengguna sebelumnya.

Result 
- Melakukan percobaan untuk untuk menemukan rekomendasi genre movie yang mirip dengan Film misal Welcome to Me (2014)
   | movie_name	                           |   genre      |
   | :---------:	                           |  :---------:	|
   | Welcome to Me (2014)	                  | Comedy, Drama |
- Top-N recommendation nya :
  
   |  | movie_name	                           |   genre      |
   |--| :---------:	                           |  :---------:	|
   |0	| Breakfast on Pluto (2005)	            | Comedy, Drama |
   |1	| Million Dollar Arm (2014)	            | Comedy, Drama |
   |2	| Deconstructing Harry (1997)	            | Comedy, Drama |
   |3	| Blaze (1989)	                           | Comedy, Drama |
   |4	| Paper Birds (Pájaros de papel) (2010)	| Comedy, Drama |

  Sistem memberikan rekomendasi nama film dengan genre yang sama sesuai inputan yaitu genre Comedy, Drama

### Collaborative Filtering
   Pengembangan model dengan Collaborative Filtering adalah salah satu pendekatan dalam sistem rekomendasi yang menggunakan informasi tentang preferensi pengguna dan item untuk menghasilkan rekomendasi. Pada model ini melakukan persiapan data untuk menyandikan (encode) fitur ‘user’ dan ‘movieId’ ke dalam indeks integer, mapping userId ke dataframe user dan mapping movieId ke dataframe movie, membagi data train dan validasi dengan komposisi 80:20. Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer
   
   Kelebihan Collaborative Filtering:
   - Efektif dalam merekomendasikan item baru yang belum banyak diketahui oleh pengguna
   - Sistem rekomendasi dapat dengan mudah ditingkatkan ketika pengguna atau item baru ditambahkan, tanpa perlu melakukan perhitungan ulang yang rumit.
   - Tidak memerlukan informasi rinci tentang item atau pengguna
     
   Kekurangan Collaborative Filtering:
   - Jika data rating tidak lengkap atau tidak akurat, maka sistem rekomendasi collaborative filtering dapat merekomendasikan item yang tidak relevan dengan preferensi pengguna.
   - Jika sistem rekomendasi collaborative filtering hanya menggunakan data rating, maka sistem tersebut tidak dapat merekomendasikan item baru kepada pengguna.
   - Sistem rekomendasi collaborative filtering dapat merekomendasikan item yang sudah dinilai oleh pengguna sebelumnya.

Result 
- Melakukan percobaan dengan memilih pengguna secara acak

![Screenshot 2023-09-05 230921](https://github.com/arifhendrawan023/Proyek-Akhir-Machine-Learning-Terapan-Membuat-Model-Sistem-Rekomendasi/assets/55530939/fcb2f58b-9ce9-40ce-8945-f315e6da4879)

Rekomendasi tersebut mencakup film-film yang telah mendapatkan peringkat tinggi dari pengguna dengan ID 239 serta daftar top 10 rekomendasi film yang mungkin sesuai dengan preferensinya. Rekomendasi ini dapat membantu pengguna menemukan film-film baru yang mungkin mereka nikmati berdasarkan preferensi mereka sebelumnya.

## Evaluation
Menggunakan metrik Evaluasi root mean squared error (RMSE) untuk mengevaluasi model Collaborative Filtering. Secara umum, RMSE adalah metrik evaluasi yang berguna untuk mengukur sistem rekomendasi. Dengan menggunakan RMSE, kita dapat memastikan bahwa sistem rekomendasi yang kita bangun telah mencapai tujuannya.

Root Mean Squared Error (RMSE) adalah salah satu metrik evaluasi yang umum digunakan untuk mengukur sistem rekomendasi. RMSE mengukur rata-rata dari kuadrat error antara nilai prediksi dan nilai aktual. Semakin kecil nilai RMSE, semakin baik sistem rekomendasi tersebut.

Dalam konteks sistem rekomendasi, RMSE dapat digunakan untuk mengukur seberapa akurat sistem rekomendasi dapat memprediksi preferensi pengguna. Semakin kecil nilai RMSE, semakin akurat sistem rekomendasi tersebut dalam memprediksi film mana yang akan dinikmati pengguna.

RMSE dapat dihitung dengan menggunakan rumus berikut:
RMSE = √∑(y_true - y_pred)^2/n

Berikut adalah cara menggunakan metrik RMSE untuk mengukur akurasi model rekomendasi:
- Latih model rekomendasi menggunakan data yang tersedia.
- Uji model rekomendasi menggunakan data yang berbeda dari data yang digunakan untuk melatih model.
- Hitung nilai RMSE untuk model rekomendasi.

Setelah dilakukan pengujian mendapatkan hasil :
loss: 0.5968 - root_mean_squared_error: 0.1876 - val_loss: 0.6083 - val_root_mean_squared_error: 0.1998

![download (15)](https://github.com/arifhendrawan023/Proyek-Akhir-Machine-Learning-Terapan-Membuat-Model-Sistem-Rekomendasi/assets/55530939/cabb51d9-031b-497d-a83c-4e8b94cb2d24)


Dari proses ini, kita memperoleh nilai error akhir sebesar sekitar 0.1876 dan error pada data validasi sebesar 0.1998. Nilai tersebut cukup bagus untuk sistem rekomendasi
