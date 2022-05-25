# Laporan Proyek Machine Learning - Riezki Maisyar
---
### Domain Project

> **Domain proyek yang dipilih dalam proyek machine learning ini adalah mengenai kesehatan dengan judul proyek "Prediksi Penyakit Kanker Payudara pada Manusia/Wanita"**.

* Latar belakang
Kanker payudara merupakan salah satu penyakit yang dapat  menyebabkan kematian. Kanker payudara adalah pertumbuhan sel abnormal yang berasal dari kelenjar susu pada payudara. Kanker payudara terjadi karena sel membelah lebih cepat yang di mana sel-sel berasal dari duktus lactiferi yang lama tidak mati dan sel-sel baru yang berasal dari sel duktus lactiferi terus tumbuh dan berinvasi sehingga sel tersebut berkembang tidak terkendali dan sel normal mati [[1](http://repository.uhn.ac.id/handle/123456789/4689)]. 
International   Agency   for   Research   on   Cancer   (IARC)   2018  menyatakan terjadi peningkatan penderita kanker setiap tahunnya. Mulai dari tahun 2008 terdapat 12,7 juta kasus kanker di dunia dan terus menerus mengalami peningkatan hingga tahun 2018 menjadi 18,1 juta kasus kanker 2018 menyatakan terjadi peningkatan penderita kanker setiap tahunnya [[2](http://repository.uhn.ac.id/handle/123456789/4689)].
Mulai dari tahun 2008 terdapat 12,7 juta kasus kanker di dunia dan terus menerus mengalami peningkatan hingga tahun 2018 menjadi 18,1 juta kasus kanker.)]. Kematian yang disebabkan oleh kanker juga mengalami peningkatan dari 7,6 juta pada tahun 2008 menjadi 9,6 juta pada tahun 2018. IARC menyatakan bahwa terjadi peningkatan kasus kanker payudara yang menyerang  wanita  dengan  tingkat  kematian  sebesar  627.000  di  seluruh dunia.
Berdasarkan data dari Riset Kesehatan Dasar (RISKESDAS) tahun 2018  jumlah  kejadian kanker  payudara  yang  menyerang  wanita adalah sebesar  42,1  per  100.000  penduduk  dengan  rata-rata  kematian  17  per 100.000  penduduk  dan  data  pada  tahun 2012  sebesar  12,1  per  100.000 penduduk dengan jumlah kematian secara keseluruhan adalah 522.000 [[3](http://repo.poltekkesbandung.ac.id/1505/)]. Dari data tersebut menunjukkan setiap tahunnya terjadi peningkatan kejadian kanker payudara di Indonesia. Oleh sebab itu, diperlukan kesadaran bagi setiap orang, karena masalah ini merupakan masalah yang serius yang dialami oleh seorang wanita/ibu menyusui. Oleh karena itu maka dibuatlah sebuah model machine learning untuk memprediksi apakah seseorang yang mederita penyakit kanker payudara di diagnosis kanker ganas atau jinak. Dengan adanya model machine learning ini diharapkan dapat memudahkan pekerjaan dokter dalam mengindetifikasi penyakit kanker ganas lebih awal.
___
# Business Understanding
---
#### Problem Statements
berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:

- Bagaimana cara melakukan pra-pemrosesan pada data penyakit kanker payudara yang akan digunakan untuk membuat model yang baik?
- Bagaimana cara membuat model untuk memprediksi penyakit kanker payudara ganas atau jinak pada manusia dengan menggunakan machine learning?
- Bagaimana cara memilih/membuat algoritma yang mampu menghasilkan nilai akurasi diatas 90%
 
#### Goals
- Melakukan pra-pemrosesan dengan baik agar dapat digunakan dalam pembuatan model.
- Mengetahui cara membuat model machine learning untuk memprediksi penyakit kanker payudara ganas dan jinak pada wanita.
- Membuat model machine learning dengan nilai akurasi yang mencapai 90%.

#### Solution Statements
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya :
* Untuk pra-pemrosesan data dapat dilakukan beberapa teknik, diantaranya :
    * Melakukan _drop_ kolom pada kolom ID.
    * Mengatasi masalah data yang kosong dengan melakukan pengecekan terlebih dahulu lalu menggantinya dengan nilai rata-rata atau nilai median (kebetulan pada project ini tidak ditemukan data yg kosong).
    * Melakukan Encoding terhadap kolom yang bertipe _object_.
    * Melakukan pembagian dataset menjadi dua bagian dengan rasio 80% untuk data latih dan 20% untuk data uji.
    * Melakukan _Standard Scaler_.

* Untuk pembuatan model dipilih penggunaan model dengan algoritma Random Forest dan K-Nearest Neighbor. Algoritma tersebut dipilih karena mudah digunakan dan juga cocok untuk kasus ini. Berikut cara kerja, kelebihan dan kekurangan algoritma Random Forest dan K-Nearest Neighbor:
    * Cara kerja Algoritma Random Forest [[4]](https://repository.usd.ac.id/35513/):
        * Diawali dengan pemilihan k pada sampel dataset yang diambil secara acak dengan pengembalian
        * Gunakan dataset untuk membangun _decision tree_ ke-i
        * Ulangi langkah kedua langkah diatas sebanyak k.
    * Kelebihan dan kekurangan Algoritma Random Forest [[5]](https://eprints.umm.ac.id/39299/):
        * Kelebihannya yaitu dapat mengatasi _noise_ dan _missing value_ serta dapat mengatasi data dalam jumlah yang besar.
        * Kekurangan pada algoritma Random Forest yaitu interpretasi yang sulit dan membutuhkan tuning model yang tepat untuk data. 
    * Cara kerja Algoritma K-Nearest Neighbor [[6]](https://publikasi.dinus.ac.id/index.php/jais/article/view/1189/):
        * Menentukan jumlah tetangga terdekat K
        * Menghitung jarak dokumen _testing_ ke dokumen _training_
        * Urutkan data berdasarkan data yang mempunyai jarak Euclidean terkecil
        * Tentukan kelompok testing berdasarkan label pada K.
    * Kelebihan dan kekurangan Algoritma K-Nearest Neighbor [[7]](https://simdos.unud.ac.id/uploads/file_penelitian_1_dir/721bdb509a6f0bb9ccca6d7374b86759.pdf):
        * KNN memiliki beberapa kelebihan yaitu bahwa algoritmanya tangguh terhadap _training_ data yang _noisy_ dan efektif apabila data latihnya besar.
        * Kekurangan pada algoritma KKN yaitu perlu menentukan nilai dari parameter K (jumlah dari tetangga terdekat), Pembelajaran berdasarkan jarak tidak jelas mengenai jenis jarak apa yang harus digunakan dan atribut mana yang harus digunakan untuk mendapatkan hasil yang terbaik dan Biaya komputasi cukup tinggi karena diperlukan perhitungan dari jarak tiap sample uji pada keseluruhan sample latih.

# Data Understanding
---
![kaggle](https://i.postimg.cc/2SyPvwxP/image.png)
Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle, dimana fokus pada data tersebut menjelaskan faktor-faktor yang akan mempengaruhi sebuah penyakit kanker payudara bersifat ganas dan jinak.
Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset : Cancer Breast Dataset](https://www.kaggle.com/datasets/yasserh/breast-cancer-dataset)
Lisensi | CC0: Public Domain
Kategori | Cancer, Women, Healthcare
Jenis dan Ukuran Berkas | CSV (124.57 kB)

Pada berkas yang diunduh yakni cancer-breast.csv berisi 569 rows × 32 columns. Kolom-kolom tersebut terdiri dari 1 buah kolom bertipe objek dan 31 buah kolom bertipe numerik (tipe data float64). Untuk penjelasan mengenai variabel-variable pada dataset cancer breast ini dapat dilihat sebagai berikut:
- **id** merupakan parameter bernilai unique. Parameter ini tidak penting untuk dimasukkan kedalam model, oleh karena itu parameter ini di drop.
- **diagnosis** merupakan fitur target pada dataset ini, bertipe object yang terdiri dari (M,B). Dimana data tersebut menjelaskan diagnosis kanker bersifat Ganas (M) atau Jinak (B)
- **radius_mean** merupakan fitur yg merepresentasikan nilai rata-rata jarak dari pusat ke titik pada keliling sekitar payudara/benjolan
- **texture_mean** merupakan fitur yg merepresentasikan standar deviasi nilai skala abu-abu atau rata-rata Tekstur Permukaan
- **perimeter_mean** merupakan rata-rata keliling
- **area_mean** merupakan fitur yg merepresentasikan Rata-rata Luas Lobes
- **smoothness_mean** merupakan fitur yg merepresentasikan Rata-rata Tingkat Kehalusan
- **compactness_mean** merupakan fitur yg merepresentasikan Rata-rata Kekompakan atau keliling² / luas — 1.0
- **concavity_mean** merupakan fitur yg merepresentasikan rata-rata kecekungan atau keparahan bagian cekung dari contour
- **concave points_mean** merupakan fitur yg merepresentasikan rata-rata titik cekung atau jumlah bagian cekung dari contour
- **symmetry_mean** merupakan fitur yg merepresentasikan rata-rata Simetri
- **fractal_dimension_mean** merupakan fitur yg merepresentasikan rata-rata dimensi fraktal atau "*coastline approximation* — 1"
- **radius_se** merupakan fitur yg merepresentasikan radius standard error
- **texture_se** merupakan fitur yg merepresentasikan texture standard error
- **perimeter_se** merupakan fitur yg merepresentasikan perimeter standard error 
- **area_se** merupakan fitur yg merepresentasikan luas standar error
- **smoothness_se** merupakan fitur yg merepresentasikan smoothness standard error
- **compactness_se** merupakan fitur yg merepresentasikan compactness standard error
- **concavity_se** merupakan fitur yg merepresentasikan concavity standard error
- **concave points_se** merupakan fitur yg merepresentasikan titik cekung standard error
- **symmetry_se** merupakan fitur yg merepresentasikan symmetry standard error
- **fractal_dimension_se** merupakan fitur yg merepresentasikan fractal dimension standard error
- **radius_worst** merupakan fitur yg merepresentasikan radius terendah
- **texture_worst** merupakan fitur yg merepresentasikan texture terendah
- **perimeter_worst** merupakan fitur yg merepresentasikan perimeter terendah
- **area_worst** merupakan fitur yg merepresentasikan area terendah
- **smoothness_worst** merupakan fitur yg merepresentasikan tingkat kehalusan terendah
- **compactness_worst** merupakan fitur yg merepresentasikan compactness terendah
- **concavity_worst** merupakan fitur yg merepresentasikan kecekungan terendah
- **concave points_worst** merupakan fitur yg merepresentasikan titik cekung terendah
- **symmetry_worst** merupakan fitur yg merepresentasikan symmetry terendah
- **fractal_dimension_worst** merupakan fitur yg merepresentasikan fractional dimensi terendah

Berikut beberapa tahapan sebelum visualisasi data pada data preparation sebagai berikut:
- Meload Dataset ke dalam sebuah Dataframe menggunakan pandas
- ``` df.info()``` digunakan untuk mengecek tipe kolom pada dataset
- ```df.isna().sum()``` digunakan untuk mengecek apakah ada kolom yg kosong, pada dataset ini nilai kosong tidak ditemukan
- ```df.describe()``` digunakan utk mendapatkan info mengenai dataset terhadap nilai rata-rata, median, banyaknya data, nilai Q1 hingga Q3 dan lain-lain.

Berikut beberapa tahapan visualisasi data pada data preparation:
- Pertama membagi dataset kedalam 2 bentuk variable, yaitu variable untuk kolom tipe numerik dan variable kolom untuk tipe object
- Kemudian melakukan visualisasi distribusi categorial, dimana ini digunakan untuk menghitung jumlah sample Kanker Ganas/positif (M) dan kanker Jinak/negatif (B). pada project ini terdapat 357 jumlah data sampel kanker jinak (B) dan 212 data sample kanker ganas (M)
![img](https://i.postimg.cc/SRf5411z/image.png)
- lalu melakukan visualisasi distribusi numerik, yg dapat dilihat lebih rinci sebagai berikut:
![img](https://i.postimg.cc/Bvyf7zRS/image.png)
- Selanjutnya visualisasi dilakukan untuk mengetahui korelasi antar fitur yg terdapat pada dataset, untuk selengkapnya sebagai berikut:
![img](https://i.ibb.co/2gg4qvP/image.png)

# Data Preparation
---
Berikut adalah tahapan-tahapan dalam melakukan pra-pemrosesan data:
- Melakukan pengecekan terhadap kolom diagnosis (fitur target) yang bertipe object. dimana kategori B  merupakan sample Kanker Jinak dan M merupakan sample Kanker Ganas. fitur ini mengindintikasikan bahwa dari sample terdapat kategori kanker yang bersifat jinak dan kanker yang bersifat ganas. inilah fitur target yg ingin coba di prediksi pada project ini.
![img](https://i.ibb.co/MPmzZ1B/image.png)
- Melakukan mapping terhadap kolom diagnosis dari type object ke numerik agar bisa dibaca mesin. Dimana kanker jinak diubah ke nilai 0 dan kanker ganas diubah ke nilai 1
![mapping](https://i.postimg.cc/tT9q3Cjm/image.png)
- Melakukan perhitungan jumlah baris terhadap kolom target ![count](https://i.postimg.cc/ZKsWJ3SY/image.png)
- Melakukan pembagian dataset menjadi dengan 80% untuk data latih dan 20% untuk data uji
Setelah melakukan pra-pemrosesan ke dataset, Data latih adalah data yang hanya digunakan untuk melatih model, sedangkan data uji adalah data yang hanya digunakan sebagai ujicoba model. Pembagian dataset ini menggunakan modul train_test_split dari scikit-learn. ![Split Data](https://i.postimg.cc/sDGrZZWg/image.png)
- Melakukan standardisasi data pada semua fitur data.
Tahap terakhir yaitu melakukan standarisasi data. Hal ini dilakukan untuk membuat semua fitur berada dalam skala data yang sama yaitu dengan range 0-1. Strandadisasi data ini menggunakan fungsi StandardScaler yang perhitungannya seperti dibawah ini:
![img](https://i.postimg.cc/J0ZCvfMB/image.png)

# Modeling
---
Setelah dilakukan pra-pemrosesan pada dataset, langkah selanjutnya adalah *modeling* terhadap data. Pada tahap ini menggunakan 2 algoritma yaitu Random Forest dan K-Nearest Neighbor dengan tanpa parameter tambahan. Pertama-tama kedua model ini dilatih menggunakan data latih. Setelah itu kedua model akan diuji dengan data uji. Terakhir kedua model akan diukur nilai akurasinya. Perbandingan Hasil dari kedua model sebagai berikut:
![img](https://i.postimg.cc/6QJnNRr2/image.png)
Pada model dengan algoritma Random Forest memiliki nilai akurasi, f1-score, recall dan precision sedikit lebih tinggi dibanding dengan algoritma K-Nearest Neighbor. Untuk membuktikannya, kedua model tersebut diuji pada data uji dan di visualisasikan pada confussion matrix seperti berikut.
- *Confussion Matrix* algoritma Random Forest:
![img](https://i.postimg.cc/kXjPZvds/image.png)
pada algoritma diatas menjelaskan bahwa bagian **atas kiri** merepresentasikan TN (True negatif) yaitu data negatif yg diprediksi benar, dan bagian **bawah kanan** merupakan data positif yg di prediksi benar, selain itu merupakan data false negatif (atas kanan) dan false positif (bawah kiri), dimana hasil itu merupakan data negatif namun diprediksi positif maupun sebaliknya.
- *Confussion Matrix* algoritma K-Nearest Neighbor:
![img](https://i.postimg.cc/5tLGxwDZ/image.png)
pada penjelasan algoritma K-NN tidak jauh berbeda dengan algoritma *random forest* dimana bagian **atas kiri** merepresentasikan TN (True Negatif) yaitu data negatif yg diprediksi benar, dan bagian **bawah kanan** merupakan data positif yg di prediksi benar, selain itu merupakan data false negatif (atas kanan) dan false positif (bawah kiri), dimana hasil itu merupakan data negatif namun diprediksi positif maupun sebaliknya.

Dengan hasil diatas dimana algoritma random forest menghasilkan nilai akurasi yg sedikit lebih tinggi, maka model dengan algoritma Random Forest merupakan model yang dipilih untuk digunakan pada project ini.
# Evaluation
---
Pada proyek ini, model yang dikembangkan adalah kasus klasifikasi dan menggunakan metriks akurasi, *f1-score*, *recall* dan *precision*. Berikut hasil pengukuran model yang dipilih yaitu model yang menggunakan algoritma Random Forest metriks akurasi, _f1-score_, _recall_ dan _precision_.
![RF](https://i.postimg.cc/cLM5KQsY/image.png)
* Akurasi
    Akurasi merupakan metrik untuk menghitung persentase dari total data yang diidentifikasi dan dinilai benar. Rumus akurasi sebagai berikut:
    ![Image of Dataset](https://i.postimg.cc/NFx1VcgJ/akurasi.png)
    * _True Positive_ (TP):
    Kasus dimana model merupakan data positif yang diprediksi benar. Contohnya, pasien menderita kanker (class 1) dan dari model yang dibuat memprediksi pasien tersebut menderita kanker (class 1).
    * _True Negative_ (TN):
    Kasus dimana model merupakan data negatif yang diprediksi benar. Contohnya, pasien tidak menderita kanker (class 2) dan dari model yang dibuat memprediksi pasien tersebut tidak menderita kanker (class 2).
    * _False Positive_ (FP) - **Type I Error** :
    Kasus dimana model merupakan data negatif namun diprediksi sebagai data positif. Contohnya, pasien tidak menderita kanker (class 2) tetapi dari model yang telah memprediksi pasien tersebut menderita kanker (class 1).
    * _False Negative_ (FN) - **Type II Error** :
    Kasus dimana model merupakan data negatif namun diprediksi sebagai data positif. Contohnya, pasien tidak menderita kanker (class 2) tetapi dari model yang telah memprediksi pasien tersebut menderita kanker (class 1).
* _Precision_
    _Precision_ merupakan metrik untuk memprediksi benar positif dari keseluruhan hasil yang diprediksi positf. Rumus _precision_ sebagai berikut:
    ![Image of Dataset](https://i.postimg.cc/mzwZLjdM/precision.png)
* _Recall_
    _Recall_ merupakan metrik untuk memprediksi benar positif dibandingkan dengan keseluruhan data yang benar positif. Rumus _precision_ sebagai berikut:
    ![Image of Dataset](https://i.postimg.cc/K38GRTVW/recall.png)
* _f1-score_
    _f1-score_ merupakan metrik untuk perbandingan rata-rata precision dan recall yang dibobotkan. Rumus _f1-score_ sebagai berikut:
    ![Image of Dataset](https://i.postimg.cc/Fzm9ztjQ/f1-score.png)
## Referensi
---
[[1,2]](http://repository.uhn.ac.id/handle/123456789/4689) Situmeang, J. P. (2020). Hubungan Tingkat Pengetahuan Mengenai Kanker Payudara dengan Upaya Pencegahan dengan Pemeriksaan Payudara Sendiri pada Wanita Usia Subur di Puskesmas Rantau Laban Kota Tebing Tinggi. http://repository.uhn.ac.id/handle/123456789/4689
[[3]](http://repo.poltekkesbandung.ac.id/1505/) Firdaus Agustiyaningsih, Anida and rohendi, Yosep and Tursini, Yati and Diah, Sansri (2020) GAMBARAN KUALITAS HIDUP PASIEN KANKER PAYUDARA. Diploma thesis, POLTEKKES KEMENKES BANDUNG. http://repo.poltekkesbandung.ac.id/1505/
[[4]](https://repository.usd.ac.id/35513/) Haristu, R. A., & Rosa, P. H. P. (2019). Penerapan Metode Random Forest Untuk Prediksi Win Ratio Pemain Player Unknown Battleground. MEANS (Media Informasi Analisa dan Sistem), 120-128. https://repository.usd.ac.id/35513/
[[5]](https://eprints.umm.ac.id/39299/) Maziida, S. R. (2018). KLASIFIKASI PENYAKIT DIABETES MELLITUS DENGAN MENGGUNAKAN PERBANDINGAN ALGORITMA J48 DAN RANDOM FOREST (STUDI KASUS: RUMAH SAKIT MUHAMMADIYAH LAMONGAN) (Doctoral dissertation, University of Muhammadiyah Malang). https://eprints.umm.ac.id/39299/
[[6]](https://publikasi.dinus.ac.id/index.php/jais/article/view/1189/) Sani, R. R., Zeniarja, J., & Luthfiarta, A. (2016). Penerapan algoritma K-Nearest Neighbor pada information retrieval dalam penentuan topik referensi tugas akhir. Journal of Applied Intelligent System, 1(2), 123-133. https://publikasi.dinus.ac.id/index.php/jais/article/view/1189/
[[7]](https://simdos.unud.ac.id/uploads/file_penelitian_1_dir/721bdb509a6f0bb9ccca6d7374b86759.pdf) Penyelenggara PS. Teknik Informa ka, Jurusan Ilmu Komputer FMIPA - Universitas Udayana Kampus Bukit Jimbaran. PROSIDING ISSN : X SEMINAR NASIONAL TEKNOLOGI INFORMASI & APLIKASINYA 2015 INOVASI TEKNOLOGI INFORMASI DAN KOMUNIKASI DALAM MENUNJANG TECHNOPRENEURSHIP. Universitas Udayana (2015). https://simdos.unud.ac.id/uploads/file_penelitian_1_dir/721bdb509a6f0bb9ccca6d7374b86759.pdf
---Ini adalah bagian akhir laporan---