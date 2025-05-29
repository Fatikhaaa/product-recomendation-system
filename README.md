# Laporan Proyek Machine Learning - Fatikha Hudi Aryani

## Project Overview

Saat ini, industri kosmetik dan kecantikan mengalami perkembangan pesat seiring meningkatnya kebutuhan konsumen akan produk kecantikan yang beragam dan berkualitas. Platform e-commerce seperti Sociolla hadir sebagai solusi untuk memudahkan konsumen menemukan dan membeli produk kecantikan tanpa harus berbelanja secara langsung di toko fisik. Namun, dengan ribuan produk yang tersedia di platform ini, konsumen sering kali kesulitan menentukan pilihan yang paling sesuai dengan kebutuhan dan preferensi mereka. Jika dibiarkan, hal ini tidak hanya dapat menurunkan pengalaman pengguna tetapi juga mengurangi peluang penjualan karena konsumen mungkin akan meninggalkan platform tanpa melakukan pembelian. Oleh karena itu, sistem rekomendasi menjadi solusi penting untuk mengatasi tantangan ini dengan membantu konsumen menemukan produk yang relevan secara cepat dan efisien sesuai dengan kebutuhan dan preferensi mereka.

Permasalahan utama yang perlu diselesaikan yaitu bagaimana cara menyaring informasi yang sangat banyak dan beragam untuk memberikan rekomendasi yang relevan. Maka dari itu, dengan menggunakan dua pendekatan utama dalam sistem rekomendasi yang relevan untuk proyek ini digunakan pendekatan **content-based filtering** dan **collaborative filtering**. **Content-based filtering** menggunakan atribut yang terkandung dalam produk, seperti kategori, nama produk, dan brand/merek untuk menemukan produk yang memiliki kesamaan. Pendekatan ini akan diterapkan dalam proyek ini dengan menganalisis produk berdasarkan karakteristik produk itu sendiri yang serupa dengan apa yang telah diinteraksikan oleh pengguna. Menurut Az Zayyad (2021), dalam penelitiannya menunjukkan bahwa penerapan metode content-based filtering dapat memberikan rekomendasi yang relevan berdasarkan kemiripan konten yang disukai oleh pengguna [[1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1)]. 

Disisi lain, pendekatan **collaborative filtering** merekomendasikan produk berdasarkan pola interaksi dan preferensi pengguna lain yang serupa, seperti rating, pembelian, atau preferensi pengguna lain yang memiliki pola yang serupa. Pendekatan ini akan diterapkan dalam proyek ini dengan mengumpulkan data interaksi pengguna seperti rating produk dan preferensi yang telah dipilih oleh pengguna sebelumnya. Dengan demikian, rekomendasi akan diberikan berdasarkan kesamaan pola preferensi antar pengguna yang memiliki kecenderungan yang mirip, tanpa memerlukan informasi mendalam tentang isi produk. Menurut Dzumiroh (2012), pendekatan collaborative filtering dapat memberikan rekomendasi yang efektif berdasarkan kesamaan preferensi antar pengguna yang mungkin tidak diketahui sebelumnya [[2](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542)]. Dengan mengadopsi algoritma seperti TF-IDF untuk analisis teks dan cosine similarity untuk menghitung kesamaan, sistem ini diharapkan dapat memberikan rekomendasi produk yang relevan, baik berdasarkan atribut produk maupun riwayat interaksi pengguna. Hasil akhirnya adalah platform yang lebih personal dan responsif, yang tidak hanya membantu konsumen dalam memilih produk tetapi juga meningkatkan kepuasan dan loyalitas mereka.

## Business Understanding

### Problem Statements

Berdasarkan uraian yang telah dipaparkan pada latar belakang diatas, maka rumusan masalah yang dapat diambil sebagai berikut:
1. Berdasarkan data mengenai produk kecantikan, bagaimana membangun sistem rekomendasi yang dipersonalisasi untuk konsumen menggunakan teknik pendekatan content-based filtering?
2. Bagaimana memberikan rekomendasi produk kecantikan yang relevan kepada konsumen berdasarkan pola interaksi dan preferensi pengguna lain yang serupa?

### Goals

Berdasarkan rumusan masalah yang telah dipaparkan di atas, maka proyek penelitian ini memiliki tujuan sebagai berikut:
1. Menghasilkan sistem rekomendasi berbasis content-based filtering untuk membantu konsumen menemukan produk kecantikan yang sesuai dengan preferensi mereka. Dimana dengan mempertimbangkan atribut produk seperti kategori, merek, dan nama produk guna menghasilkan rekomendasi yang relevan dan dipersonalisasi bagi setiap konsumen.
2. Mengimplementasikan pendekatan collaborative filtering untuk memberikan rekomendasi produk berdasarkan pola interaksi pengguna lain yang memiliki preferensi serupa.
Dengan menganalisis pola seperti rating, pembelian ulang, wishlist, dan ulasan, sistem ini bertujuan untuk meningkatkan pengalaman konsumen dengan menyarankan produk yang relevan dan diminati.

### Solution Statements

Berdasarkan tujuan yang telah dipaparkan diatas, maka proyek ini memiliki solusi yaitu sebagai berikut:
- Menerapkan pendekatan **Content-Based Filtering**: Memanfaatkan atribut produk seperti kategori, merek, dan nama produk untuk menemukan kesamaan antar produk. Algoritma yang digunakan meliputi teknik TF-IDF untuk ekstraksi fitur dari teks dan cosine similarity untuk menghitung kesamaan antara produk. Dengan cara ini, sistem dapat merekomendasikan produk yang memiliki karakteristik serupa dengan produk yang disukai atau telah digunakan oleh konsumen.
- Menerapkan pendekatan **Collaborative Filtering**: Membangun sistem rekomendasi dengan memanfaatkan interaksi pengguna dengan produk (seperti rating atau preferensi eksplisit) untuk menganalisis pola kesamaan antar pengguna dan memberikan rekomendasi buku yang relevan berdasarkan kesamaan preferensi tersebut. Memanfaatkan pola interaksi pengguna seperti pembelian, wishlist, rating, dan ulasan untuk memberikan rekomendasi berdasarkan preferensi pengguna lain yang memiliki pola serupa. Dengan memodelkan hubungan antar pengguna dan produk, serta mengidentifikasi produk yang relevan untuk setiap pengguna. Pendekatan ini sangat berguna dalam memberikan rekomendasi yang tidak secara langsung terlihat melalui atribut produk.


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

Berikut ini kode yang digunakan untuk menghitung jumlah row dan column:

```python 
# Menampilkan jumlah row dan column (ukuran shape)
products.shape
```

