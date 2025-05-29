# Laporan Proyek Machine Learning - Fatikha Hudi Aryani

## Project Overview

Saat ini, industri kosmetik dan kecantikan mengalami perkembangan pesat seiring meningkatnya kebutuhan konsumen akan produk kecantikan yang beragam dan berkualitas. Platform e-commerce seperti Sociolla hadir sebagai solusi untuk memudahkan konsumen menemukan dan membeli produk kecantikan tanpa harus berbelanja secara langsung di toko fisik. Namun, dengan ribuan produk yang tersedia di platform ini, konsumen sering kali kesulitan menentukan pilihan yang paling sesuai dengan kebutuhan dan preferensi mereka. Jika dibiarkan, hal ini tidak hanya dapat menurunkan pengalaman pengguna tetapi juga mengurangi peluang penjualan karena konsumen mungkin akan meninggalkan platform tanpa melakukan pembelian. Oleh karena itu, sistem rekomendasi menjadi solusi penting untuk mengatasi tantangan ini dengan membantu konsumen menemukan produk yang relevan secara cepat dan efisien sesuai dengan kebutuhan dan preferensi mereka.

Permasalahan utama yang perlu diselesaikan yaitu bagaimana cara menyaring informasi yang sangat banyak dan beragam untuk memberikan rekomendasi yang relevan. Maka dari itu, dengan menggunakan dua pendekatan utama dalam sistem rekomendasi yang relevan untuk proyek ini digunakan pendekatan **content-based filtering** dan **collaborative filtering**. **Content-based filtering** menggunakan atribut yang terkandung dalam produk, seperti kategori, nama produk, dan brand/merek untuk menemukan produk yang memiliki kesamaan. Pendekatan ini akan diterapkan dalam proyek ini dengan menganalisis produk berdasarkan karakteristik produk itu sendiri yang serupa dengan apa yang telah diinteraksikan oleh pengguna. Menurut Az Zayyad (2021), dalam penelitiannya menunjukkan bahwa penerapan metode content-based filtering dapat memberikan rekomendasi yang relevan berdasarkan kemiripan konten yang disukai oleh pengguna [1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1). 

Disisi lain, pendekatan **collaborative filtering** merekomendasikan produk berdasarkan pola interaksi dan preferensi pengguna lain yang serupa, seperti rating, pembelian, atau preferensi pengguna lain yang memiliki pola yang serupa. Pendekatan ini akan diterapkan dalam proyek ini dengan mengumpulkan data interaksi pengguna seperti rating produk dan preferensi yang telah dipilih oleh pengguna sebelumnya. Dengan demikian, rekomendasi akan diberikan berdasarkan kesamaan pola preferensi antar pengguna yang memiliki kecenderungan yang mirip, tanpa memerlukan informasi mendalam tentang isi produk. Menurut Dzumiroh (2012), pendekatan collaborative filtering dapat memberikan rekomendasi yang efektif berdasarkan kesamaan preferensi antar pengguna yang mungkin tidak diketahui sebelumnya [2](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542). Dengan mengadopsi algoritma seperti TF-IDF untuk analisis teks dan cosine similarity untuk menghitung kesamaan, sistem ini diharapkan dapat memberikan rekomendasi produk yang relevan, baik berdasarkan atribut produk maupun riwayat interaksi pengguna. Hasil akhirnya adalah platform yang lebih personal dan responsif, yang tidak hanya membantu konsumen dalam memilih produk tetapi juga meningkatkan kepuasan dan loyalitas mereka.

## Business Understanding

### Problem Statements

Berdasarkan uraian yang telah dipaparkan pada latar belakang diatas, maka rumusan masalah yang dapat diambil sebagai berikut:
1. Berdasarkan data mengenai produk kecantikan, bagaimana membangun sistem rekomendasi yang dipersonalisasi untuk konsumen menggunakan teknik pendekatan content-based filtering?
2. Bagaimana memberikan rekomendasi produk kecantikan yang relevan kepada konsumen berdasarkan pola interaksi dan preferensi pengguna lain yang serupa?

