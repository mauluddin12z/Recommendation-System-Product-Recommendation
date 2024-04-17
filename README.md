# Laporan Proyek 2 Machine Learning - Muhammad Hidayat Mauluddin

## Domain Proyek

Dalam era digital yang terus berkembang, penggunaan sistem rekomendasi produk telah menjadi bagian integral dari platform e-commerce dan situs web lainnya. Sistem ini membantu pengguna menemukan produk yang sesuai dengan preferensi mereka, meningkatkan pengalaman belanja online, dan mendorong penjualan. Salah satu contoh paling terkenal adalah penggunaan sistem rekomendasi produk oleh Amazon. Mereka menggunakan algoritme yang canggih untuk menganalisis perilaku belanja pengguna, seperti riwayat pembelian, penelusuran, dan preferensi produk. Sistem rekomendasi Amazon membantu pengguna menemukan produk yang relevan dan meningkatkan penjualan dengan mendorong pembelian tambahan. Oleh karena itu, pengembangan sistem rekomendasi produk menjadi topik yang menarik dalam bidang ilmu komputer dan bisnis[1].

Ada banyak pendekatan dalam sistem rekomendasi produk. Contohnya *Content Based Filtering* dan *Collaborative Filtering*. Secara garis besar *Content Based Filtering* adalah metode pendekatan yang dilakukan dengan menggunakan data atau item yang sudah ada sebagai dasar dalam memberikan rekomendasi[2]. Sedangkan *Collaborative Filtering* adalah sebuah model atau metode pendekatan yang dilakukan menggunakan item item atau pendapat dari pengguna lain. Item item yang dimaksud dalam kasus ini adalah rating dari user. Data rating tersebut akan digunakan sebagai dasar untuk merekomendasikan item item yang relevan kepada pengguna[3]. Dengan metode atau pendekatan sistem rekomendasi tersebut diharapkan dapat meningkatkan pengalaman belanja online dari pengguna yang pada akhirnya dapat meningkatkan penjualan.



## Business Understanding

### Problem Statements

1. Bagaimana cara mengembangkan sistem rekomendasi produk dengan menggunakan pendekatan *Content-Based Filtering* yang memanfaatkan informasi konten produk seperti kategori produk untuk memberikan rekomendasi yang relevan kepada pengguna?
1. Bagaimana cara mengembangkan sistem rekomendasi produk dengan menggunakan pendekatan *Collaborative Filtering* yang memanfaatkan informasi perilaku pengguna seperti rating yang diberikan pengguna untuk memberikan rekomendasi yang personal dan akurat?

### Goals

1. Membangun sistem rekomendasi dengan pendekatan *Content-Based Filtering* yang dapat memberikan rekomendasi produk yang relevan dan sesuai dengan preferensi pengguna berdasarkan konten produk.
1. Membangun sistem rekomendasi dengan pendekatan Collaborative Filtering yang dapat memberikan rekomendasi produk yang personal dan akurat berdasarkan data perilaku pengguna.

### Solution Statements

Solusi yang dilakukan untuk memecahkan masalah tersebut yaitu menggunakan dua model atau algoritma Sistem Rekomendasi pada Machine Learning, Yaitu:

- Content Based Filtering adalah metode pendekatan yang dilakukan dengan menggunakan data atau item yang sudah ada sebagai dasar dalam memberikan rekomendasi[2].
- Collaborative Filtering adalah sebuah model atau metode pendekatan yang dilakukan menggunakan item item atau pendapat dari pengguna lain. Item item yang dimaksud dalam kasus ini adalah rating dari user[3].

## Data Understanding

Dataset yang digunakan dalam proyek ini adalah dataset yang bernama "Amazon Sales Dataset".

Berikut ini adalah informasi lebih terperinci tentang dataset:

- Jumlah baris (observasi): 1351
- Jumlah kolom (variabel): 16
- Variabel yang terdapat dalam dataset:

  - product_id - ID dari Produk
  - product_name - Nama Produk
  - category - Kategori produk
  - discounted_price - Harga Diskon
  - actual_price - Harga Asli
  - discount_percentage - Persentase Diskon
  - rating - Rating yang diberikan user untuk produk
  - rating_count - Jumlah orang  yang memberikan rating
  - about_product - Deskripsi Produk
  - user_id - ID dari user
  - user_name - nama user
  - review_id - id review
  - review_title - review singkat
  - review_content - review panjang
  - img_link - link gambar dari produk
  - product_link - link produk