![image](https://github.com/user-attachments/assets/20c83898-aeab-496b-b1d9-e8c7a70f0357)

Berdasarkan dari informasi diatas, dapat diketahui bahwa dataset terdiri dari 7636 records data dimana didalamnya berisi 19 fitur.

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

### Pengecekan Missing Value

Langkah selanjutnya adalah memeriksa apakah terdapat data yang hilang (missing values) pada setiap fitur. Untuk pengecekan missing values, berikut kode yang digunakan:

```python # Memeriksa missing value
products.isnull().sum()
```

![image](https://github.com/user-attachments/assets/0eaf4898-a2a8-4580-91b7-4e761eab0ebd)

Dari informasi diatas dapat disimpulkan bahwa terdapat missing value pada kolom price_by_combinations, activate_date, categories, rating_types_str, dan average_rating_by_types. Dimana jumlah missing value pada kolom price_by_combinations sebanyak	3549 entri yang kosong, kolom active_date memiliki 2102 entri yang kosong, kolom categories memiliki 4 entri yang kosong, rating_types_str memiliki 75 entri yang kosong, dan kolom average_rating_by_types	memiliki 1846 entri yang kosong. Sehingga untuk tahap selanjutnya perlu dilakukan pananganan missing value, baik dengan imputasi atau penghapusan data, terutama apabila kolom-kolom tersebut berperan penting dalam proses rekomendasi berbasis konten. Selain itu, penting untuk memeriksa kolom mana saja yang kosong untuk mempermudah proses imputasi, agar kita dapat memilih metode imputasi yang tepat. Namun, karena kolom-kolom tersebut tidak relevan untuk sistem rekomendasi berbasis content-based filtering dan collaborative filtering, maka kolom-kolom ini akan dihapus dari dataset sehingga tidak perlu dilakukan penanganan.

### Pengecekan Data Duplikat

Langkah selanjutnya yaitu memeriksa apakah terdapat data duplikat di dalam dataset. Data duplikat bisa saja terjadi akibat kesalahan saat pengumpulan atau proses input data.
Untuk memeriksa data duplikat, dapat menggunakan kode berikut:

```python # Memeriksa data duplikat
product_duplicate = products.duplicated().sum()
print(f"Jumlah baris duplikat: {product_duplicate}")
```

![image](https://github.com/user-attachments/assets/bed750c9-dc56-49eb-9dbe-a10924732402)

Terlihat dari outputnya menampilkan bahwa tidak ada data duplikat, sehingga tidak perlu dilakukan penanganan data duplikat untuk tahapan selanjutnya.


## Exploratory Data Analysis (EDA)
Selanjutnya, akan dilakukan proses analisis data dengan teknik Univariate Analysis dan Multivariate Analysis.

### 1. Univariate Analysis

- **Analisis Jumlah Nilai Unik pada Dataframe**
  
  ![image](https://github.com/user-attachments/assets/b7b5c7f1-38c6-4373-b54a-a9ee8eeb9aed)

  Berdasarkan output yang dihasilkan dari analisis jumlah nilai unik pada kolom product_id, brand_mname, average_rating, dan default_category dengan fungsi unique(), dapat diketahui jika dataset terdiri dari 7636 nama produk yang berbeda, 319 nama brand yang berbeda, 3187 nilai rating yang berbeda, dan 195 kategori produk yang berbeda.
  
- **Analisis Distribusi Rating Produk**

  ![image](https://github.com/user-attachments/assets/c6a2695c-913a-4766-a267-cb8e7de5ff82)

  Berdasarkan analisis distribusi rating produk, menunjukkan bahwa sebagian besar produk memiliki rating tinggi (4-5), menunjukkan kepuasan pelanggan yang baik. Hanya sedikit produk yang mendapat rating rendah (0-3), yang mungkin memerlukan evaluasi lebih lanjut. Distribusi ini mengindikasikan bahwa sebagian besar produk diterima dengan baik oleh pelanggan.

- **Analisis Kategori Produk**

  ![image](https://github.com/user-attachments/assets/a1a85235-a11c-4ba3-bbda-9d4da1aa64b7)

  Berdasarkan analisa kategori produk, terlihat bahwa daftar kategori produk yang paling dominan untuk rekomendasi Content-Based Filtering menunjukkan seperti yang ada di visualisasi barplot diatas meliputi : Skin Care Set, Face Serum, Face Cream & Lotion, Sheet Mask, Face Wash, Toner, Body Lotion/Body Serum, Sunscreen, False Eyelash, dan Body Wash. Dimana 3 top produk teratas menunjukkan produk pada kategori Skin Care Set, Face Serum, Face Cream & Lotion dengan jumlah masing-masing kategori sebanyak lebih dari 400 produk. Kategori produk yang dominan, seperti Skin Care Set, Face Serum, dan Face Cream & Lotion, mencerminkan tingginya variasi produk dalam kategori tersebut. Dalam content-based filtering, keberagaman ini memungkinkan sistem untuk menemukan produk serupa berdasarkan fitur deskriptif, seperti nama produk, kategori, merek, dll. Misalnya, pengguna yang tertarik pada produk Face Serum tertentu cenderung menerima rekomendasi produk lain dalam kategori yang sama atau yang memiliki karakteristik serupa. Di sisi lain, dalam collaborative filtering, popularitas kategori ini tercermin dari data interaksi pengguna, seperti ulasan, rating, atau pembelian. Produk dalam kategori yang lebih populer cenderung lebih sering direkomendasikan karena tingkat interaksi yang lebih tinggi di antara pengguna yang memiliki preferensi serupa.

- **Analisis Sentimen dari Rekomendasi & Repurchase**

  ![image](https://github.com/user-attachments/assets/cb634c65-4ba7-4ba0-b5c8-f86cba92b21a)

  Berdasarkan analisis sentimen dari rekomedasi dan repurchase, terlihat bahwa produk yang direkomendasikan dan dibeli ulang oleh pelanggan menunjukkan total yang paling tinggi dibandingkan jumlah produk yang mungkin akan dibeli ulang dan jumlah produk yang tidak akan dibeli lagi. Tingginya jumlah produk yang direkomendasikan dan dibeli ulang menunjukkan bahwa produk-produk ini memiliki kualitas dan kepuasan pelanggan yang tinggi. Dalam content-based filtering, hal ini berarti bahwa fitur deskriptif seperti kategori, merek, dan nama produk yang sering dibeli ulang dapat digunakan untuk merekomendasikan produk dengan karakteristik serupa kepada pelanggan baru. Di sisi lain, dalam collaborative filtering, pola interaksi dari pelanggan yang sering membeli ulang produk tertentu dapat menjadi dasar untuk merekomendasikan produk-produk yang sama atau produk lain yang memiliki pola pembelian serupa di antara pelanggan dengan preferensi yang mirip.

- **Analisis Brand Populer**

  ![image](https://github.com/user-attachments/assets/1db604dc-70c9-470a-867e-725a275243c7)

  Berdasarkan hasil visualisasi diatas, dapat diketahui bahwa daftar nama brand yang paling banyak mendapatkan rating tertinggi (>4.5) diantaranya meliputi papa-recipe, celove, nona-woman, skindoze, itsy-nail, murad, memoir, moonshot, lamica, dan banobagi. Visualisasi brand yang mendapatkan rating tertinggi menunjukkan bahwa merek-merek (brand) tersebut tidak hanya mampu memenuhi ekspektasi pelanggan tetapi juga berhasil membangun loyalitas konsumen melalui kualitas produk yang konsisten. Rating tertinggi (>4.5) pada suatu brand mencerminkan tingginya tingkat kepuasan pelanggan, baik dari segi efektivitas produk, hingga pengalaman pengguna secara keseluruhan. Hal ini mengindikasikan bahwa brand-brand tersebut memiliki daya tarik yang kuat di pasar dan sering kali menjadi pilihan utama bagi konsumen, yang pada gilirannya dapat meningkatkan peluang mereka untuk direkomendasikan dalam sistem rekomendasi berbasis rating atau popularitas.


### 2. Multivariate Analysis

- **Korelasi antar Fitur Numerik dengan Menggunakan Heatmap Correlation**

  ![image](https://github.com/user-attachments/assets/e9d09b0a-2f7c-4124-957a-0c12d1a10b1b)

  Berdasarkan heatmap correlation, dapat diketahui bahwa:
  
  **1. Korelasi Tinggi pada Fitur Tertentu**:
  
     - Terdapat korelasi yang sangat tinggi antara total_recommended_count dan **total_reviews** (korelasi positif sangat kuat dengan nilai 1), ini menunjukkan bahwa produk yang paling banyak direkomendasikan cenderung memiliki jumlah review yang tinggi juga.
     - Terdapat korelasi yang sangat tinggi antara total_repurchase_yes_count dan total_recommended_count (nilai korelasi mendekati 1). Hal ini menunjukkan bahwa produk yang sering direkomendasikan cenderung lebih banyak dibeli kembali oleh pengguna. Selain itu, Korelasi tinggi juga terlihat antara total_reviews dan variabel terkait repurchase behavior (yes/maybe/no count), yang menunjukkan bahwa jumlah ulasan dapat menjadi indikator penting untuk perilaku pembelian ulang.
       
  **2. Korelasi Lemah pada Beberapa Fitur**:
  
     - Fitur seperti beauty_point_earned dan average_rating memiliki korelasi lemah terhadap sebagian besar fitur lain. Sehingga untuk beauty_point_earned akan dilakukan drop kolom. Sedangkan, untuk fitur average_rating tidak dilakukan drop kolom karena meskipun korelasinya lemah, kolom ini tetap penting untuk membangun sistem rekomendasi, terutama dalam pendekatan Content-based Filtering, yang memerlukan atribut produk untuk merepresentasikan karakteristiknya.
       
  **3. Drop Kolom yang Tidak Berguna**:
  
     - Proses pembersihan data tetap dilakukan untuk memastikan efisiensi dan efektivitas dalam membangun sistem rekomendasi. Hanya fitur yang tidak berkontribusi terhadap pendekatan Content-based Filtering atau Collaborative Filtering yang akan dihapus, sementara fitur lainnya tetap dipertahankan karena relevansinya terhadap problem statement dan tujuan proyek.
     - Kolom-kolom yang tidak relevan dengan pendekatan Content-based Filtering (berbasis atribut produk) atau Collaborative Filtering (berbasis interaksi pengguna) akan dihapus, seperti beauty_point_earned, url, price_by_combinations, active_date, categories, average_rating_by_types dan rating_types_str dapat di-drop karena tidak berkontribusi langsung pada pembentukan rekomendasi.
     - Kolom yang tetap dipertahankan adalah yang berkaitan dengan atribut produk (brand_name, product_id, product_name, price_range,	default_category) atau interaksi pengguna (total_reviews, total_recommended_count, total_repurchase_maybe_count,	total_repurchase_no_count,	total_repurchase_yes_count	dan total_in_wishlist).
  

## Data Preparation
Berikut ini teknik yang digunakan dalam tahap data preparation:

- **Hapus Kolom yang Tidak Diperlukan (Dropping Columns)**

  ```python # Drop kolom yang tidak terlalu berpengaruh
  products.drop(['beauty_point_earned'], inplace=True, axis=1)
  products.drop(['price_by_combinations'], inplace=True, axis=1)
  products.drop(['url'], inplace=True, axis=1)
  products.drop(['active_date'], inplace=True, axis=1)
  products.drop(['categories'], inplace=True, axis=1)
  products.drop(['rating_types_str'], inplace=True, axis=1)
  products.drop(['average_rating_by_types'], inplace=True, axis=1)
  products
  ```

  Berikut ini detail mengenai kolom-kolom yang akan di-drop karena tidak terlalu berpengaruh dalam membangun sistem rekomendasi berbasis Content-based Filtering (berdasarkan atribut produk) dan Collaborative Filtering (berdasarkan interaksi pengguna) yaitu:
  
  - *beauty_point_earned* : kolom ini terkait dengan program loyalitas atau poin yang diperoleh pengguna, yang tidak secara langsung berkontribusi pada algoritma Content-based (berdasarkan atribut produk) atau Collaborative Filtering (berdasarkan interaksi pengguna).
  - *price_by_combinations*: meskipun harga bisa menjadi faktor dalam keputusan pembelian, dalam konteks dasar Content-based dan Collaborative Filtering, detail harga spesifik atau range harga biasanya tidak menjadi fitur utama. Rekomendasi lebih berfokus pada kesamaan produk atau preferensi pengguna.
  - *url*: URL produk tidak diperlukan untuk membangun model rekomendasi dan ini lebih relevan untuk display atau navigasi setelah rekomendasi dibuat.
  - *categories*: kolom ini memiliki kemiripan dengan kolom default_category yang secara tidak langsung juga terwakili dengan kolom tersebut, sehingga tidak terlalu berpengaruh apabila didrop.
  - *active_date*: tanggal aktif produk mungkin berguna untuk analisis tren atau produk baru, tetapi tidak esensial untuk model rekomendasi dasar yang berfokus pada kesamaan atau interaksi.
  - *rating_types_str*: karena sudah ada average_rating dan total_reviews, detail rating types dalam bentuk string tidak diperlukan. Karena kolom tersebut tidak diperlukan dalam analisis pada tahap selanjutnya, maka kita perlu lakukan drop kolom.
  - *average_rating_by_types*: karena sudah ada average_rating, detail rating types dalam bentuk string tidak diperlukan. Selain itu, terlihat pada pemeriksaan missing value pada tahap data understanding menunjukkan kolom ini memiliki banyak sekali nilai yang kosong sehingga apabila tidak didrop dapat berpengaruh dalam pemodelan. Dan karena kolom tersebut tidak diperlukan dalam analisis pada tahap selanjutnya, maka kita perlu lakukan drop kolom.
  
- **Penanganan Missing Value**

  ![image](https://github.com/user-attachments/assets/20364d0d-7554-47fc-b191-862902933aa9)

  Kolom-kolom yang terdeteksi memiliki missing value, seperti **price\_by\_combinations**, **active\_date**, **categories**, **rating\_types\_str**, dan **average\_rating\_by\_types**, ternyata tidak terlalu relevan atau berguna untuk analisis dan pemodelan pada tahap selanjutnya. Oleh karena itu, kolom-kolom tersebut telah dilakukan proses dropping pada tahap sebelumnya dan sekaligus sebagai langkah penanganan missing value. Dengan demikian, dataset yang digunakan saat ini sudah bersih dari missing value, sehingga dapat lebih optimal dalam mendukung analisis dan pemodelan sistem rekomendasi.
  
- **Memisahkan Nilai Kolom Name Brand**

  Selanjutnya, yaitu memisahkan nilai kolom nama brand. Dapat diketahui jika, kolom 'brand_name', tergabung dari dua values, yaitu nama brand, dan id brand, untuk itu dilakukan pemisahan dengan fungsi split(). Pemecahan kolom **brand\_name** menjadi dua kolom terpisah, yaitu **brand\_name** dan **brand\_id**, penting dilakukan untuk memastikan kemudahan analisis data dan pemodelan sistem rekomendasi. Dengan memisahkan kedua nilai tersebut, proses analisis dapat dilakukan secara lebih terstruktur, memungkinkan identifikasi hubungan antara nama brand dengan produk secara langsung, sekaligus mempermudah agregasi data berdasarkan ID brand. Selain itu, pemisahan ini juga akan meningkatkan fleksibilitas dalam pengolahan data, seperti pengelompokan atau pemetaan data berdasarkan brand tertentu, tanpa harus melakukan parsing tambahan setiap kali diperlukan.

  | brand_name_id | brand_name    | product_name                     | product_id | price_range                | default_category      | average_rating | total_reviews | total_recommended_count | total_repurchase_maybe_count | total_repurchase_no_count | total_repurchase_yes_count | total_in_wishlist |
  |---------------|---------------|----------------------------------|------------|----------------------------|-----------------------|----------------|---------------|--------------------------|-----------------------------|---------------------------|----------------------------|-------------------|
  | 796           | 3ce           | MULTI EYE COLOR PALETTE         | 97802      | Rp 555.000 - Rp 687.000   | Eyeshadow            | 4.920000       | 5             | 5                        | 0                           | 0                         | 5                          | 717               |
  | 796           | 3ce           | VELVET LIP TINT                 | 97810      | Rp 264.000                | Lip Cream            | 4.576190       | 42            | 42                       | 10                          | 2                         | 30                         | 682               |
  | 796           | 3ce           | LIP COLOR                       | 97822      | Rp 317.000                | Lipstick             | 0.000000       | 0             | 0                        | 0                           | 0                         | 0                          | 173               |
  | 796           | 3ce           | MINI MULTI EYE COLOR PALETTE    | 97833      | Rp 423.000                | Eyeshadow            | 4.883333       | 6             | 12                       | 1                           | 0                         | 11                         | 257               |
  | 796           | 3ce           | FACE BLUSH                      | 97801      | Rp 300.000                | Blush                | 4.858824       | 13            | 17                       | 2                           | 0                         | 15                         | 387               |
  | ...           | ...           | ...                              | ...        | ...                        | ...                  | ...            | ...           | ...                      | ...                         | ...                       | ...                        | ...               |
  | 273           | yves-rocher   | Ambre Noir Eau De Toilette      | 2158       | Rp 659.000                | Eau De Toilette      | 4.476190       | 7             | 6                        | 1                           | 2                         | 4                          | 355               |
  | 273           | yves-rocher   | Soin Stimulating Conditioner    | 64174      | Rp 199.000                | Conditioner          | 4.638889       | 9             | 7                        | 1                           | 2                         | 6                          | 122               |
  | 273           | yves-rocher   | Repair Hair Mask                | 36357      | Rp 289.000                | Hair Mask            | 4.750000       | 5             | 5                        | 1                           | 0                         | 4                          | 58                |
  | 273           | yves-rocher   | Hand Cream Olive Petitgrain     | 36404      | Rp 109.000                | Hand & Foot Cream    | 4.968750       | 8             | 8                        | 2                           | 0                         | 6                          | 117               |
  | 273           | yves-rocher   | Color Mask                      | 64153      | Rp 289.000                | Hair Mask            | 4.500000       | 2             | 2                        | 1                           | 0                         | 1                          | 35                |

  
### Preparation Content-Based Filtering

- **Konversi Data Series dalam Bentuk List**
  
  Selanjutnya yaitu mengonversi data series menjadi list, yang akan memudahkan dalam membuat dataframe baru atau mengolah data lebih lanjut. Dalam hal ini, akan mengonversi kolom-kolom seperti brand_name, product_name, dan default_category ke dalam list.
  
  ```python # Mengonversi data series ‘brand_name’ menjadi dalam bentuk list
  brand_name = products['brand_name'].tolist()
  
  # Mengonversi data series ‘product_name’ menjadi dalam bentuk list
  product_name = products['product_name'].tolist()
  
  # Mengonversi data series ‘default_category’ menjadi dalam bentuk list
  default_category = products['default_category'].tolist()
  
  print(len(brand_name))
  print(len(product_name))
  print(len(default_category))
  ```

  Tahapan di atas dilakukan untuk mengonversi kolom-kolom data series dari dataset ke dalam bentuk list, yaitu kolom **`brand_name`**, **`product_name`**, dan **`default_category`**. Langkah ini bertujuan untuk mempermudah proses manipulasi data pada tahapan selanjutnya, seperti membuat dataframe baru, mengolah data lebih lanjut, atau melakukan operasi khusus pada elemen-elemen dalam setiap kolom. Dengan mengonversi data series menjadi list, kita dapat:
  
  1. **Fleksibilitas Pengolahan Data**: List menyediakan fleksibilitas yang lebih besar dibandingkan dengan data series dalam hal iterasi dan penerapan fungsi Python biasa.
  2. **Kompatibilitas dengan Fungsi dan Algoritma Lain**: Banyak algoritma atau fungsi dalam Python (terutama yang tidak menggunakan Pandas) lebih kompatibel dengan struktur list daripada data series.
  3. **Mempermudah Transformasi Data**: Untuk langkah-langkah seperti tokenisasi, pembuatan bag-of-words, atau proses lainnya yang memerlukan iterasi per elemen, list mempermudah implementasinya.
  Langkah terakhir pada kode tersebut mencetak jumlah elemen dalam setiap list untuk memastikan bahwa semua kolom yang dikonversi memiliki panjang yang sama, sehingga dapat meminimalkan risiko ketidaksesuaian data selama proses pengolahan selanjutnya.

- **Membuat Dataframe baru**
  
  Tahap berikutnya yaitu membuat dictionary untuk menentukan pasangan key-value pada data brand_name, product_name dan default_category yang telah disiapkan pada tahap sebelumnya. Dimana tahapan ini untuk menggabungkan data brand_name, product_name dan default_category menjadi satu DataFrame baru yang siap digunakan untuk model sistem rekomendasi berbasis konten. Kode yang digunakan sebagai berikut:

  ```python # Membuat dictionary untuk data ‘brand_name’, ‘product_name’, dan ‘default_category’
  product_data = pd.DataFrame({
      'brand_name': brand_name,
      'product_name': product_name,
      'default_category': default_category
  })
  
  product_data.head()
  ```
  
  ![image](https://github.com/user-attachments/assets/1f4b022d-aa05-4e41-8570-347665a9cfef)

  Pengecekan data duplikat pada dataframe product_data dengan menggunakan kode berikut:
  ```python # Menampilkan duplikat data
  product_duplicate = product_data.duplicated().sum()
  print(f"Jumlah baris duplikat: {product_duplicate}")
  ```

  ![image](https://github.com/user-attachments/assets/a937b0f3-4b83-453a-9ac9-bf8a7693919d)

  Selanjutnya, dilakukan penghapusan duplikasi pada DataFrame product_data dengan fokus pada kolom 'brand_name'.

  ```python product_data = product_data.drop_duplicates(subset=['brand_name'])```

  ![image](https://github.com/user-attachments/assets/322355da-5cea-4e55-a4cb-67d5b3b78593)

  Terlihat bahwa data duplikasi telah berhasil ditangani, maka bisa dilanjutkan untuk tahap selanjutnya.
  
  
- **TF-IDF Vectorizer**

  Pada langkah ini, dimana akan menggunakan TF-IDF Vectorizer untuk mendapatkan representasi fitur penting dari setiap kategori produk. Dimana disini akan fokus pada kolom default_category.

  ```python # Inisialisasi TfidfVectorizer
  tf = TfidfVectorizer()
  
  # Melakukan perhitungan idf pada data 'default_category'
  tf.fit(product_data['default_category'])
  
  # Menampilkan fitur nama dari hasil perhitungan tf-idf
  tf.get_feature_names_out()
  ```

  Setelah menghitung IDF, selanjutnya dengan melakukan transformasi untuk menghasilkan matriks TF-IDF yang menggambarkan hubungan antara setiap kategori produk.

  ```python # Melakukan transformasi data 'default_category' menjadi matriks tf-idf
  tfidf_matrix = tf.fit_transform(product_data['default_category'])
  
  # Melihat ukuran matriks tf-idf
  tfidf_matrix.shape 
  ```

  Kemudian untuk menghasilkan vektor tf-idf dalam bentuk matriks, gunakan fungsi todense().

  ```python # Mengubah vektor tf-idf dalam bentuk matriks dengan fungsi todense()
  tfidf_matrix.todense()
  ```

  ![image](https://github.com/user-attachments/assets/46141bfb-56d4-4cfb-a429-98487fe53b50)

  Tahapan TF-IDF ini harus dilakukan untuk mengubah data teks menjadi format numerik yang dapat diproses oleh algoritma, menangkap pentingnya kata kunci dengan memberikan bobot lebih tinggi pada kata-kata spesifik yang deskriptif, serta menjadi dasar untuk perhitungan kemiripan konten antar produk menggunakan metrik seperti cosine similarity. Dengan demikian, TF-IDF memungkinkan sistem untuk secara objektif mengukur kemiripan konten produk dan merekomendasikan produk berdasarkan relevansinya.

### Persiapan Collaborative Filtering
- **Encoding Data**
  
  Tahapan encoding data bertujuan untuk mengubah nilai kategoris pada kolom **`brand_name_id`** menjadi representasi numerik yang unik. Langkah ini dimulai dengan mengambil nilai unik dari kolom tersebut menggunakan fungsi **`unique()`**, kemudian membuat mapping dua arah: dari **`brand_name_id`** ke angka unik (**`brand_to_brand_encoded`**) dan sebaliknya (**`brand_encoded_to_brand`**). Proses encoding ini penting untuk memastikan kompatibilitas data dengan algoritma machine learning yang umumnya bekerja dengan data numerik. Selain itu, representasi numerik mempermudah pengolahan data, mempercepat komputasi, dan memungkinkan interpretasi hasil model dengan mudah melalui mapping balik ke nilai kategoris asli. Berikut adalah kode yang digunakan:

  ```python # Mengubah brand_name_id menjadi list tanpa nilai yang sama
  brand_name_ids = df['brand_name_id'].unique().tolist()
  print('list brand_name_id: ', brand_name_ids)
  
  # Melakukan encoding brand_name_id
  brand_to_brand_encoded = {x: i for i, x in enumerate(brand_name_ids)}
  print('encoded brand_name_id : ', brand_to_brand_encoded)
  
  # Melakukan proses encoding angka ke brand_name_ids
  brand_encoded_to_brand = {i: x for i, x in enumerate(brand_name_ids)}
  print('encoded angka ke brand_name_id: ', brand_encoded_to_brand)
  ```
  
- **Memetakan brand_name_id dan product_id ke Dataframe yang Berkaitan**
  
  Selanjutnya, dilakukan pemetaan 'brand_name_id' dan 'product_id' ke kolom baru 'brand' dan 'product' dalam DataFrame. Kolom 'brand' dibuat dengan memetakan setiap 'brand_name_id' asli ke representasi integer yang telah di-encode menggunakan kamus brand_to_brand_encoded, sementara kolom 'product' dihasilkan dengan memetakan 'product_id' asli ke integer yang di-encode menggunakan kamus product_to_product_encoded. Berikut kode yang digunakan dalam proses ini:
  
  ```python # Mapping brand_name_id ke dataframe user
  df['brand'] = df['brand_name_id'].map(brand_to_brand_encoded)
  
  # Mapping product_id ke dataframe product
  df['product'] = df['product_id'].map(product_to_product_encoded)
  ```
  
- **Mengecek Jumlah Brand dan Jumlah Product dan Mengubah Nilai Rating menjadi Float**

  Selanjutnya, jumlah brand (num_brands) dihitung dari ID Brand yang sudah di-encode, dan jumlah product (num_products) dihitung dari ID Product yang sudah di-encode. Kemudian, dilakukan pemeriksaan dan penentuan nilai minimum (min_rating) serta nilai maksimum (max_rating) dari kolom average_rating. Karena kolom tersebut sudah berbentuk tipe data float, maka langsung saja dengan mengambil nilai minimum dan maksimum dari seluruh rating yang ada. Berikut kode yang digunakan dalam proses ini:
  
  ```python # Mendapatkan jumlah brand
  num_brands = len(brand_to_brand_encoded)
  print(num_brands)
  
  # Mendapatkan jumlah product
  num_products = len(product_encoded_to_product)
  print(num_products)
  
  # Nilai minimum rating
  min_rating = min(df['average_rating'])
  
  # Nilai maksimal rating
  max_rating = max(df['average_rating'])
  
  print('Number of Brand: {}, Number of Product: {}, Min Rating: {}, Max Rating: {}'.format(
      num_brands, num_products, min_rating, max_rating
  ))
  ```
  
  ![image](https://github.com/user-attachments/assets/5173b5b1-b959-4dbd-8b8e-862fa0241b82)

  Penentuan rentang rating ini penting untuk memahami distribusi data rating dan memastikan bahwa model memiliki informasi yang akurat mengenai batas-batas nilai yang mungkin diprediksi atau dianalisis.

- **Membagi Data untuk Training dan Validasi**
  
  Selanjutnya, perlu melakukan splitting data menjadi training dan validasi. Namun sebelum melakukan itu, perlu dilakukan pengacakan seluruh data secara menyeluruh. Hal ini penting untuk dilakukan untuk memastikan bahwa saat data nanti dibagi, bagian-bagian data pelatihan dan pengujian memiliki campuran informasi yang merata. Jika tidak diacak, model bisa belajar pola yang salah karena data yang berdekatan mungkin memiliki karakteristik yang mirip. Berikut hasil dari acak data:

  | brand_name_id | brand_name         | product_name                                    | product_id | price_range   | default_category    | average_rating | total_reviews | total_recommended_count | total_repurchase_maybe_count | total_repurchase_no_count | total_repurchase_yes_count | total_in_wishlist | brand | product |
  |---------------|--------------------|------------------------------------------------|------------|---------------|---------------------|----------------|---------------|--------------------------|-----------------------------|---------------------------|---------------------------|-------------------|-------|---------|
  | 683           | beauty-of-majesty | Eight Tea Cleansing Water                      | 89845      | Rp 269.000    | Makeup Remover       | 5.000000       | 3             | 4                        | 0                           | 0                         | 4                         | 86                | 25    | 683     |
  | 4457          | mirael            | Moisturizing Honey Sugar Wax Kit              | 92538      | Rp 95.000     | Hair Removal Care    | 4.647436       | 39            | 37                       | 9                           | 1                         | 29                        | 525               | 192   | 4457    |
  | 2457          | feat-for-skin     | Skintuition Hydrating Gel Crème               | 92662      | Rp 129.500    | Face Gel             | 4.350000       | 10            | 8                        | 1                           | 3                         | 6                         | 232               | 100   | 2457    |
  | 2598          | garnier           | Hydrabomb Serum Mask                          | 19764      | Rp 23.500     | Sheet Mask           | 4.507502       | 5465          | 5236                     | 891                         | 339                       | 4235                     | 699               | 107   | 2598    |
  | 7036          | the-originote     | B5 Acne Serum                                 | 101543     | Rp 38.000     | Face Serum           | 4.732639       | 72            | 70                       | 16                          | 2                         | 54                        | 461               | 292   | 7036    |
  | 5226          | papa-recipe       | Bombee Honey Mask Pack                        | 106251     | Rp 42.000     | Sheet Mask           | 5.000000       | 1             | 1                        | 0                           | 0                         | 1                         | 42                | 222   | 5226    |
  | 5390          | precious-skin     | Alpha Arbutin Collagen Body Serum UV Formula | 95707      | Rp 130.000    | Face Serum           | 4.078947       | 19            | 18                       | 6                           | 1                         | 12                        | 322               | 230   | 5390    |
  | 860           | bio-essence       | Twinpack Bioessence BioWater Energizing Water | 92067      | Rp 555.000    | Face Mist            | 0.000000       | 0             | 0                        | 0                           | 0                         | 0                         | 2                 | 33    | 860     |
  | 7603          | you-beauty        | YOU Cloud Touch Fixing Tint Special Pack      | 100820     | Rp 249.000    | Lip Tint             | 4.900000       | 2             | 2                        | 0                           | 0                         | 2                         | 18                | 316   | 7603    |
  | 7270          | vaseline          | Daily Sun Cream                               | 82320      | Rp 129.000    | Sunscreen            | 4.566810       | 113           | 107                      | 29                          | 11                        | 76                        | 1077              | 308   | 7270    |
  

 Selanjutnya, informasi yang akan menjadi masukan model (fitur input) dan informasi yang akan diprediksi (target) dikumpulkan. Untuk input, kolom `brand` dan `product` dipilih karena keduanya merepresentasikan identitas unik produk. Sedangkan untuk target, kolom `rating` digunakan untuk merepresentasikan penilaian produk oleh pengguna. Pada tahap ini, nilai rating dinormalisasi ke dalam rentang 0 hingga 1. Proses normalisasi ini penting untuk membantu model belajar dengan lebih stabil dan menghasilkan prediksi yang lebih konsisten.
 Kemudian, data dibagi menjadi dua bagian, yaitu 80% untuk data pelatihan dan 20% untuk data validasi. Data pelatihan digunakan untuk melatih model agar dapat mengenali pola dari data, sedangkan data validasi digunakan untuk mengevaluasi kinerja model terhadap data baru yang tidak digunakan selama pelatihan. Pemisahan data ini dilakukan untuk menghindari overfitting dan memastikan bahwa model dapat memberikan hasil yang baik ketika diuji pada data yang belum pernah dilihat sebelumnya. Pada proses ini, penting untuk memastikan bahwa transformasi data, seperti normalisasi, hanya dilakukan pada data pelatihan. Hal ini agar data validasi tetap berperan sebagai data baru yang benar-benar terpisah dari proses pelatihan.

 ![image](https://github.com/user-attachments/assets/51b8f0bd-84e3-4c58-b735-4a3d6cba22a5)


## Modeling
Pada tahap modeling akan menggunakan 2 pendekatan, yaitu teknik Content-Based Filtering dan Collaborative Filtering untuk membangun sistem rekomendasi produk.

### 1. Content-Based Filtering

Pendekatan Content-Based Filtering memberikan rekomendasi produk berdasarkan kesamaan konten antara produk yang pernah dilihat, dibeli, atau disukai oleh pengguna dengan produk lainnya dalam dataset. Kesamaan ini dihitung menggunakan metrik seperti **Cosine Similarity**, yang mengukur kemiripan antar produk berdasarkan fitur-fitur tertentu, seperti nama produk, kategori, dan brand.

- **Proses Content-Based Filtering**

  1. **Perhitungan Cosine Similarity**
     
     Cosine Similarity digunakan untuk mengukur tingkat kemiripan antar produk berdasarkan representasi fitur dalam ruang vektor. Semakin tinggi nilai Cosine Similarity, semakin mirip dua produk tersebut. Fungsi `cosine_similarity()` digunakan untuk menghitung matriks kesamaan antar produk dalam dataset. Matriks ini menunjukkan hubungan antara semua produk, baik dalam sumbu X maupun Y.
  
  3. **Penyusunan Matriks Cosine Similarity**
     
     Hasil perhitungan Cosine Similarity diubah menjadi sebuah DataFrame untuk mempermudah analisis dan pencarian produk-produk yang paling mirip. Baris dan kolom pada DataFrame ini mewakili produk, sementara nilai di dalamnya menunjukkan tingkat kemiripan antar produk.

    | **product_name**                                                | MULTI EYE COLOR PALETTE | Heartleaf Essence Calming Pump | Licorice pH Balancing Cleansing Toner | Noni Glow Concentrate | Nudie Blendies - Makeup Sponge | Glazed Lip Tint | 01 Powder Room Eau De Parfum | Shake Lip Pigment (SLP) - Matte Liquid Lipstick, Serum-Infused | DEW POWER VEGAN CUSHION | New Brightening Uv Sunscreen Gel |
    |------------------------------------------------------------------|--------------------------|---------------------------------|----------------------------------------|-----------------------|-------------------------------|-----------------|------------------------------|----------------------------------------------------------------|--------------------------|----------------------------------|
    | **MULTI EYE COLOR PALETTE**                                     | 1.0                      | 0.0                             | 0.0                                    | 0.0                   | 0.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 0.0                      | 0.0                              |
    | **Heartleaf Essence Calming Pump**                              | 0.0                      | 1.0                             | 0.0                                    | 0.0                   | 0.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 0.0                      | 0.0                              |
    | **Licorice pH Balancing Cleansing Toner**                       | 0.0                      | 0.0                             | 1.0                                    | 0.0                   | 0.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 0.0                      | 0.0                              |
    | **Noni Glow Concentrate**                                       | 0.0                      | 0.0                             | 0.0                                    | 1.0                   | 0.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 0.0                      | 0.0                              |
    | **Nudie Blendies - Makeup Sponge**                              | 0.0                      | 0.0                             | 0.0                                    | 0.0                   | 1.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 0.0                      | 0.0                              |
    | **Glazed Lip Tint**                                             | 0.0                      | 0.0                             | 0.0                                    | 0.0                   | 0.0                           | 1.000000        | 0.0                          | 0.440314                                                       | 0.0                      | 0.0                              |
    | **01 Powder Room Eau De Parfum**                                | 0.0                      | 0.0                             | 0.0                                    | 0.0                   | 0.0                           | 0.000000        | 1.0                          | 0.000000                                                       | 0.0                      | 0.0                              |
    | **Shake Lip Pigment (SLP) - Matte Liquid Lipstick, Serum-Infused** | 0.0                      | 0.0                             | 0.0                                    | 0.0                   | 0.0                           | 0.440314        | 0.0                          | 1.000000                                                       | 0.0                      | 0.0                              |
    | **DEW POWER VEGAN CUSHION**                                     | 0.0                      | 0.0                             | 0.0                                    | 0.0                   | 0.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 1.0                      | 0.0                              |
    | **New Brightening Uv Sunscreen Gel**                            | 0.0                      | 0.0                             | 0.0                                    | 0.0                   | 0.0                           | 0.000000        | 0.0                          | 0.000000                                                       | 0.0                      | 1.0                              |
    
    _Matriks ini menunjukkan tingkat kemiripan antar produk berdasarkan fitur konten. Semakin tinggi nilai (mendekati 1), semakin mirip kedua produk tersebut._
  
  4. **Penyaringan Data**
     
     Produk-produk dengan nilai kemiripan tertinggi disaring sebagai kandidat untuk direkomendasikan kepada pengguna. Hasil ini disesuaikan dengan produk yang sudah pernah diinteraksikan oleh pengguna untuk menghindari duplikasi.

  Dengan menggunakan cosine similarity, sistem berhasil mengukur tingkat kemiripan antara satu nama produk dengan produk lainnya. Matriks kesamaan yng dihasilkan berukuran (321, 321). Matriks ini merepresentasikan tingkat kesamaan antar 321 produk. Karena ukurannya besar, hanya ditampilkan sebanyak 10 sampel data saja, yaitu 10 produk secara vertikal dan 10 secara horizontal. Data ini digunakan untuk merekomendasikan produk yang mirip dengan yang pernah dibeli oleh pengguna. Contoh: angka 1 pada 01 Powder Room Eau De Parfum dan Secretly Sexy Eau De Parfum yang menunjukkan dua produk ini memiliki kesamaan kategori produk.

- **Fungsi Rekomendasi Produk**
  
  * Fungsi **product\_recommendation** dibuat untuk menghasilkan rekomendasi berbasis konten, dengan menampilkan daftar produk yang mirip dengan produk yang pernah dilihat atau dibeli oleh pengguna. Output dari fungsi ini berupa **Top-N recommendation**, di mana jumlah rekomendasi dapat diatur sesuai kebutuhan melalui parameter k. Fungsi ini mengidentifikasi sejumlah produk teratas dengan nilai kemiripan tertinggi terhadap produk yang diberikan sebagai input.
  * Untuk implementasi yang efisien, dengan mengimplementasikan fungsi `argpartition()` yang digunakan untuk mengekstrak nilai kemiripan tertinggi dari matriks Cosine Similarity. Nilai-nilai tersebut kemudian diurutkan berdasarkan bobot kemiripan dari yang paling tinggi ke rendah dan disimpan dalam variabel closest. Untuk menghindari duplikasi dalam hasil, judul buku yang dijadikan acuan (input) akan dihapus dari daftar rekomendasi agar tidak muncul kembali dalam hasil rekomendasi yang diberikan. Produk yang dijadikan input akan dikeluarkan (dihapus) dari hasil rekomendasi untuk menghindari duplikasi. Dengan pendekatan ini, sistem mampu memberikan rekomendasi yang relevan berdasarkan fitur dan karakteristik produk dalam dataset.

- **Output Rekomendasi**
  Ketika pengguna memilih produk tertentu, maka sistem akan mencari produk-produk dengan kemiripan tertinggi terhadap produk tersebut berdasarkan nama produk, nama brand, dan kategori. Sehingga rekomendasi yang dihasilkan akan mencakup 10 produk yang paling mirip dengan produk yang dipilih.
  Misalnya, apabila pengguna memilih produk yaitu "Bakuchiol Revitalizing Serum", maka sistem akan memberikan rekomendasi seperti berikut ini:

  ![image](https://github.com/user-attachments/assets/892dadfc-0b91-4e6f-8e11-a2a2ac2cf922)

  Berdasarkan output diatas, sistem berhasil merekomendasikan 10 produk teratas dengan kategori produk (default_category) yang sama yaitu 'Face Serum' dan memiliki produk dengan penamaan yang mirip (masih dalam satu rangkaian kategori yang sama yaitu Face Serum).
  
- **Kelebihan Content-based Filtering**
  1. **Personalized Recommendations**: Rekomendasi berbasis kesukaan pengguna terhadap produk tertentu, sehingga hasil lebih relevan dan sesuai dengan preferensi individu.
  2. **Tidak Membutuhkan Data Pengguna Lain**: Hanya bergantung pada data konten produk, sehingga tetap berfungsi meskipun hanya ada satu pengguna dalam sistem.
  3. **Fleksibilitas Fitur Produk**: Dapat memanfaatkan berbagai jenis atribut produk, seperti deskripsi, kategori, atau fitur tambahan, untuk menghasilkan rekomendasi yang lebih akurat.
  4. **Skalabilitas pada Dataset Baru**: Model dapat dengan mudah merekomendasikan produk baru selama produk tersebut memiliki informasi konten yang lengkap.
  5. **Menghindari Cold Start pada Pengguna**: Pengguna baru tetap mendapatkan rekomendasi berbasis produk yang mereka eksplorasi, tanpa perlu menunggu data interaksi yang banyak.
  
- **Kekurangan Content-Based Filtering**
  1. **Kurangnya Keberagaman Rekomendasi (Over-Specialization)**: Sistem hanya merekomendasikan produk yang sangat mirip dengan yang sudah dipilih atau disukai, sehingga keberagaman produk yang disarankan cenderung rendah.
  2. **Ketergantungan pada Kualitas Data Konten**: Jika data konten produk tidak lengkap atau tidak relevan, kualitas rekomendasi akan menurun.
  3. **Tidak Bisa Merekomendasikan Produk Tanpa Interaksi Awal**: Sistem tidak dapat memberikan rekomendasi yang optimal jika pengguna belum memberikan preferensi atau data eksplisit terkait produk tertentu.
  4. **Cold Start untuk Produk Baru Tanpa Deskripsi yang Memadai**: Produk baru dengan deskripsi yang kurang lengkap akan sulit masuk dalam sistem rekomendasi.
  5. **Komputasi yang Intensif**: Membutuhkan perhitungan seperti Cosine Similarity yang memerlukan banyak sumber daya untuk dataset besar, terutama saat membuat matriks kemiripan.
  6. **Sulit Menangkap Preferensi Kompleks**: Tidak dapat memahami preferensi yang tidak tersurat atau pola interaksi pengguna yang lebih kompleks (misalnya, konteks penggunaan).

### 2. Collaborative Filtering

Collaborative Filtering adalah pendekatan sistem rekomendasi yang memanfaatkan pola interaksi pengguna dengan produk. Pendekatan ini bekerja dengan memprediksi preferensi pengguna terhadap produk yang belum mereka interaksikan, berdasarkan pola interaksi pengguna lain yang memiliki preferensi serupa. Collaborative Filtering secara umum dibagi menjadi dua jenis utama: **memory-based** (berbasis memori) dan **model-based** (berbasis model). Dalam implementasi modern, teknik berbasis model dengan pembelajaran mendalam sering digunakan untuk menghasilkan rekomendasi yang lebih akurat.

- **Proses Collaborative Filtering**
  1. **Model Embedding untuk Pengguna dan Produk**
     * Dalam pendekatan model-based, brand dan produk direpresentasikan dalam bentuk vektor embedding berdimensi rendah. Representasi ini dirancang untuk menangkap pola preferensi pengguna dan karakteristik produk.
     * Setiap pengguna dan produk memiliki vektor embedding unik yang dipelajari selama proses pelatihan. Selain itu, bias pengguna dan bias produk ditambahkan untuk mengakomodasi preferensi individual.
     * Dropout (contohnya dengan rate 0.2) diterapkan pada embedding untuk mengurangi risiko overfitting. Embedding untuk pengguna (brand) dan produk diinisialisasi menggunakan **layers.Embedding**. Regularisasi L2 diterapkan untuk mencegah overfitting, sementara dropout dengan rate 0.2 digunakan untuk meningkatkan generalisasi.
  
  3. **Perhitungan Prediksi**
     * Prediksi preferensi dihitung dengan melakukan *dot product* antara embedding pengguna dan produk.
     * Hasil *dot product* ini ditambahkan dengan bias pengguna dan bias produk.
     * Fungsi aktivasi sigmoid digunakan untuk memastikan nilai prediksi berada dalam rentang 0 hingga 1.
  
  4. **Pelatihan Model**
     * Model dilatih menggunakan data interaksi yang mencakup pasangan pengguna dan produk, serta rating yang diberikan.
     * Tahapan utama nya meliputi:
       - Input data: x_train berisi pasangan user_id dan product_id, serta y_train berisi nilai interaksi.
       - Optimisasi: Menggunakan fungsi loss BinaryCrossentropy dan optimizer Adam.
       - Parameter pelatihan: Batch size 64, jumlah epoch 50, dan penggunaan data validasi untuk memantau performa.
     * Regularisasi L2 dan dropout digunakan untuk mencegah overfitting dan meningkatkan generalisasi model.
     * Fungsi loss, seperti *binary crossentropy*, diterapkan untuk mengoptimalkan model.
     * Optimizer Adam dengan *learning rate* rendah (misalnya, 1e-4) digunakan untuk mempercepat konvergensi.
     * Pelatihan dilakukan dalam beberapa epoch (contohnya 50 epoch) dengan batch size kecil (misalnya, 64) untuk meningkatkan efisiensi pembelajaran.

    ```python # Compile Model
    model.compile(
        loss = tf.keras.losses.BinaryCrossentropy(),
        optimizer=keras.optimizers.Adam(learning_rate=1e-4),
        metrics=[tf.keras.metrics.RootMeanSquaredError()]
    ) 
    ```
- **Fungsi Rekomendasi Produk**
  1. **Identifikasi Produk yang Belum Dinilai**: Untuk pengguna tertentu, sistem mengidentifikasi produk-produk yang belum pernah diberi rating.
  2. **Prediksi Skor untuk Produk Baru**: Produk-produk yang belum dinilai di-encode, kemudian digabungkan dengan data pengguna dalam format array input. Model memprediksi rating untuk setiap produk tersebut, menghasilkan skor prediksi untuk seluruh produk yang belum diinteraksikan oleh pengguna.
  3. **Pemilihan Rekomendasi Terbaik**: Sistem memilih *Top-N* produk dengan skor prediksi tertinggi untuk direkomendasikan. Misalnya, 10 produk dengan skor tertinggi. Selain itu, sistem juga menampilkan daftar produk dengan rating tertinggi yang sudah dinilai oleh pengguna, untuk memberikan konteks preferensi pengguna terhadap produk sebelumnya.

- **Manfaat Collaborative Filtering**

Pendekatan ini memungkinkan rekomendasi yang relevan dan personal dengan memanfaatkan pola kolektif dari interaksi pengguna. Dengan mengandalkan kesamaan preferensi antar pengguna, Collaborative Filtering dapat memberikan rekomendasi bahkan untuk produk yang tidak memiliki deskripsi atau metadata lengkap, menjadikannya ideal untuk dataset besar dan dinamis.

- **Output Rekomendasi**
  Setelah pelatihan, model dapat memberikan Top-N recommendation produk berdasarkan prediksi rating. Sebagai contoh, rekomendasi produk untuk pengguna dengan ID **302** berhasil dihasilkan melalui pendekatan **Collaborative Filtering**. Sistem ini tidak hanya merekomendasikan produk baru yang relevan tetapi juga memberikan konteks preferensi pengguna dengan menampilkan produk yang sebelumnya pernah diinteraksikan. Berdasarkan hasil tersebut, pengguna sebelumnya telah menunjukkan ketertarikan pada produk seperti *Renew You Toner Essence* dengan rata-rata rating **4.33**, yang menjadi indikasi preferensi pengguna terhadap produk perawatan kulit.
  Dari rekomendasi yang dihasilkan, beberapa produk unggulan seperti *Body Wash PATCHOULI* dan *Age Miracle Hya-Retinol Ultimate Glow Essence* memiliki rating tinggi, mencapai **5.0**, menunjukkan tingkat kesesuaian yang sangat baik dengan preferensi pengguna. Selain itu, rekomendasi lain seperti *Song of The Youth* dengan rating **4.66** dan *Hand & Nature White Musk Hand Cream* dengan rating **4.75** juga memperlihatkan variasi yang kaya namun tetap relevan dalam kategori yang serupa.
  Keberhasilan ini mencerminkan kemampuan sistem untuk menangkap pola interaksi pengguna dengan produk secara mendalam, sehingga menghasilkan rekomendasi yang lebih personal dan beragam. Dengan memanfaatkan kesamaan preferensi antar pengguna, pendekatan ini menunjukkan efisiensi dalam mengidentifikasi produk yang sesuai dengan kebutuhan pengguna, sekaligus meningkatkan pengalaman dan kepuasan mereka terhadap sistem rekomendasi.

  ![image](https://github.com/user-attachments/assets/effbf8ca-11c7-4e9b-a797-d0988eb990fd)

- **Kelebihan Collaborative Filtering**
  1. **Personalisasi Rekomendasi:** Sistem ini berhasil memberikan rekomendasi yang personal berdasarkan preferensi pengguna lain yang memiliki pola interaksi serupa, sehingga relevansi produk yang direkomendasikan menjadi lebih tinggi.
  2. **Tidak Memerlukan Data Produk yang Mendalam:** Collaborative Filtering hanya memanfaatkan pola interaksi (seperti rating atau klik) tanpa memerlukan informasi mendalam tentang produk, sehingga bisa digunakan pada dataset dengan metadata produk yang terbatas.
  3. **Kemampuan Menangkap Tren:** Model ini mampu mengidentifikasi produk yang sedang populer di antara pengguna dengan preferensi serupa, menjadikan rekomendasi lebih dinamis dan sesuai dengan tren terkini.
  4. **Efektif pada Dataset yang Luas:** Dengan jumlah pengguna dan produk yang besar, pendekatan ini semakin akurat karena pola kesamaan antar pengguna dan produk dapat teridentifikasi lebih baik.
  5. **Rekomendasi Bervariasi:** Rekomendasi yang diberikan mencakup beragam kategori produk, seperti perawatan kulit, perawatan tubuh, dan kosmetik, yang sesuai dengan berbagai kebutuhan pengguna.

- **Kekurangan Collaborative Filtering:**
  1. **Cold-Start Problem:** Sistem kesulitan memberikan rekomendasi untuk pengguna atau produk baru karena belum memiliki interaksi historis (data awal).
  2. **Sparse Data Issue:** Jika dataset interaksi terlalu jarang (misalnya, banyak produk yang belum pernah diinteraksikan oleh pengguna), performa model bisa menurun karena kesulitan menemukan pola kesamaan.
  3. **Computational Complexity:** Pada dataset yang sangat besar, seperti jutaan pengguna dan produk, proses komputasi untuk menghitung kesamaan antar pengguna atau produk bisa menjadi intensif.
  4. **Kurang Responsif terhadap Perubahan Preferensi:** Sistem ini lebih mengandalkan data historis sehingga memerlukan waktu untuk menyesuaikan jika preferensi pengguna berubah secara signifikan.
  5. **Tidak Mempertimbangkan Karakteristik Produk:** Pendekatan ini hanya fokus pada pola interaksi dan tidak memperhitungkan atribut produk (misalnya, harga), sehingga bisa mengabaikan kebutuhan spesifik pengguna.

## Evaluation
### 1. Evaluasi Model Content-Based Filtering

Dalam model Content-Based Filtering, digunakan tiga evaluation metrix utama untuk mengukur performa sistem rekomendasi buku berbasis kemiripan konten, yaitu Precision, Recall, dan F1-score. Metrik-metrik ini dipilih karena sesuai untuk mengukur kualitas model dalam tugas klasifikasi biner, yakni memprediksi apakah sebuah pasangan buku memiliki kemiripan tinggi (positif) atau tidak (negatif).

- **Precision**
  Precision merupakan metrik yang digunakan untuk mengukur rasio antara jumlah item relevan yang berhasil direkomendasikan dengan jumlah total item yang direkomendasikan oleh model. Precision dihitung menggunakan rumus berikut:
  ![image](https://github.com/user-attachments/assets/c1ee63b6-d223-4463-a7ec-c2c72ef26a8f)

  Dalam konteks ini, Precision menunjukkan seberapa baik model dalam menghindari rekomendasi item yang tidak relevan. Semakin tinggi nilai precision, semakin relevan rekomendasi yang dihasilkan oleh model.
  
- **Recall**
  Recall mengukur rasio antara jumlah item relevan yang berhasil direkomendasikan dengan total item relevan yang seharusnya direkomendasikan. Recall dihitung menggunakan rumus berikut:
  
  ![image](https://github.com/user-attachments/assets/777b35bf-26df-444a-b546-b787acf0d6cf)

  Recall fokus pada kemampuan model menemukan sebanyak mungkin item relevan. Semakin tinggi nilai recall, semakin banyak item relevan yang ditemukan oleh sistem.

- **F1-Score**
  F1-Score adalah rata-rata harmonik dari Precision dan Recall, yang memberikan ukuran keseimbangan antara keduanya. F1-Score dihitung menggunakan rumus berikut:
  ![image](https://github.com/user-attachments/assets/7812922f-4eef-48c9-9549-33d549f50a6e)

  F1-Score sangat penting ketika ada ketidakseimbangan antara jumlah item relevan dan tidak relevan, karena memastikan keseimbangan antara akurasi rekomendasi dan cakupan item relevan. Nilai F1-Score yang tinggi menunjukkan bahwa model tidak hanya akurat tetapi juga mampu merekomendasikan item relevan dalam jumlah yang cukup.

  Sebelum menghitung ketiga metrik TERSEBUT, perlu disiapkan data **ground_truth** yang menjadi acuan evaluasi. Dalam proyek ini, data ground truth dibentuk berdasarkan nilai kemiripan antar item (produk) menggunakan teknik cosine similarity. Setiap baris dan kolom mewakili nama produk, dan nilai dalam sel menunjukkan apakah dua produk tersebut dianggap mirip atau tidak. Ambang batas (threshold) sebesar 0.5 digunakan untuk menentukan apakah dua item dianggap mirip. Jika nilai kemiripan ≥ threshold, item dianggap mirip/similar (nilai 1) dan sebaliknya jika kurang, item dianggap tidak mirip/not similar (nilai 0). Nilai threshold ini ditentukan berdasarkan kebutuhan dan karakteristik data setelah mengamati hasil rekomendasi sebelumnya. Proses pembuatan ground truth dilakukan dengan fungsi np.where() dari library NumPy. Matriks ini kemudian diubah ke dalam bentuk DataFrame, dengan nama produk digunakan sebagai indeks pada baris dan kolom. Setelah ground truth terbentuk, langkah selanjutnya adalah mengevaluasi performa model menggunakan metrik precision, recall, dan f1-score.
  Proses evaluasi dimulai dengan data similarity matrix dan ground truth diubah ke dalam bentuk array 1 dimensi (flattened) agar mudah dibandingkan. Prediksi model dikonversi menjadi biner (0 atau 1) berdasarkan threshold. Fungsi precision_recall_fscore_support dari pustaka Scikit-learn digunakan untuk menghitung metrik evaluasi, dengan parameter average='binary' dan zero_division=1. Dengan pendekatan ini, evaluasi menggunakan ketiga metrik tersebut memberikan pandangan menyeluruh mengenai kekuatan dan kelemahan sistem Content-Based Filtering yang dikembangkan. Adapun hasil evaluasi yang diperoleh menunjukkan performa model sebagai berikut:

![image](https://github.com/user-attachments/assets/2eb8cf40-6347-408e-bcd7-addfb60ad1fb)

- **Hasil Evaluasi dengan Precision, Recall, dan F1-score**
  Pada hasil evaluasi, ketiga metrik menunjukkan nilai yang sempurna yaitu sebesar 1.00. Hal ini menunjukkan bahwa model berhasil memberikan semua rekomendasi produk yang benar-benar relevan (precision = 1.00), sekaligus tidak melewatkan produk yang relevan sama sekali (recall = 1.00). Nilai F1-score yang sempurna (nilai 1.0) menunjukkan keseimbangan ideal antara precision dan recall. Nilai evaluasi ini mengindikasikan bahwa sistem rekomendasi bekerja sangat baik pada subset data yang diuji, menghasilkan rekomendasi yang sangat akurat dan komprehensif.

### 2. Evaluasi Model Collaborative Filtering

Dalam proyek ini, evaluasi performa model rekomendasi menggunakan pendekatan Collaborative Filtering dilakukan dengan metrik Root Mean Squared Error (RMSE). RMSE adalah metrik yang umum digunakan untuk mengukur tingkat kesalahan dalam prediksi yang dihasilkan oleh model. Dalam konteks sistem rekomendasi, RMSE mengukur seberapa jauh prediksi rating yang dihasilkan oleh model dibandingkan dengan rating aktual yang diberikan oleh pengguna.
- **Formula RMSE**
  
  Root Mean Squared Error (RMSE) adalah metrik yang digunakan untuk mengukur tingkat kesalahan rata-rata antara nilai yang diprediksi oleh model dengan nilai aktual. RMSE dihitung dengan mengkuadratkan selisih antara prediksi dan aktual, merata-ratakannya, lalu mengambil akar kuadratnya. Nilai RMSE yang lebih rendah menunjukkan model memiliki akurasi prediksi yang lebih baik. RMSE dihitung menggunakan rumus berikut:
  ![image](https://github.com/user-attachments/assets/dbc949c0-7d05-4676-8a1c-3d679490b4b8)

  Keterangan :
  ![image](https://github.com/user-attachments/assets/ba27b83c-a823-46bc-942a-e234189ba211)

  Proses Perhitungan RMSE yaitu dengan menghitung selisih antara rating aktual dan prediksi dihitung untuk setiap interaksi pengguna dengan produk. Lalu, setiap selisih dikuadratkan untuk memastikan nilai negatif tidak mempengaruhi hasil dan memberikan bobot lebih pada kesalahan besar. Kemudian, nilai kuadrat selisih dirata-ratakan, menghasilkan Mean Squared Error (MSE). Dan terakhir, akar kuadrat diambil dari nilai MSE untuk mengembalikan kesalahan ke skala asli rating, sehingga lebih mudah dipahami. **RMSE memberikan bobot lebih besar pada kesalahan yang lebih besar, sehingga nilai RMSE yang lebih rendah menunjukkan kinerja model yang lebih baik dalam merekomendasikan produk sesuai preferensi pengguna**.
  
- **Hasil Evaluasi dengan RMSE**

  ![image](https://github.com/user-attachments/assets/11db0a59-8d12-47ad-9148-ed04137caf32)

  Terlihat berdasarkan Grafik RMSE selama epoch menunjukkan bahwa performa model rekomendasi produk, nilai RMSE pada data training turun dari sekitar 0.45 ke 0.37, hal ini menandakan model belajar dengan baik. Sedangkan, nilai RMSE pada data testing turun tidak terlalu signifikan dan tetap stabil di sekitar 0.43, mengindikasikan sedikit overfitting dan keterbatasan generalisasi. Meski demikian, perbedaan antara kurva train dan test tidak terlalu besar, yang menunjukkan bahwa model tidak mengalami overfitting dan model sudah cukup baik. Untuk meningkatkan generalisasi, langkah seperti regularisasi lebih kuat, penyesuaian dropout, atau peningkatan jumlah data pelatihan bisa dipertimbangkan. Secara keseluruhan, model sudah menunjukkan performa yang memuaskan.


## Evaluasi Terhadap Business Understanding
1. Model machine learning dengan pendekatan Content-Based Filtering berhasil dirancang untuk memberikan rekomendasi produk yang sesuai dengan preferensi pengguna dengan memanfaatkan atribut produk seperti nama produk, kategori, dan nama brand. Sistem ini menggunakan teknik TF-IDF dan Cosine Similarity untuk menganalisis kemiripan antar produk berdasarkan atribut tekstual. Dengan pendekatan ini, sistem mampu merekomendasikan produk baru yang memiliki karakteristik serupa dengan produk yang telah diinteraksikan oleh pengguna, sehingga meningkatkan relevansi rekomendasi.
2. Model Collaborative Filtering berhasil diimplemtasikan untuk memberikan rekomendasi produk yang relevan dengan memanfaatkan data interaksi pengguna, seperti penilaian/rating, repurchase, wishlist, ulasan, dan aktivitas eksplisit lainnya. Sistem ini mempelajari pola kesamaan antar pengguna berdasarkan preferensi mereka dan merekomendasikan produk yang telah dinilai tinggi oleh pengguna lain dengan pola preferensi serupa. Dengan pendekatan ini, sistem dapat menangkap pola kolektif dan memberikan saran produk yang relevan bahkan untuk pengguna yang memiliki sedikit riwayat interaksi.

## Kesimpulan
Proyek ini berhasil menjawab problem statement dan mencapai goals yang telah ditentukan. Pengembangan model machine learning untuk membangun sistem rekomendasi berbasis Content-Based Filtering dan Collaborative Filtering yang mampu memberikan rekomendasi produk secara personal dan relevan. Dengan memanfaatkan atribut produk seperti nama produk, kategori, dan brand/merek, Content-Based Filtering memberikan saran produk yang mirip dengan preferensi pengguna berdasarkan analisis kesamaan konten. Sementara itu, Collaborative Filtering memanfaatkan pola interaksi pengguna untuk merekomendasikan produk berdasarkan preferensi kolektif, meskipun riwayat interaksi pengguna terbatas. Hasil evaluasi menunjukkan bahwa kedua pendekatan ini berhasil menjawab permasalahan utama, yaitu meningkatkan pengalaman pengguna dengan memberikan rekomendasi yang relevan, bervariasi, dan mendukung pengambilan keputusan yang lebih baik. Keberhasilan ini membuka peluang untuk pengembangan lebih lanjut, seperti integrasi kedua pendekatan untuk membangun sistem rekomendasi hibrid.


## Referensi
[1] M. R. Az Zayyad, "Sistem Rekomendasi Buku Menggunakan Metode Content-Based Filtering," *Universitas Islam Indonesia*, Yogyakarta, 2021, [Online], Available: https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1
[2] Dzumiroh Lisniati, "Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD," *Jurnal ITSMART*, vol. 1, no. 2, pp. 54-56, 2012, DOI: https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542

