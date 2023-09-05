# Laporan Proyek Machine Learning - Arif Hendrawan Priliyanto

## Project Overview

Dengan banyaknya pilihan film yang tersedia saat ini, semakin sulit bagi pengguna untuk menemukan film yang di sukai. Sistem rekomendasi film dapat membantu pengguna menemukan film yang sesuai dengan selera pengguna dengan merekomendasikan film berdasarkan rating, metadata film, atau kombinasi keduanya.

Proyek ini penting untuk diselesaikan karena dapat memberikan manfaat bagi berbagai pihak, pengguna dapat menemukan film yang lebih sesuai dengan selera mereka. Sistem rekomendasi film menggunakan data rating dan metadata film untuk merekomendasikan film yang mirip dengan film yang telah disukai pengguna sebelumnya. Hal ini dapat menghemat waktu pengguna dalam mencari film yang mereka sukai.

Sistem rekomendasi film dapat membantu pengguna menemukan film yang sesuai dengan selera mereka. Hal ini dapat meningkatkan kepuasan pengguna dan mendorong mereka untuk terus menggunakan layanan streaming video.

## Business Understanding

Dalam kasus proyek sistem rekomendasi film, tujuan bisnis adalah membantu pengguna menemukan film yang kemungkinan mereka sukai. Situasi saat ini adalah terdapat banyak data yang tersedia tentang film, seperti rating, ulasan, dan metadata. Tantangan yang dihadapi bisnis adalah sulit bagi pengguna untuk menemukan film yang kemungkinan mereka sukai, dan bisnis tidak dapat sepenuhnya memonetisasi data yang mereka miliki tentang film.

### Problem Statements

- Bagaimana cara mengembangkan sistem rekomendasi film yang akurat dan dapat diandalkan?
- Bagaimana cara memaksimalkan kepuasan pengguna dengan sistem rekomendasi film?
- Bagaimana cara mempromosikan film secara efisien dan efektif dengan sistem rekomendasi film?

### Goals