### Goals

Berdasarkan rumusan masala yang telah dipaparkan di atas, maka proyek penelitian ini memiliki tujuan sebagai berikut:
1. Menghasilkan sistem rekomendasi berbasis content-based filtering untuk membantu konsumen menemukan produk kecantikan yang sesuai dengan preferensi mereka. Dimana dengan mempertimbangkan atribut produk seperti kategori, merek, dan ulasan guna menghasilkan rekomendasi yang relevan dan dipersonalisasi bagi setiap konsumen.
2. Mengimplementasikan pendekatan collaborative filtering untuk memberikan rekomendasi produk berdasarkan pola interaksi pengguna lain yang memiliki preferensi serupa.
Dengan menganalisis pola seperti pembelian ulang, wishlist, dan ulasan, sistem ini bertujuan untuk meningkatkan pengalaman konsumen dengan menyarankan produk yang relevan dan diminati.

### Solution Statements

Berdasarkan tujuan yang telah dipaparkan diatas, maka proyek ini memiliki solusi yaitu sebagai berikut:
- Menerapkan pendekatan **Content-Based Filtering**: Memanfaatkan atribut produk seperti kategori, merek, dan nama produk untuk menemukan kesamaan antar produk. Algoritma yang digunakan meliputi teknik TF-IDF untuk ekstraksi fitur dari teks dan cosine similarity untuk menghitung kesamaan antara produk. Dengan cara ini, sistem dapat merekomendasikan produk yang memiliki karakteristik serupa dengan produk yang disukai atau telah digunakan oleh konsumen.
- Menerapkan pendekatan **Collaborative Filtering**: Membangun sistem rekomendasi dengan memanfaatkan interaksi pengguna dengan buku (seperti rating atau preferensi eksplisit) untuk menganalisis pola kesamaan antar pengguna dan memberikan rekomendasi buku yang relevan berdasarkan kesamaan preferensi tersebut. Memanfaatkan pola interaksi pengguna seperti pembelian, wishlist, rating, dan ulasan untuk memberikan rekomendasi berdasarkan preferensi pengguna lain yang memiliki pola serupa. Dengan memodelkan hubungan antar pengguna dan produk, serta mengidentifikasi produk yang relevan untuk setiap pengguna. Pendekatan ini sangat berguna dalam memberikan rekomendasi yang tidak secara langsung terlihat melalui atribut produk.


## Data Understanding