Sumber dataset ini berasal dari Kaggle. Anda dapat mengakses dataset tersebut melalui tautan berikut: [Amazon Sales Dataset](https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset). Dari data tersebut akan diolah lagi dan dipilih yang mana saja variabel yang akan digunakan.

Berikut adalah statistik deskriptif untuk variabel "rating":

- Count: Terdapat 1464 data yang memiliki nilai pada variabel "rating".
- Mean: Rata-rata dari nilai "rating" adalah sekitar 4.097.
- Std (Standard Deviation): Standar deviasi dari nilai "rating" adalah sekitar 0.292. Hal ini menunjukkan tingkat dispersi atau variasi data dari rata-rata.
- Min: Nilai terendah dari "rating" adalah 2.000.
- 25%: 25% dari data "rating" memiliki nilai kurang dari atau sama dengan 4.000.
- 50%: Median dari "rating" adalah 4.100. Artinya, setengah dari data memiliki nilai "rating" kurang dari atau sama dengan 4.100.
- 75%: 75% dari data "rating" memiliki nilai kurang dari atau sama dengan 4.300.
- Max: Nilai tertinggi dari "rating" adalah 5.000.

Informasi ini memberikan gambaran tentang distribusi variabel "rating" dalam dataset, termasuk ukuran dataset, rata rata, variasi (standar deviasi), serta kuartil pertama (25%), median (50%), dan kuartil ketiga (75%).

## Data Preparation

Pada tahap ini akan dilakukan persiapan untuk data yang akan digunakan agar selanjutnya akan dapat dilakukan pemodelan pada data teresbut, contohnya adalah:

- Mengatasi Missing Value:

  - Data diperiksa untuk melihat apakah terdapat nilai yang kosong (missing value).

  - Jika ada data yang kosong, akan dilakukan penghapusan data tersebut.

    ![Capture](https://github.com/mauluddin12z/Proyek-2-Machine-Learning-Dicoding-Sistem-Rekomendasi/assets/71598808/20f9d3d5-c01b-452c-86ef-62a97cfb274f)

    Gambar 1. Pemeriksaan Data yang kosong pada dataset amazon Sales

    Dari gambar 1. diatas terdapat 3 missing value yang masing masing berada pada kolom rating dan rating_count. Maka 3 data tersebut akan dihapus menggunakan fungsi dropna().

- Membersihkan Data dan Merubah Tipe Data:

  - Data dibersihkan dari karakter atau kata yang tidak relevan.

  - Tipe data rating diubah menjadi float.

  - Misalnya, jika terdapat karakter "|" pada kolom rating yang mengakibatkan tipe data tidak dapat diubah menjadi float, maka dilakukan pembersihan data dengan menghilangkan karakter tersebut.

    ![cata cleaning](https://github.com/mauluddin12z/Proyek-2-Machine-Learning-Dicoding-Sistem-Rekomendasi/assets/71598808/6b2fdcd5-bddf-4e18-a72e-ce26b5a727b7)

    Gambar 2. Fungsi membersihkan data dari karakter atau kata yang tidak relevan dan merubah tipe data dari kolom rating.

- Membagi data menjadi data training dan validasi.
  - Data dibagi menjadi 80% data train dan 20% data validasi.
- Mengurutkan Data berdasarkan Product ID
  - Jika diperlukan, data diurutkan berdasarkan Product ID menggunakan fungsi seperti `sort_values()` dari library Pandas.
  - Pengurutan data membantu dalam memahami pola data atau memastikan data tersusun dengan benar sebelum proses selanjutnya dilakukan.
- Mengatasi Duplikasi Data:
  - Duplikasi data dapat mempengaruhi hasil analisis dan model yang dibangun.
  - Untuk mengatasi duplikasi data, digunakan fungsi `drop_duplicates()` untuk menghapus baris data yang memiliki nilai yang sama pada kolom yang ditentukan.
- Mengkonversi Data menjadi List:
  - Data dikonversi menjadi list menggunakan metode `tolist()` pada objek data seperti DataFrame atau Numpy Array.
  - Konversi ini berguna jika data perlu digunakan dalam format list untuk proses selanjutnya, seperti membangun model atau melakukan analisis khusus.
- Membuat Dictionary:
  - Penggunaan dictionary berguna jika data perlu dihubungkan dalam format key-value atau jika ingin melakukan pencarian berdasarkan kunci tertentu.
- Menggunakan TfidfVectorizer:
  - Dengan menggunakan TfidfVectorizer, teks diubah menjadi representasi numerik yang dapat diproses oleh algoritma machine learning.
  - Metode ini berguna jika teks ingin digunakan sebagai fitur dalam pemodelan, seperti dalam kasus content-based filtering.



## **Modeling** and Result

Terdapat  dua model atau algoritma yang digunakan untuk sistem rekomendasi ini, yaitu *Content Based Filtering* dan *Collaborative Filtering*

Berikut adalah hasil dari algoritma tersebut:

1. ***Content Based Filtering***

   Berikut adalah tabel rekomendasi dari produk "Wayona Nylon Braided USB to Lightning Fast Charging and Data Sync Cable Compatible for iPhone 13, 12,11, X, 8, 7, 6, 5, iPad Air, Pro, Mini (3 FT Pack of 1, Grey)" yang kategorinya "Computers&Accessories|Accessories&Peripherals|Cables&Accessories|Cables|USBCables"

   Tabel 1. Tabel Rekomendasi dari produk yang diinputkan.

   | index | product\_name                                                | category                                                     |
   | ----- | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | 0     | Ambrane Unbreakable 60W / 3A Fast Charging 1\.5m Braided Type C to Type C Cable for Smartphones, Tablets, Laptops & Other Type C Devices, PD Technology, 480Mbps Data Sync \(RCTT15, Black\) | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 1     | Belkin Apple Certified Lightning to USB Charge and Sync Tough Braided Cable for iPhone, iPad, Air Pods, 3\.3 feet \(1 meters\) – Black | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 2     | Portronics Konnect CL 20W POR-1067 Type-C to 8 Pin USB 1\.2M Cable with Power Delivery & 3A Quick Charge Support, Nylon Braided for All Type-C and 8 Pin Devices, Green | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 3     | Portronics Konnect L 1\.2Mtr, Fast Charging 3A Micro USB Cable with Charge & Sync Function \(Grey\) | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 4     | Portronics Konnect Spydr 31 3-in-1 Multi Functional Cable with 3\.0A Output, Tangle Resistant, 1\.2M Length, Nylon Braided\(Zebra\) | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |

Pada Tabel 1. di atas menampilkan rekomendasi produk. Produk Produk tersebut direkomendasikan dikarenakan pada produk tersebut terdapat relevansi dari segi kategori produk. Berikut adalah penjelasan kolom pada tabel 1. diatas.

1. **index**: Indeks numerik yang menunjukkan posisi setiap produk dalam tabel.
2. **product_name**: Nama produk yang direkomendasikan.
3. **category**: Kategori produk yang direkomendasikan. Kategori-kategori ini mencakup "Computers&Accessories|Accessories&Peripherals|Cables&Accessories|Cables|USBCables"

Dengan menggunakan sistem rekomendasi, tabel ini menyajikan beberapa opsi produk yang serupa dengan produk yang diinputkan. Pengguna dapat mempertimbangkan produk-produk ini sebagai alternatif yang relevan berdasarkan kategori dan fitur yang serupa.

**Kelebihan Content-Based Filtering:**

1. Independen dari data pengguna: Content-based filtering tidak memerlukan data pengguna lain atau kolaborasi antar pengguna. Model ini hanya mempertimbangkan preferensi pengguna yang bersangkutan dan karakteristik konten item untuk memberikan rekomendasi. Oleh karena itu, tidak ada masalah dengan cold-start problem saat ada pengguna baru atau item baru yang ditambahkan ke sistem.
2. Kemampuan dalam merekomendasikan item baru: Content-based filtering dapat merekomendasikan item yang belum pernah dikonsumsi oleh pengguna sebelumnya. Hal ini memungkinkan pengguna untuk menemukan item baru yang mungkin sesuai dengan preferensi mereka berdasarkan fitur dan karakteristik yang disukai.

**Kekurangan Content-Based Filtering:**

1. Kurangnya keberagaman rekomendasi dari produk dikarenakan Model content based filtering cenderung memberikan rekomendasi berdasarkan klasifikasi atau kategori dari produk.

   

2. ***Collaborative Filtering***

   Berikut adalah tabel 10 rekomendasi teratas produk untuk id user yang diinputkan pada model Machine Learning.

   Tabel 2. Hasil 10 Rekomendasi menggunakan pendekatan *Collaborative Filtering*

   | Product Name                                                 | Categories                                                   |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | Logitech Pebble M350 Wireless Mouse with Bluetooth or USB    | Computers&Accessories \| Accessories&Peripherals \| Keyboards,Mice&InputDevices \| Mice |
   | Amazon Basics Wireless Mouse                                 | Computers&Accessories \| Accessories&Peripherals \| Keyboards,Mice&InputDevices \| Mice |
   | Spigen EZ Fit Tempered Glass Screen Protector for iPhone 14 Pro Max - 2 Pack (Sensor Protection) | Electronics \| Mobiles&Accessories \| MobileAccessories \| Maintenance,Upkeep&Repairs \| ScreenProtectors |
   | Instant Pot Air Fryer, Vortex 2QT, Touch Control Panel, 360° EvenCrisp™ Technology, Uses 95% less Oil, 4-in-1 Appliance | Home&Kitchen \| Kitchen&HomeAppliances \| SmallKitchenAppliances \| DeepFatFryers \| AirFryers |
   | Aquadpure Copper + Mineral RO+UV+UF 10 to 12 Liter RO + UV + TDS ADJUSTER Water Purifier with Copper Charge Technology black & copper Best For Home and Office (Made In India) | Home&Kitchen \| Kitchen&HomeAppliances \| WaterPurifiers&Accessories \| WaterFilters&Purifiers |
   | FIGMENT Handheld Milk Frother Rechargeable, 3-Speed Electric Frother for Coffee with 2 Whisks and Coffee Decoration Tool | Home&Kitchen \| Kitchen&HomeAppliances \| SmallKitchenAppliances \| HandBlenders |
   | Multifunctional 2 in 1 Electric Egg Boiling Steamer Egg Frying Pan Egg Boiler Electric Automatic Off with Egg Boiler Machine Non-Stick Electric Egg Frying Pan | Home&Kitchen \| Kitchen&HomeAppliances \| SmallKitchenAppliances \| EggBoilers |
   | Syncwire LTG to USB Cable for Fast Charging Compatible with Phone 5/5C/5S/6/6S/7/8/X/XR/XS Max/11/12/13 Series and Pad Air/Mini, Pod & Other Devices | Computers&Accessories \| Accessories&Peripherals \| Cables&Accessories \| Cables \| USBCables |
   | Campfire Spring Chef Prolix Instant Portable Water Heater Geyser 1Ltr. for Use Home Stainless Steel Baking Rack | Home&Kitchen \| Heating,Cooling&AirQuality \| WaterHeaters&Geysers \| InstantWaterHeaters |
   | Oratech Coffee Frother electric, milk frother electric, coffee beater, cappuccino maker, Coffee Foamer, Mocktail Mixer, Coffee Foam Maker, coffee whisker electric, Froth Maker, coffee stirrers electric, coffee frothers, Coffee Blender | Home&Kitchen \| Kitchen&HomeAppliances \| SmallKitchenAppliances \| HandBlenders |

   Dari tabel 2. didapatkan Hasil rekomendasi dari pendekatan Collaborative Filtering. Produk-produk di atas direkomendasikan berdasarkan peringkat tertinggi dari pengguna yang diberikan sebagai input pada model. Hasil ini didasarkan pada pola atau tren yang ditemukan dalam data pengguna yang serupa. Metode ini mengidentifikasi pengguna dengan preferensi yang mirip dengan pengguna yang diberikan sebagai input, dan merekomendasikan produk yang disukai oleh pengguna serupa tersebut.

   Jika kita lihat hasil rekomendasi, terdapat dua bagian utama:

   1. **Products with high ratings from user**: Daftar ini mencantumkan produk dengan rating tinggi yang diberikan oleh pengguna. Rekomendasi ini didasarkan pada kesesuaian preferensi pengguna yang diberikan dengan produk yang memiliki rating tinggi. 
   2. **Top 10 Products recommendation**: Daftar ini mencantumkan 10 produk teratas yang direkomendasikan. Rekomendasi ini didasarkan pada kesamaan preferensi pengguna yang serupa dengan pengguna yang diberikan sebagai input. Metode Collaborative Filtering mengidentifikasi pengguna dengan pola preferensi yang mirip, dan merekomendasikan produk yang disukai oleh pengguna serupa tersebut. Produk-produk ini mungkin memiliki karakteristik atau atribut yang mirip dengan produk yang diinput, sehingga dianggap relevan dan cocok untuk direkomendasikan.

   Alasan di balik hasil ini adalah bahwa Collaborative Filtering mendasarkan rekomendasinya pada perilaku dan preferensi pengguna serupa. Metode ini mengasumsikan bahwa pengguna yang memiliki pola preferensi yang mirip cenderung memiliki minat yang serupa dalam produk. Dengan menganalisis pola preferensi dan perilaku pengguna, sistem rekomendasi dapat mengidentifikasi produk yang mungkin menarik bagi pengguna yang diberikan.

   **Kelebihan Collaborative Filtering:**

   1. Kemampuan dalam menangani long-tail data: Collaborative filtering mampu merekomendasikan item yang jarang dikonsumsi oleh pengguna atau item yang kurang populer. Model ini mengandalkan data pengguna dan umpan balik mereka untuk memprediksi preferensi pengguna, sehingga dapat memberikan rekomendasi yang lebih beragam.
   2. Tidak bergantung pada informasi konten: Collaborative filtering tidak memerlukan informasi konten yang rinci atau akurat tentang item. Model ini menggunakan pola-pola perilaku pengguna yang ditemukan dari data kolaboratif untuk membuat rekomendasi. Ini berguna dalam situasi di mana informasi konten tidak tersedia atau sulit diperoleh.

   **Kekurangan Collaborative Filtering:**

   1. Masalah cold-start dan sparsity: Collaborative filtering memiliki tantangan dalam menghadapi pengguna baru atau item baru yang belum memiliki data kolaboratif yang cukup. Dalam situasi ini, model akan kesulitan memberikan rekomendasi yang akurat.
   2. Kelemahan dalam mengatasi bubble effect: Collaborative filtering cenderung mendorong pengguna untuk tetap dalam "gelembung" preferensi mereka saat ini. Jika pengguna hanya mendapatkan rekomendasi yang serupa dengan apa yang telah mereka konsumsi sebelumnya, mereka mungkin tidak terpapar pada variasi yang lebih luas atau item yang berbeda.

## **Evaluation**

### Evaluasi Model Content-Based Filtering

1. **Precision**: Metrik presisi digunakan untuk mengukur seberapa tepat model content-based filtering dalam memberikan rekomendasi yang relevan. Presisi dihitung dengan membagi jumlah rekomendasi yang relevan dengan jumlah total rekomendasi yang diberikan. Semakin tinggi nilai presisi, semakin baik model dalam memberikan rekomendasi yang sesuai dengan preferensi pengguna.

   $$ \text{precision} = \frac{\text{Number of Relevant Items Recommended}}{\text{Total Number of Items Recommended}} $$
   
   Dari Hasil Rekomendasi pada Tabel 1. dapat dihitung bahwa terdapat 5 rekomendasi yang relevan dari 5 rekomendasi yang diberikan. Artinya nilai presisinya tinggi.

### Evaluasi Model Collaborative Filtering

1. **Root Mean Squared Error (RMSE)**: Metrik evaluasi yang umum digunakan dalam collaborative filtering adalah RMSE. Metrik ini mengukur seberapa besar kesalahan model dalam memprediksi peringkat atau preferensi pengguna terhadap item. RMSE dihitung dengan menghitung selisih antara peringkat yang diprediksi oleh model dan peringkat yang sebenarnya, kemudian mengambil akar kuadrat dari rata-rata kuadrat selisih tersebut. Semakin rendah nilai RMSE, semakin baik performa model collaborative filtering dalam memprediksi preferensi pengguna.

   ![RMSE](https://github.com/mauluddin12z/Proyek-2-Machine-Learning-Dicoding-Sistem-Rekomendasi/assets/71598808/87be7d95-9207-4bb2-9eae-64d3ed67a3c9)

   Gambar 4. Penerapan RMSE

   Pada gambar 4. terdapat gambar yang menampilkan evaluasi menggunakan RMSE yang dituliskan dengan code program "metrik metrics=[tf.keras.metrics.RootMeanSquaredError()]" 

   Dengan menggunakan metrik evaluasi ini, kita dapat mengukur dan membandingkan performa model collaborative filtering dalam memberikan rekomendasi yang sesuai dengan preferensi pengguna.

   Berikut adalah hasil dari model evaluasi visualisasi matriks :

   ![visualisasi](https://github.com/mauluddin12z/Proyek-2-Machine-Learning-Dicoding-Sistem-Rekomendasi/assets/71598808/23f37da5-57bc-4d9a-b267-a859e63b6787)

   Gambar 5. Visualisasi Model Metrics RMSE

2. **Mean Squared Error (MSE)**. Teknik ini menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi. Berikut kode programnya :

   ```
   from sklearn.metrics import mean_squared_error
   print("MSE dari pada data train = ", mean_squared_error(y_true=y_train, y_pred=model.predict(x_train))/1e3)
   print("MSE dari pada data validation = ", mean_squared_error(y_true=y_val, y_pred=model.predict(x_val))/1e3)
   ```

   Hasil dari MSE pada data train adalah 6.753121698747183e-05 (atau 0.0000675312) dan MSE pada data validation adalah 2.0921279512482833e-05 (atau 0.0000209213). Kedua nilai tersebut sangat kecil, menunjukkan bahwa model kita memiliki performa yang baik dalam memprediksi nilai target pada kedua dataset tersebut.

   ## Conclusion

1.  Model Content-Based Filtering: Model content-based filtering mampu memberikan rekomendasi produk yang relevan dengan preferensi pengguna secara akurat. Pendekatan ini memanfaatkan fitur-fitur konten dari item untuk memprediksi preferensi pengguna dan memberikan rekomendasi yang sesuai. Keuntungan dari model ini adalah kemampuannya dalam memanfaatkan informasi spesifik dari item untuk memberikan rekomendasi yang sesuai dengan preferensi pengguna. Model ini cocok untuk situasi di mana kita memiliki informasi yang kaya tentang atribut dan karakteristik item. Namun, perlu diperhatikan bahwa keterbatasan model content-based filtering terletak pada kemampuannya dalam menemukan item baru yang tidak sesuai dengan preferensi sebelumnya pengguna. Model ini cenderung mempertahankan preferensi yang sudah diketahui dan mungkin tidak menemukan rekomendasi yang inovatif atau berbeda dari preferensi sebelumnya.

2.  Model Collaborative Filtering: Model collaborative filtering mampu memberikan rekomendasi produk yang disukai oleh pengguna dengan akurat. Pendekatan ini memanfaatkan informasi dari pengguna lain untuk memprediksi preferensi pengguna tertentu. Keuntungan dari model ini adalah kemampuannya dalam mengidentifikasi kesamaan preferensi di antara pengguna dan menggunakan informasi ini untuk menghasilkan rekomendasi yang relevan. Model ini dapat menemukan item yang mungkin diminati oleh pengguna berdasarkan pola perilaku dan preferensi pengguna serupa. Namun, perlu diperhatikan bahwa model collaborative filtering memiliki keterbatasan dalam situasi dengan data yang terbatas atau dalam menemukan item baru yang belum dikenal oleh pengguna. Model ini sangat bergantung pada data historis dan preferensi pengguna yang tersedia untuk menghasilkan rekomendasi yang akurat, sehingga jika data tersebut terbatas atau pengguna menghadapi item yang baru, model mungkin mengalami kesulitan dalam memberikan rekomendasi yang relevan.

Dengan demikian, kedua model ini memiliki kelebihan dan kekurangan masing-masing. Model content-based filtering cocok untuk memanfaatkan informasi atribut dan karakteristik item yang tersedia, sedangkan model collaborative filtering efektif dalam memanfaatkan informasi dari pengguna lain. Pemilihan model yang sesuai tergantung pada karakteristik dataset, ketersediaan informasi, dan preferensi pengguna yang ingin ditangani.



## Refrensi

[1]   T. Badriyah, R. Fernando, and I. Syarif, “Sistem Rekomendasi Content Based Filtering Menggunakan Algoritma Apriori,” *Konf. Nas. Sist. Inf.*, vol. 1, no. 1, pp. 554–559, 2018.

[2]   A. E. Wijaya and D. Alfian, “Sistem Rekomendasi Laptop Menggunakan Collaborative Filtering Dan Content-Based Filtering,” *J. Comput. Bisnis*, vol. 12, no. 1, pp. 11–27, 2018.

[3]   E. Erlangga and H. Sutrisno, “Jurnal Manajemen Sistem Informasi dan Teknologi Sistem Rekomendasi Beauty Shop Berbasis Collaborative Filtering,” vol. 10, no. 2, pp. 2745–7265.