- Mengembangkan sistem rekomendasi film yang dapat merekomendasikan film yang sesuai dengan selera pengguna. Sistem rekomendasi film harus dapat mengakomodasi berbagai faktor yang memengaruhi selera pengguna, seperti rating dan ulasan film yang diberikan oleh pengguna dapat digunakan untuk mengukur selera mereka. Dapat dengan cara rekomendasi kolaboratif yaitu merekomendasikan film kepada pengguna berdasarkan rating dan ulasan film yang diberikan oleh pengguna lain yang memiliki selera yang sama atau rekomendasi berbasis konten yang merekomendasikan film kepada pengguna berdasarkan metadata tentang film.
- Sistem rekomendasi film harus dapat memenuhi kebutuhan dan harapan pengguna dengan cara dapat merekomendasikan film yang kemungkinan besar akan disukai oleh pengguna.
- Mempromosikan film secara efisien dan efektif dengan sistem rekomendasi film dimana sistem rekomendasi film dapat digunakan untuk menjangkau pengguna yang lebih luas, karena dapat merekomendasikan film kepada pengguna yang mungkin tidak pernah mendengar tentang film tersebut sebelumnya.

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
   - Melakukan Deskripsi Variabel
     1. Movies Variabel
        
        RangeIndex: 9742 entries, 0 to 9741
         Data columns (total 3 columns):
        
          |#   |Column|   Non-Null Count | Dtype |
         |---  |------|   -------------- | ----- |
          |0   |movieId|  9742 non-null  | int64 |
          |1   |title |   9742 non-null  | object|
          |2  |genres |  9742 non-null  | object|
        
         dtypes: int64(1), object(2)
        
        Berdasarkan output di atas, dapat diketahui bahwa file movies.csv memiliki 9742 entri. Kolom "movieId" adalah tipe data integer (int64) dan tidak memiliki nilai yang hilang (non-null count adalah 9742). Kolom "title" adalah tipe data objek (object) dan tidak memiliki nilai yang hilang (non-null count adalah 9742). Kolom "genres" juga adalah tipe data objek (object) dan tidak memiliki nilai yang hilang (non-null count adalah 9742).

        Mengecek deskripsi statistik data dengan fitur describe(). Fungsi describe() memberikan informasi statistik pada masing-masing kolom. Karena pada movies hanya movieId yang bernilai int maka hanya movieId yang ditampilkan.

         |       |       movieId |
         |------:|--------------:|
         | count |   9742.000000 |
         |  mean |  42200.353623 |
         |  std  |  52160.494854 |
         |  min  |      1.000000 |
         |  25%  |   3248.250000 |
         |  50%  |   7300.000000 |
         |  75%  |  76232.000000 |
         |  max  | 193609.000000 |

      2. Link Variabel
         
         RangeIndex: 9742 entries, 0 to 9741
         Data columns (total 3 columns):
   
         |   # |  Column | Non-Null Count | Dtype   |
         |----:|--------:|----------------|---------|
         | --- |  ------ | -------------- | -----   |
         |  0  | movieId | 9742 non-null  | int64   |
         |  1  |  imdbId | 9742 non-null  | int64   |
         |  2  |  tmdbId | 9734 non-null  | float64 |
   
         dtypes: float64(1), int64(2)
      
         Berdasarkan output di atas, dapat diketahui bahwa file links.csv memiliki 9742 entri. Tipe data movieId adalah integer (int64), tipe data imdbId adalah integer (int64), tipe data tmdbId ini adalah float (float64). movieId dan imdbId tidak ada nilai yang hilang (non-null count adalah 9742), namun tmdbId ada beberapa nilai yang hilang (missing values), yaitu 8 dari 9742 entri (non-null count adalah 9734).
      
         Mengecek deskripsi statistik data dengan fitur describe(). Fungsi describe() memberikan informasi statistik pada masing-masing kolom. 
      
         |       |       movieId |       imdbId |        tmdbId |
         |------:|--------------:|-------------:|--------------:|
         | count |   9742.000000 | 9.742000e+03 |   9734.000000 |
         |  mean |  42200.353623 | 6.771839e+05 |  55162.123793 |
         |  std  |  52160.494854 | 1.107228e+06 |  93653.481487 |
         |  min  |      1.000000 | 4.170000e+02 |      2.000000 |
         |  25%  |   3248.250000 | 9.518075e+04 |   9665.500000 |
         |  50%  |   7300.000000 | 1.672605e+05 |  16529.000000 |
         |  75%  |  76232.000000 | 8.055685e+05 |  44205.750000 |
         |  max  | 193609.000000 | 8.391976e+06 | 525662.000000 |
      
         Berikut adalah simpulan yang dapat diambil dari data ini:
        
         - Jumlah data: Terdapat 9.742 baris data dalam dataset ini.
           
         - Statistik rata-rata (mean):
         Rata-rata movieId adalah sekitar 42.200,35.
         Rata-rata imdbId adalah sekitar 677.183,9 (dalam notasi ilmiah, 6.771839e+05).
         Rata-rata tmdbId adalah sekitar 55.162,12.
         
         - Deviasi standar (std):
         Deviasi standar movieId adalah sekitar 52.160,49, yang menunjukkan variasi yang cukup besar dalam kolom ini.
         Deviasi standar imdbId adalah sekitar 1.107.228, yang juga menunjukkan variasi yang besar.
         Deviasi standar tmdbId adalah sekitar 93.653,48, yang menunjukkan variasi besar dalam kolom ini.
      
         - Nilai Minimum dan Maksimum:
         Nilai terendah (minimum) dalam kolom movieId adalah 1, sedangkan nilai tertinggi (maksimum) adalah 193.609.
         Nilai terendah dalam kolom imdbId adalah sekitar 417, sedangkan nilai tertinggi adalah sekitar 8.391.976.
         Nilai terendah dalam kolom tmdbId adalah 2, sedangkan nilai tertinggi adalah 525.662.
      
         - Quartil:
         Kuartil pertama (25%) movieId adalah sekitar 3.248,25.
         Kuartil pertama (25%) imdbId adalah sekitar 95.180,75.
         Kuartil pertama (25%) tmdbId adalah sekitar 9.665,5.
      
         - Median (Kuartil kedua atau 50%):
         Nilai tengah (median) movieId adalah sekitar 7.300.
         Nilai tengah (median) imdbId adalah sekitar 167.260,5.
         Nilai tengah (median) tmdbId adalah sekitar 16.529.
      
         - Kuartil ketiga (75%):
         Kuartil ketiga (75%) movieId adalah sekitar 76.232.
         Kuartil ketiga (75%) imdbId adalah sekitar 805.568,5.
         Kuartil ketiga (75%) tmdbId adalah sekitar 44.205,75.

      3. Tags Variabel

         RangeIndex: 3683 entries, 0 to 3682
         Data columns (total 4 columns):
         
         |   # |    Column | Non-Null Count |  Dtype |
         |----:|----------:|---------------:|-------:|
         | --- |    ------ | -------------- |  ----- |
         |  0  |    userId |  3683 non-null |  int64 |
         |  1  |   movieId |  3683 non-null |  int64 |
         |  2  |       tag |  3683 non-null | object |
         |  3  | timestamp |  3683 non-null |  int64 |
         
         dtypes: int64(3), object(1)

         Berdasarkan output di atas, dapat diketahui bahwa file tags.csv memiliki 3683 entri. Tipe data userId adalah integer (int64), tipe data movieId adalah integer (int64), tipe data tag adalah object (object), tipe data timestamp adalah integer (int64). Dari ke 4 kolom tidak ada nilai yang hilang (non-null count adalah 3683).

         Mengecek deskripsi statistik data dengan fitur describe(). Fungsi describe() memberikan informasi statistik pada masing-masing kolom.

         |       |      userId |       movieId |    timestamp |
         |------:|------------:|--------------:|-------------:|
         | count | 3683.000000 |   3683.000000 | 3.683000e+03 |
         |  mean |  431.149335 |  27252.013576 | 1.320032e+09 |
         |  std  |  158.472553 |  43490.558803 | 1.721025e+08 |
         |  min  |    2.000000 |      1.000000 | 1.137179e+09 |
         |  25%  |  424.000000 |   1262.500000 | 1.137521e+09 |
         |  50%  |  474.000000 |   4454.000000 | 1.269833e+09 |
         |  75%  |  477.000000 |  39263.000000 | 1.498457e+09 |
         |  max  |  610.000000 | 193565.000000 | 1.537099e+09 |

          Berikut adalah simpulan yang dapat diambil dari data ini:

         - Jumlah data: Terdapat 3.683 baris data dalam dataset ini.
           
         - Statistik rata-rata (mean):
         Rata-rata userId adalah sekitar 431,15.
         Rata-rata movieId adalah sekitar 27.252,01.
         Rata-rata timestamp adalah sekitar 1.320.032.000.

         - Deviasi standar (std):
         Deviasi standar userId adalah sekitar 158,47, yang menunjukkan variasi yang cukup besar dalam kolom ini.
         Deviasi standar movieId adalah sekitar 43.490,56, yang juga menunjukkan variasi yang besar.
         Deviasi standar timestamp adalah sekitar 172.102.500, yang menunjukkan variasi yang besar dalam kolom ini.

         - Nilai Minimum dan Maksimum:
         Nilai terendah (minimum) dalam kolom userId adalah 2, sedangkan nilai tertinggi (maksimum) adalah 610.
         Nilai terendah dalam kolom movieId adalah 1, sedangkan nilai tertinggi adalah 193.565.
         Nilai terendah dalam kolom timestamp adalah sekitar 1.137.179.000, sedangkan nilai tertinggi adalah sekitar 1.537.099.000.

         - Quartil:
         Kuartil pertama (25%) userId adalah sekitar 424.
         Kuartil pertama (25%) movieId adalah sekitar 1.262,5.
         Kuartil pertama (25%) timestamp adalah sekitar 1.137.521.000.

         - Median (Kuartil kedua atau 50%):
         Nilai tengah (median) userId adalah sekitar 474.
         Nilai tengah (median) movieId adalah sekitar 4.454.
         Nilai tengah (median) timestamp adalah sekitar 1.269.833.000.

         - Kuartil ketiga (75%):
         Kuartil ketiga (75%) userId adalah sekitar 477.
         Kuartil ketiga (75%) movieId adalah sekitar 39.263.
         Kuartil ketiga (75%) timestamp adalah sekitar 1.498.457.000.

      4. Rating Variabel
    
         RangeIndex: 100836 entries, 0 to 100835
         Data columns (total 4 columns):
    
         |   # |    Column |  Non-Null Count |   Dtype |
         |----:|----------:|----------------:|--------:|
         |  0  |    userId | 100836 non-null |   int64 |
         |  1  |   movieId | 100836 non-null |   int64 |
         |  2  |    rating | 100836 non-null | float64 |
         |  3  | timestamp | 100836 non-null |   int64 |
            
         dtypes: float64(1), int64(3)
    
         Berdasarkan output di atas, dapat diketahui bahwa file ratings.csv memiliki 100836 entri. Tipe data userId, movieId dan timestamp adalah integer (int64), dan tipe data rating adalah float (float64). Dari ke 4 kolom tidak ada nilai yang hilang (non-null count adalah 100836).

         |   | userId | movieId | rating | timestamp |
         |--:|-------:|--------:|-------:|----------:|
         | 0 |      1 |       1 |    4.0 | 964982703 |
         | 1 |      1 |       3 |    4.0 | 964981247 |
         | 2 |      1 |       6 |    4.0 | 964982224 |
         | 3 |      1 |      47 |    5.0 | 964983815 |
         | 4 |      1 |      50 |    5.0 | 964982931 |

         Dari hasil output fungsi ratingMovies.head(), kita dapat mengidentifikasi bahwa data rating terdiri dari 4 kolom dengan atribut-atribut berikut:
         - userId: Kolom ini berisi ID unik untuk setiap pengguna yang memberikan penilaian pada film-film dalam dataset.
         - movieId: Kolom ini berisi ID unik untuk setiap film yang menerima penilaian dari pengguna. Film-film ini sesuai dengan film-film dalam dataset.
         - rating: Kolom ini berisi penilaian yang diberikan oleh pengguna pada film tertentu. Nilai penilaian ini mungkin berupa skor atau peringkat yang diberikan pengguna pada film-film tersebut.
         - timestamp: Kolom ini berisi timestamp atau waktu ketika penilaian diberikan oleh pengguna pada film. Ini mencatat kapan penilaian tersebut terjadi.
        
         Mengecek deskripsi statistik data dengan fitur describe(). Fungsi describe() memberikan informasi statistik pada masing-masing kolom.

         Berikut adalah simpulan yang dapat diambil dari data ini:

         - Jumlah data: Terdapat 100.836 baris data dalam dataset ini.
         
         - Statistik rata-rata (mean):
         Rata-rata userId adalah sekitar 326,13.
         Rata-rata movieId adalah sekitar 19.435,30.
         Rata-rata rating adalah sekitar 3,50.
         Rata-rata timestamp adalah sekitar 1.205.946.000.

         - Deviasi standar (std):
         Deviasi standar userId adalah sekitar 182,62, yang menunjukkan variasi yang cukup besar dalam kolom ini.
         Deviasi standar movieId adalah sekitar 35.530,99, yang juga menunjukkan variasi yang besar.
         Deviasi standar rating adalah sekitar 1,04, yang menunjukkan variasi yang lebih rendah dibandingkan dengan kolom lainnya.
         Deviasi standar timestamp adalah sekitar 216.261.000, yang menunjukkan variasi yang besar dalam kolom ini.

         - Nilai Minimum dan Maksimum:
         Nilai terendah (minimum) dalam kolom userId adalah 1, sedangkan nilai tertinggi (maksimum) adalah 610.
         Nilai terendah dalam kolom movieId adalah 1, sedangkan nilai tertinggi adalah 193.609.
         Nilai terendah dalam kolom rating adalah 0,5, sedangkan nilai tertinggi adalah 5.
         Nilai terendah dalam kolom timestamp adalah sekitar 828.124.600, sedangkan nilai tertinggi adalah sekitar 1.537.799.000.

         - Quartil:
         Kuartil pertama (25%) userId adalah sekitar 177.
         Kuartil pertama (25%) movieId adalah sekitar 1.199.
         Kuartil pertama (25%) rating adalah 3.
         Kuartil pertama (25%) timestamp adalah sekitar 1.019.124.000.

         - Median (Kuartil kedua atau 50%):
         Nilai tengah (median) userId adalah sekitar 325.
         Nilai tengah (median) movieId adalah sekitar 2.991.
         Nilai tengah (median) rating adalah 3,5.
         Nilai tengah (median) timestamp adalah sekitar 1.186.087.000.

         - Kuartil ketiga (75%):
         Kuartil ketiga (75%) userId adalah sekitar 477.
         Kuartil ketiga (75%) movieId adalah sekitar 8.122.
         Kuartil ketiga (75%) rating adalah 4.
         Kuartil ketiga (75%) timestamp adalah sekitar 1.435.994.000.

         Berdasarkan statistik yang diberikan untuk kolom "rating" dalam dataset, Nilai rata-rata yang mendekati 3.50 menunjukkan penilaian netral secara umum, sedangkan nilai maksimum adalah 5.0, yang mungkin menunjukkan bahwa film-film dalam dataset ini menerima penilaian tertinggi. Standar deviasi yang relatif rendah menunjukkan bahwa penilaian pengguna cenderung mendekati rata-rata.

   - Menggabungkan variabel-variabel
   - Membersihkan data dari kesalahan dan anomali
   - Menghapus data duplikat 