| Jenis               | Keterangan                                                                                     |
|---------------------|------------------------------------------------------------------------------------------------|
| **Title**           | Sociolla All Brands Products Catalog                                                           |
| **Source**          | [Kaggle](https://www.kaggle.com/datasets/ibrahimhafizhan/sociolla-all-brands-products-catalog) |
| **License**         | CC0: Public Domain                                                                             |
| **Visibility**      | Publik                                                                                         |  
| **Tags**            | E-commerce, Beauty Products, Skincare, Makeup                                                  |
| **Usability**       | 9.5 (High - Clean dataset with structured product attributes)                                  |
| **File Format**     | CSV                                                                                            |
| **Size**            | 3.48MB                                                                                         |

Dataset yang digunakan dalam proyek ini mencakup informasi mendetail mengenai produk skincare dan kosmetik dari platform Sociolla, dengan total data sebanyak 7637 entri produk unik. Dataset ini berisi berbagai atribut penting, seperti nama produk, kategori, merek, rentang harga, dan metrik interaksi pengguna, seperti rata-rata ulasan, total ulasan, serta data pembelian ulang. Data yang tersedia juga mencakup informasi deskriptif tambahan, seperti tag kategori dan poin kecantikan yang diperoleh dari pembelian. Secara keseluruhan, dataset ini memberikan dasar yang cukup untuk membangun sistem rekomendasi berbasis content-based dan collaborative filtering.

### Variabel pada Sociolla: All Brands Products Catalog Dataset
* **brand\_name**: Merek skincare yang terkait dengan setiap produk.
* **product\_name**: Nama atau judul dari produk skincare.
* **product\_id**: Identifikasi unik yang diberikan untuk setiap produk.
* **beauty\_point\_earned**: Poin kecantikan yang diperoleh melalui pembelian produk.
* **price\_range**: Kategori rentang harga umum dari produk.
* **price\_by\_combinations**: Detail harga spesifik berdasarkan variasi produk.
* **url**: Tautan URL menuju halaman produk di Sociolla.com.
* **active\_date**: Tanggal saat produk mulai aktif di platform.
* **default\_category**: Kategori utama tempat produk diklasifikasikan.
* **categories**: Kategori tambahan atau tag yang terkait dengan produk.
* **rating\_types\_str**: Jenis ulasan yang diterima untuk produk (misalnya, efektivitas, aroma, kemasan).
* **average\_rating**: Rata-rata penilaian keseluruhan yang diberikan oleh pelanggan.
* **total\_reviews**: Jumlah total ulasan yang diterima oleh produk.
* **average\_rating\_by\_types**: Rata-rata penilaian berdasarkan aspek atau jenis tertentu.
* **total\_recommended\_count**: Jumlah total pelanggan yang merekomendasikan produk.
* **total\_repurchase\_maybe\_count**: Jumlah total pelanggan yang mempertimbangkan untuk membeli ulang.
* **total\_repurchase\_no\_count**: Jumlah total pelanggan yang tidak mempertimbangkan untuk membeli ulang.
* **total\_repurchase\_yes\_count**: Jumlah total pelanggan yang berencana untuk membeli ulang.
* **total\_in\_wishlist**: Jumlah total pengguna yang menambahkan produk ke daftar keinginan mereka.

### Informasi Dataset
| #   | Column                        | Non-Null Count | Dtype   |
|-----|-------------------------------|----------------|---------|
| 0   | brand_name                    | 7636           | object  |
| 1   | product_name                  | 7636           | object  |
| 2   | product_id                    | 7636           | int64   |
| 3   | beauty_point_earned           | 7636           | int64   |
| 4   | price_range                   | 7636           | object  |
| 5   | price_by_combinations         | 4087           | object  |
| 6   | url                           | 7636           | object  |
| 7   | active_date                   | 5534           | object  |
| 8   | default_category              | 7636           | object  |
| 9   | categories                    | 7632           | object  |
| 10  | rating_types_str              | 7561           | object  |
| 11  | average_rating                | 7636           | float64 |
| 12  | total_reviews                 | 7636           | int64   |
| 13  | average_rating_by_types       | 5790           | object  |
| 14  | total_recommended_count       | 7636           | int64   |
| 15  | total_repurchase_maybe_count  | 7636           | int64   |
| 16  | total_repurchase_no_count     | 7636           | int64   |
| 17  | total_repurchase_yes_count    | 7636           | int64   |
| 18  | total_in_wishlist             | 7636           | int64   |

### Statistik Deskriptif pada Kolom Numerik

```python 
# Menampilkan statistik deskriptif dari dataset untuk kolom numerik
products.describe()
```
| Statistic    | product_id    | beauty_point_earned | average_rating | total_reviews | total_recommended_count | total_repurchase_maybe_count | total_repurchase_no_count | total_repurchase_yes_count | total_in_wishlist |
|--------------|---------------|---------------------|----------------|---------------|--------------------------|------------------------------|----------------------------|----------------------------|-------------------|
| count        | 7636.000000   | 7636.000000         | 7636.000000    | 7636.000000   | 7636.000000              | 7636.000000                  | 7636.000000                | 7636.000000                | 7636.000000       |
| mean         | 82903.974725  | 37.236773           | 3.517905       | 198.197617    | 186.560503               | 40.603457                    | 15.479963                  | 141.873494                 | 633.016108        |
| std          | 27257.173650  | 46.056962           | 2.000138       | 852.067365    | 803.185318               | 169.473278                   | 79.716058                  | 625.673542                 | 2055.067002       |
| min          | 68.000000     | 0.000000            | 0.000000       | 0.000000      | 0.000000                 | 0.000000                     | 0.000000                   | 0.000000                   | -317.000000       |
| 25%          | 75267.000000  | 10.000000           | 3.910714       | 1.000000      | 1.000000                 | 0.000000                     | 0.000000                   | 0.000000                   | 28.000000         |
| 50%          | 91856.500000  | 20.000000           | 4.576923       | 9.000000      | 9.000000                 | 2.000000                     | 0.000000                   | 6.000000                   | 132.000000        |
| 75%          | 101825.500000 | 50.000000           | 4.738155       | 76.000000     | 71.000000                | 17.000000                    | 6.000000                   | 52.000000                  | 480.000000        |
| max          | 109155.000000 | 610.000000          | 5.000000       | 21536.000000  | 20804.000000             | 5025.000000                  | 2824.000000                | 17653.000000               | 58568.000000      |


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

  

### Statistik Deskriptif pada Kolom Numerik
![Deskripsi Statistik](image/deskripsi-statistik.png)

### Pengecekan Missing Value
Langkah pertama yang perlu dilakukan yaitu memeriksa apakah terdapat data yang hilang (missing values) pada setiap fitur atau tidak. Apabila terdapat nilai yang hilang pada fitur penting, imputasi dilakukan menggunakan median atau mean (untuk fitur numerik). Namun apabila jumlahnya sangat sedikit, baris yang memiliki missing values dapat dihapus tanpa mempengaruhi kualitas dataset. Penanganan missing values diperlukan karena data yang hilang dapat mengurangi kualitas model dan menyebabkan bias dalam prediksi. Dengan imputasi atau penghapusan missing values, dataset menjadi lebih konsisten dan memungkinkan model untuk belajar dengan lebih baik.

Untuk pengecekan missing values, dapat menggunakan kode berikut:

```python
# Menghitung dan menampilkan nilai NaN
missing_df = df.isna().sum()  # Menampilkan jumlah NaN per kolom
print(missing_df)
```

![Missing Value](image/missing-value.png)

Dari informasi diatas dapat disimpulkan bahwa terdapat missing value pada kolom 

### Pengecekan Data Duplikat
Langkah selanjutnya yaitu memeriksa apakah terdapat data duplikat di dalam dataset. Data duplikat bisa saja terjadi akibat kesalahan saat pengumpulan atau proses input data.

Untuk memeriksa data duplikat, dapat menggunakan kode berikut:
```python # Memeriksa duplikasi data 
df_duplicate = df.duplicated().sum()
print(f"Jumlah baris duplikat: {df_duplicate}")
```

![Duplikat Data](image/duplikat-data.png)

Dalam dataset ini, saat dilakukan pengecekan tidak terdapat adanya data duplikat sehingga tidak diperlukan penanganan data duplikat.

### Pengecekan Outlier
Langkah yang selanjutnya yaitu memeriksa apakah terdapat outlier di dalam dataset. Dalam mendeteksi adanya outlier atau nilai ekstrem, digunakan teknik boxplot dan Interquartile Range (IQR) untuk mengidentifikasi data yang berada di luar batas normal distribusi dan akan divisualisasikan ke dalam boxplot. Penanganan outlier perlu dilakukan karena outlier dapat menjadi nilai yang ekstrem dan tidak biasa yang dapat mempengaruhi hasil analisis statistik dan model prediksi. Dengan memperhatikan IQR dan melihat visualisasi boxplot, kita dapat menentukan batas atas dan batas bawah untuk outlier, serta mengambil tindakan yang tepat, seperti menghapus atau mengelola outlier tersebut, agar tidak mempengaruhi hasil analisis secara signifikan.

![Outlier 1](image/outlier-1.png)

Berdasarkan hasil dari perhitungan outlier dengan menggunakan metode Interquartile Range (IQR), terlihat bahwa hanya ada satu kolom yang tidak ditemukan adanya outlier yaitu pada kolom sex. Kolom lainnya (ALB, ALP, ALT, AST, BIL, CHE, CHOL, CREA, GGT, PROT) terlihat adanya outlier sehingga perlu untuk dilakukan penanganan outlier pada tahap selanjutnya.

## Exploratory Data Analysis

### 1. Univariate Analysis
- **Analisis Distribusi Data Kategorikal**
  ![Univariate 1](image/univariate-1.png)

  Dari hasil diatas, dapat dilihat bahwa terdapat lebih banyak individu berjenis kelamin Male (laki-laki) daripada Female (perempuan), dimana jumlah male yang jauh lebih dominan. Sedangkan, distribusi Category menunjukkan bahwa kategori normal (individu yang sehat) jauh lebih dominan dibandingkan dengan kategori abnormal (individu yang memiliki penyakit hati seperti hepatitis, fibrosis, dan sirosis). Hal ini mengindikasikan bahwa jumlah individu yang memiliki penyakit hepatitis, sirosis, dan fibrosis jauh lebih sedikit.
  
- **Analisis Distribusi Data Numerik**
  ![Univariate 2](image/univariate-2.png)

  Berdasarkan grafik histogram dari fitur numerik dalam dataset Hepatitis C, berikut adalah beberapa informasi yang diperoleh:
  
### 3. Multivariate Analysis
- **Analisis Distribusi Fitur-fitur Numerik dengan Data Kategorikal**
  ![Multivariate 1](image/multivariate-1.png)

  Berdasarkan visualisasi diatas, dapat disimpulkan bahwa parameter AST, BIL, dan GGT menjadi yang paling relevan untuk membedakan kategori normal dan abnormal. Parameter seperti ALB, ALP, CHE, CHOL, CREA dan PROT tidak menunjukkan perbedaan mencolok, sehingga kurang relevan sebagai indikator kondisi patologis.
  
- **Kolerasi Antar Fitur Numerik Menggunakan Fungsi pairplot()**
  ![Multivariate 2](image/multivariate-2.png)
  
- **Kolerasi Fitur Numerik dengan Menggunakan Heatmap Correlation Matrix**
  ![Multivariate 3](image/multivariate-3.png)

  Matriks korelasi diatas menunjukkan bahwa terlihat adanya korelasi positif yang kuat yaitu pada 

## Data Preparation
Berikut ini teknik yang digunakan dalam tahap data preparation:

- **Hapus Kolom yang Tidak Diperlukan**

Karena kolom Unnamed:0 tidak diperlukan dalam analisis pada tahap selanjutnya, maka kita perlu drop kolom tersebut dengan menggunakan fungsi drop().

```python # Menghapus kolom yang tidak diperlukan 
df = df.drop(['Unnamed: 0'], axis=1)
```

- **Penanganan Missing Value**

  Berikut kode yang digunakan untuk menangani missing value:
  ```python # Mengisi missing value dengan nilai mean
  def fill_selected_missing_with_mean(df, columns):
      for col in columns:
          df[col] = df[col].fillna(df[col].mean())
      return df
  
  selected_columns = ['ALB', 'ALP', 'ALT', 'CHOL', 'PROT']
  df = fill_selected_missing_with_mean(df, selected_columns)
  print(df.isnull().sum())
  ```

  ![Missing Value 2](image/missing-value2.png)

- **Penanganan Outlier**

  Dalam tahap ini, penanganan outlier dilakukan dengan menggunakan teknik winsorization untuk membatasi nilai ekstrem (outlier) pada fitur numerik yang meliputi data medis. Penerapan ini digunakan untuk meningkatkan stabilitas dan performa model. Winsorization adalah teknik statistik yang digunakan untuk mengurangi pengaruh outlier (nilai ekstrem) dalam data numerik dengan mengganti nilai ekstrem tersebut dengan nilai batas tertentu sehingga mengurangi skewness (kemencengan data).

  Untuk menangani outlier, dapat menggunakan kode berikut:
  ```python # Daftar kolom yang akan diproses
  columns_to_winsorize = ['ALB', 'ALP', 'ALT', 'AST', 'BIL', 'CHE', 'CHOL', 'CREA', 'GGT', 'PROT']
  
  for col in columns_to_winsorize:
      # Hitung batas IQR
      Q1 = df[col].quantile(0.25)
      Q3 = df[col].quantile(0.75)
      IQR = Q3 - Q1
      upper = Q3 + 1.5 * IQR
      lower = Q1 - 1.5 * IQR
  
      # Terapkan winsorization
      df.loc[df[col] > upper, col] = upper  # Ganti outlier atas
      df.loc[df[col] < lower, col] = lower  # Ganti outlier bawah
  
  # Verifikasi
  print("Jumlah outlier yang ditangani per kolom:")
  for col in columns_to_winsorize:
      original_count = len(df) - df[col].between(lower, upper).sum()
      print(f"{col}: {original_count} nilai di luar batas IQR")
  ```
  Dan setelah dilakukan penanganan outlier dengan teknik winsorization, terlihat tiap fitur numerik yang terdapat outlier telah berhasil ditangani:
  
  ![outlier 2](image/outlier-2.png)

- **Encoding Fitur Kategoris**

  Langkah selanjutnya yaitu encoding fitur kategoris, dimana tahapan ini merupakan proses mengubah nilai dalam kolom kategorikal (seperti jenis kelamin dan kategori) menjadi bentuk numerik agar dapat diproses oleh algoritma machine learning.
  
  Berikut kode yang digunakan untuk encoding:
  ```python # Mengubah nilai di DataFrame untuk Gender dan Category menjadi Numerikal
  df['Sex'] = df['Sex'].replace({'m': 0, 'f': 1})
  df['Category'] = df['Category'].replace({'Normal' : 0, 'Abnormal': 1})
  ```
  
   ![encoding](image/encoding.png)
  
- **Data Splitting**

  Dataset akan dibagi menjadi dua set yaitu data training dan testing (dengan proporsi 80:20). Data training akan digunakan untuk melatih model, sedangkan untuk data testing akan digunakan untuk mengevaluasi kinerja dari model yang sudah dibangun. Splitting data ini penting untuk menghindari overfitting dan memastikan model dapat diuji pada data yang tidak digunakan selama proses pelatihan. Splitting data diperlukan agar proses transformasi hanya dilakukan pada data training saja. Data testing harus berperan sebagai data baru yang tidak terpengaruh oleh proses pelatihan, untuk menilai bagaimana model bekerja pada data yang belum pernah dilihat sebelumnya.

  ![Data Splitting](image/data-splitting.png)

  Jumlah data keseluruhan sebanyak 615 data, untuk data pelatihan terdapat sebanyak 492 data, sedangkan untuk data uji sebanyak 123 data.
  
- **Penanganan Imbalance Data**

  Pada tahap EDA (Exploratory Data Analysis), diketahui terdapat ketidakseimbangan kelas pada kolom Category (Normal dan Abnormal). Oleh karena itu, perlu dilakukan penanganan untuk menyeimbangkan kelas menggunakan SMOTE(Synthetic Minority Over-sampling Technique). Penanganan imbalance data dilakukan dengan teknik SMOTE, yaitu metode yang membuat data sintetik pada kelas minoritas agar distribusi kelas menjadi lebih seimbang tanpa sekadar menduplikasi data. Dalam tahap ini, SMOTE diterapkan hanya pada data training dengan target keseimbangan 80%, kemudian divisualisasikan untuk membandingkan distribusi kelas sebelum dan sesudah dilakukan oversampling.

  Berikut ini adalah tampilan dari perbandingan data sebelum dan setelah dilakukan penerapan SMOTE:
  ![Imbalance Data](image/imbalance-data.png)
  Setelah dilakukan SMOTE (Synthetic Minority Oversampling Technique), terlihat bahwa data antara normal dan abnormal menjadi lebih seimbang dibandingkan sebelumnya.

## Modelling



## Evaluation
Pada tahap ini, dilakukan evaluasi terhadap model yang telah dilatih untuk mengukur performa model dengan menggunakan metrik evaluasi. Evaluasi dilakukan berdasarkan empat metrik utama yang meliputi Akurasi, Precision, Recall, dan F1-Score. Metrik tersebut dipilih karena relevansinya dalam konteks masalah klasifikasi biner yang ada pada proyek ini, yaitu memprediksi apakah individu termasuk kedalam kategori menderita Hepatitis C atau tidak. Berikut adalah penjelasan dan hasil dari evaluasi:

### Accuracy
**Accuracy** merupakan metrik yang digunakan untuk mengukur proporsi prediksi yang benar dari seluruh prediksi yang dilakukan. Ini adalah metrik paling umum untuk menilai performa model klasifikasi. 
  
**Formula Metrik**

Accuracy dihitung menggunakan rumus berikut:

![Akurasi](image/akurasi.png)

Keterangan:
- **TP**: True Positive (prediksi positif yang benar)
- **TN**: True Negative (prediksi negatif yang benar)
- **FP**: False Positive (prediksi positif yang salah)
- **FN**: False Negative (prediksi negatif yang salah)
  
**Interpretasi**

Semakin tinggi nilai accuracy (mendekati 1 atau 100%), maka semakin baik performa model secara keseluruhan. Namun, accuracy bisa menyesatkan jika data tidak seimbang (imbalanced), karena model bisa terlihat baik hanya karena memprediksi mayoritas kelas.

### Precision
**Precision** merupakan metrik yang digunakan untuk mengukur berapa banyak dari seluruh prediksi positif yang benar-benar positif. Ini penting ketika biaya dari kesalahan false positive tinggi.

**Formula Metrik**

Precision dihitung menggunakan rumus berikut:

![Precision](image/presisi.png)

Keterangan:
- **TP**: True Positive
- **FP**: False Positive

**Interpretasi**

Nilai precision yang tinggi menunjukkan bahwa model jarang salah mengklasifikasikan data negatif sebagai positif. Precision yang tinggi berarti model dapat mengidentifikasi individu yang benar-benar menderita Hepatitis C dengan baik, menghindari prediksi yang salah terhadap individu yang sehat. Ini sangat penting ketika tujuan adalah meminimalkan false positives, misalnya, untuk menghindari pemberian diagnosis yang salah.

### Recall
**Recall** merupakan metrik untuk mengukur berapa banyak dari seluruh kasus positif yang berhasil terdeteksi dengan benar oleh model. Ini penting ketika biaya dari kesalahan false negative tinggi.

**Formula Metrik**

Recall dihitung menggunakan rumus berikut:

![Recall](image/recall.png)

Keterangan:
- **TP**: True Positive
- **FN**: False Negative
  
**Interpretasi**

Nilai recall yang tinggi berarti model berhasil menangkap sebagian besar data positif, meskipun mungkin menghasilkan false positive lebih banyak. Ini sangat penting dalam diagnosis medis, di mana melewatkan kasus positif bisa berbahaya dan juga lebih penting untuk menangkap semua pasien yang menderita Hepatitis C (mencegah false negatives) daripada menghindari beberapa false positives.

### F1-Score
**F1-Score** merupakan rata-rata harmonis antara precision dan recall, yang digunakan untuk menyeimbangkan kedua metrik ketika penting untuk mempertimbangkan keduanya.

**Formula Metrik**

F1-Score dihitung menggunakan rumus berikut:

![F1-Score](image/f1-score.png)

Keterangan:
- **Precision**: Proporsi prediksi positif yang benar.
- **Recall**: Proporsi kejadian positif yang berhasil terdeteksi.

**Interpretasi**

F1-Score memberikan ukuran keseimbangan antara kesalahan tipe I (false positive) dan tipe II (false negative). Nilai F1 mendekati 1 menunjukkan model yang baik secara keseluruhan, terutama dalam kondisi data tidak seimbang. F1-Score yang baik menunjukkan bahwa model tidak hanya akurat dalam memprediksi penyakit Hepatitis C tetapi juga berhasil mendeteksi sebagian besar individu yang benar-benar menderita Hepatitis C, yang sangat penting dalam konteks medis.

### Metrik MSE
**Mean Squared Error (MSE)** adalah salah satu metrik evaluasi yang digunakan untuk mengukur rata-rata kesalahan kuadrat antara nilai yang diprediksi oleh model dan nilai aktual. MSE sangat umum digunakan dalam permasalahan regresi dan memberikan gambaran seberapa jauh prediksi model menyimpang dari nilai sebenarnya.

**Formula Metrik**

 Metrik MSE dihitung menggunakan rumus berikut:

![Rumus MSE](image/rumus-mse.png)

Keterangan :

![Keterangan MSE](image/ket-mse.png) 

**Interpretasi**

Nilai MSE lebih kecil menunjukkan bahwa prediksi model lebih mendekati nilai aktual. Karena kesalahan dikuadratkan, MSE lebih sensitif terhadap outlier. Artinya, kesalahan besar akan memberikan kontribusi lebih besar terhadap nilai akhir MSE. MSE tidak bisa bernilai negatif, karena hasil kuadrat selalu positif atau nol. Dalam konteks evaluasi model, semakin rendah nilai MSE, maka semakin baik kinerja model dalam melakukan prediksi.


## Result
### Analisa Hasil Metrik Evaluasi
Setelah melakukan training model dan evaluasi model, hasil yang didapatkan menunjukkan performa model 

![Evaluasi 2](image/metrik-evaluasi2.png)

### Predict

![Prediksi](image/prediksi.png)

Untuk hasil prediksi, terlihat nilai terdekat dari nilai sesungguhnya (0) adalah Random Forest dan KNN sebesar 0, dan yang paling jauh dari nilai sesungguhnya adalah Decison Tree dan Logistic Regression sebesar 1. Sehingga tetap model Random Forest yang paling unggul dan dapat dipilih untuk pemodelan yang terbaik dalam proyek ini berdasarkan hasil evaluasi menggunakan metrik evaluasi yang telah dilakukan pada tahap sebelumnya.

### Evaluasi Terhadap Business Understanding
1. Model machine learning yang dibangun berhasil 


## Kesimpulan
Proyek ini berhasil menjawab problem statement dan mencapai goals yang telah ditentukan. Pengembangan model machine learning untuk 

## Referensi
[1] T. Jimmy, and P. Valentino, "Penentuan Jalur Diagnostik Penyakit Berbasis Konsep Pembelajaran Mesin: Studi kasus Penyakit Hepatitis C," *Journal of Applied Computer Science and Technology*, Vol. 4, No. 2, 2023, DOI: https://doi.org/10.52158/jacost.v4i2.556.
[2] K. S. Putri, "Epidemiologi Hepatitis C," Alomedika, Accessed: May. 19, 2025 [Online], Available: https://www.alomedika.com/penyakit/gastroenterologi/hepatitis-c/epidemiologi.
[3] The World Health Organization, "Laporan WHO Mengungkapkan Peningkatan Kematian Global Akibat Virus Hepatitis," Accessed: May. 19, 2025 [Online], Available: https://pedulihatibangsa.id/2024/06/08/laporan-who-mengungkapkan-peningkatan-kematian-global-akibat-virus-hepatitis/.
[4] S. Nabilah, G. R. Nur, "Analisis SMOTE Pada Klasifikasi Hepatitis C Berbasis Random Forest dan Naïve Bayes,"  *Journal of Information Technology and Computer Science*, Vol. 8, No. 1, 2023, Hal. 33 – 40, DOI: http://publishing-widyagama.ac.id/ejournal-v2/index.php/jointecs.
[5] R. Ahmad, "Penerapan Random Forest Untuk Prediksi Virus Hepatitis C," *Journal of Information Systems and Technology*, Vol. 1, No. 1, 2024, DOI: https://ejournal.katersipublisher.com/index.php/FIMERKOM/article/view/48/15.


## Hasil Review Proyek

![Hasil Review](image/hasil-review.jpg)
