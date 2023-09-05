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

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