## Data Preparation

   - Mengatasi Missing Value
     
     Mengecek apakah terdapat nilai yang null atau tidak.
   

      |    userId_x |      0 |
      |------------:|-------:|
      |   movieId   |      0 |
      |    rating   |      0 |
      | timestamp_x |      0 |
      |    title    | 334049 |
      |    genres   | 334049 |
      |    imdbId   | 334049 |
      |    tmdbId   | 334062 |
      |   userId_y  | 201672 |
      | tag         | 201672 |
      | timestamp_y | 201672 |

      Setelah dicek ternyata banyak nilai yang null / nan di fitur title dan genre. Mengatasi nya dengan cara mengisi data dengan data title dan genre yang memiliki nilai 'movieId' sama. Data title dan genre adalah data penting yang dapat digunakan untuk menggambarkan film. Title adalah judul film, sedangkan genre adalah kategori film. Kedua data ini dapat membantu untuk memahami film tersebut dengan lebih baik. Jika data title dan genre tidak ada, maka tidak akan dapat mengetahui judul dan genre film tersebut. Hal ini dapat menyebabkan kebingungan dan kesulitan dalam menganalisis data film. Oleh karena itu, perlu mengisi data title dan genre untuk film-film yang memiliki nilai movieId yang sama. Dengan begitu, akan memiliki data yang lengkap untuk semua film, sehingga dapat menganalisis data tersebut dengan lebih akurat dan efektif.

   - Membuat variabel baru bernama fix_movie untuk menyimpan dataframe dan juga membuat variabel preparation
   - Karena hanya akan menggunakan data unik untuk dimasukkan ke dalam proses pemodelan maka menghapus data duplikat pada kolom 'movieId'
   - Untuk memudahkan pemrosesan data melakukan konversi data series menjadi list.
     Meningkatkan efisiensi pemrosesan data. Data series adalah data yang terstruktur dalam bentuk kolom, sedangkan list adalah data yang terstruktur dalam bentuk baris. Data list lebih efisien untuk diproses oleh komputer daripada data series. Hal ini karena data list dapat diakses secara langsung, sedangkan data series harus diakses secara berurutan. Dalam kasus ini, memudahkan akses ke data movieId, title, dan genre. Data movieId, title, dan genre merupakan data series yang terstruktur dalam bentuk kolom. Dengan mengubah data series tersebut menjadi list, maka data tersebut menjadi lebih mudah untuk diakses.

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

   Langkah-langkah pembuatan model Content Based Filtering
   - Menggunakan TF-IDF Vectorizer untuk menemukan representasi fitur penting dari setiap genre film.
   - Melakukan fit dan transformasi ke dalam bentuk matriks.
   - Untuk menghasilkan vektor tf-idf dalam bentuk matriks, kita menggunakan fungsi todense().
   - Menghitung derajat kesamaan (similarity degree) antar film dengan teknik cosine similarity
   - Membuat fungsi movie_recommendations dengan beberapa parameter sebagai berikut:
      - nama_movie: Ini adalah parameter yang mewakili nama film yang akan digunakan sebagai referensi untuk mencari rekomendasi film lainnya. Dengan kata lain, ini adalah film yang akan menjadi dasar untuk mencari film-film serupa atau rekomendasi.
      - similarity_data (default: cosine_sim_df): Parameter ini adalah matriks atau data kesamaan (similarity) antar film. Biasanya, ini akan berisi nilai-nilai kesamaan antara setiap pasangan film dalam dataset. Secara khusus, dalam kode, ini adalah matriks kesamaan kosinus (cosine_sim_df), yang digunakan untuk mengukur sejauh mana dua film serupa.
      - items (default: movie_new[['movie_name', 'genre']]): Parameter ini adalah DataFrame yang berisi data film. Dalam kode, ini mencakup dua kolom, yaitu 'movie_name' (nama film) dan 'genre' (genre film). Ini digunakan untuk mengidentifikasi film berdasarkan nama dan genre saat mengembalikan rekomendasi.
      - k (default: 5): Parameter ini menentukan jumlah film rekomendasi yang akan dikembalikan. Secara default, akan mengembalikan 5 rekomendasi teratas, tetapi dapat menggantinya dengan angka lain sesuai dengan berapa banyak rekomendasi yang di inginkan.
   - Melakukan pengujian model
   
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

   Langkah-langkah pembuatan model Content Based Filtering
   - Membuat variabel rating dan menetapkan data pada variabel tersebut. Untuk memudahkan supaya tidak tertukar dengan fitur ‘rating’ pada data, kita ubah nama variabel rating menjadi df.
   - Mempersiapkan data untuk menyandikan (encode) fitur ‘user’ dan ‘movieId’ ke dalam indeks integer.
   - Mapping userId ke dataframe user dan Mapping movieId ke dataframe movie
   - Mengacak datanya terlebih dahulu agar distribusinya menjadi random
   - Membagi data train dan validasi dengan komposisi 80:20. Namun sebelumnya, perlu memetakan (mapping) data user dan movie menjadi satu value terlebih dahulu. Lalu, buatlah rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training.
   - Menghitung skor kecocokan antara pengguna dan movie dengan teknik embedding. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid.
   - 

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
