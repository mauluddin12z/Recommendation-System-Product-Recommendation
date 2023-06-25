# Laporan Proyek 2 Machine Learning - Muhammad Hidayat Mauluddin

## Domain Proyek

Dalam era digital yang terus berkembang, penggunaan sistem rekomendasi produk telah menjadi bagian integral dari platform e-commerce dan situs web lainnya. Sistem ini membantu pengguna menemukan produk yang sesuai dengan preferensi mereka, meningkatkan pengalaman belanja online, dan mendorong penjualan. Oleh karena itu, pengembangan sistem rekomendasi produk menjadi topik yang menarik dalam bidang ilmu komputer dan bisnis[1].

Ada banyak pendekatan dalam sistem rekomendasi produk. Contohnya *Content Based Filtering* dan *Collaborative Filtering*. Secara garis besar *Content Based Filtering* adalah metode pendekatan yang dilakukan dengan menggunakan data atau item yang sudah ada sebagai dasar dalam memberikan rekomendasi[2]. Sedangkan *Collaborative Filtering* adalah sebuah model atau metode pendekatan yang dilakukan menggunakan item item atau pendapat dari pengguna lain. Item item yang dimaksud dalam kasus ini adalah rating dari user. Data rating tersebut akan digunakan sebagai dasar untuk merekomendasikan item item yang relevan kepada pengguna[3]. Dengan metode atau pendekatan sistem rekomendasi tersebut diharapkan dapat meningkatkan pengalaman belanja online dari pengguna yang pada akhirnya dapat meningkatkan penjualan.



## Business Understanding

### Problem Statements

1. Bagaimana cara membuat sistem rekomendasi menggunakan model machine learning dengan pendekatan *Content Based Filtering* ?
1. Bagaimana cara membuat sistem rekomendasi menggunakan model machine learning dengan pendekatan *Collaborative Filtering* ?

### Goals

1. Dapat merekomendasikan produk yang disukai oleh pengguna dengan akurat menggunakan Machine Learning dengan pendekatan *Content Based Filtering*.
1. Dapat merekomendasikan produk yang disukai oleh pengguna dengan akurat menggunakan Machine Learning dengan pendekatan *Collaborative Filtering*.

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

## Data Preparation

Pada tahap ini akan dilakukan persiapan untuk data yang akan digunakan agar selanjutnya akan dapat dilakukan pemodelan pada data teresbut, contohnya adalah:

- Mengatasi missing value : menyeleksi data apakah data tersebut ada yang kosong atau tidak, jika terdapat data yang kosong maka akan dihapus.
- Membersihkan data dari kata atau character yang tidak relevan. pada proyek ini terdapat character "|" pada kolom rating yang mengakibatkan tipe data pada kolom rating tidak bisa dirubah menjadi float. Oleh karena itu harus dilakukan data cleaning.
- Merubah tipe data : Merubah tipe data yang diperlukan seperti rating.
- Membagi data menjadi data training dan validasi
- Mengurutan data berdasarkan product id.
- Mengatasi duplikasi data.
- Mengkonversi data menjadi list
- Membuat dictionary.
- Menggunakan TfidfVectorizer untuk melakukan pembobotan.
- melakukan preprocessing untuk menghilangkan permasalahan permasalahan pada data yang dapat mengganggu proses pemodelan.

## **Modeling** and Result

Terdapat  dua model atau algoritma yang digunakan untuk sistem rekomendasi ini, yaitu *Content Based Filtering* dan *Collaborative Filtering*

Berikut adalah hasil dari algoritma tersebut:

### ***Content Based Filtering***

   Berikut adalah tabel rekomendasi dari produk "Wayona Nylon Braided USB to Lightning Fast Charging and Data Sync Cable Compatible for iPhone 13, 12,11, X, 8, 7, 6, 5, iPad Air, Pro, Mini (3 FT Pack of 1, Grey)" yang kategorinya "Computers&Accessories|Accessories&Peripherals|Cables&Accessories|Cables|USBCables"

   Tabel 1. Tabel Rekomendasi dari produk yang diinputkan.

   | index | product\_name                                                | category                                                     |
   | ----- | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | 0     | Ambrane Unbreakable 60W / 3A Fast Charging 1\.5m Braided Type C to Type C Cable for Smartphones, Tablets, Laptops & Other Type C Devices, PD Technology, 480Mbps Data Sync \(RCTT15, Black\) | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 1     | Belkin Apple Certified Lightning to USB Charge and Sync Tough Braided Cable for iPhone, iPad, Air Pods, 3\.3 feet \(1 meters\) – Black | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 2     | Portronics Konnect CL 20W POR-1067 Type-C to 8 Pin USB 1\.2M Cable with Power Delivery & 3A Quick Charge Support, Nylon Braided for All Type-C and 8 Pin Devices, Green | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 3     | Portronics Konnect L 1\.2Mtr, Fast Charging 3A Micro USB Cable with Charge & Sync Function \(Grey\) | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |
   | 4     | Portronics Konnect Spydr 31 3-in-1 Multi Functional Cable with 3\.0A Output, Tangle Resistant, 1\.2M Length, Nylon Braided\(Zebra\) | Computers&Accessories&#124;Accessories&Peripherals&#124;Cables&Accessories&#124;Cables&#124;USBCables |

**Kelebihan Content-Based Filtering:**

1. Independen dari data pengguna: Content-based filtering tidak memerlukan data pengguna lain atau kolaborasi antar pengguna. Model ini hanya mempertimbangkan preferensi pengguna yang bersangkutan dan karakteristik konten item untuk memberikan rekomendasi. Oleh karena itu, tidak ada masalah dengan cold-start problem saat ada pengguna baru atau item baru yang ditambahkan ke sistem.
2. Kemampuan dalam merekomendasikan item baru: Content-based filtering dapat merekomendasikan item yang belum pernah dikonsumsi oleh pengguna sebelumnya. Hal ini memungkinkan pengguna untuk menemukan item baru yang mungkin sesuai dengan preferensi mereka berdasarkan fitur dan karakteristik yang disukai.

**Kekurangan Content-Based Filtering:**

1. Kurangnya keberagaman rekomendasi dari produk dikarenakan Model content based filtering cenderung memberikan rekomendasi berdasarkan klasifikasi atau kategori dari produk.

   

### ***Collaborative Filtering***

   ![image-20230625212720944](https://github.com/mauluddin12z/Proyek-2-Machine-Learning-Dicoding-Sistem-Rekomendasi/assets/71598808/fa0a3563-a0e8-4066-947e-3621c5d444ad)

   Gambar 1. Gambar top 10 rekomendasi produk menggunakan model *Collaborative Filtering*

   **Kelebihan Collaborative Filtering:**

   1. Kemampuan dalam menangani long-tail data: Collaborative filtering mampu merekomendasikan item yang jarang dikonsumsi oleh pengguna atau item yang kurang populer. Model ini mengandalkan data pengguna dan umpan balik mereka untuk memprediksi preferensi pengguna, sehingga dapat memberikan rekomendasi yang lebih beragam.
   2. Tidak bergantung pada informasi konten: Collaborative filtering tidak memerlukan informasi konten yang rinci atau akurat tentang item. Model ini menggunakan pola-pola perilaku pengguna yang ditemukan dari data kolaboratif untuk membuat rekomendasi. Ini berguna dalam situasi di mana informasi konten tidak tersedia atau sulit diperoleh.

   **Kekurangan Collaborative Filtering:**

   1. Masalah cold-start dan sparsity: Collaborative filtering memiliki tantangan dalam menghadapi pengguna baru atau item baru yang belum memiliki data kolaboratif yang cukup. Dalam situasi ini, model akan kesulitan memberikan rekomendasi yang akurat.
   2. Kelemahan dalam mengatasi bubble effect: Collaborative filtering cenderung mendorong pengguna untuk tetap dalam "gelembung" preferensi mereka saat ini. Jika pengguna hanya mendapatkan rekomendasi yang serupa dengan apa yang telah mereka konsumsi sebelumnya, mereka mungkin tidak terpapar pada variasi yang lebih luas atau item yang berbeda.

## **Evaluation**

### Evaluasi Model Content-Based Filtering

1. **Precision**: Metrik presisi digunakan untuk mengukur seberapa tepat model content-based filtering dalam memberikan rekomendasi yang relevan. Presisi dihitung dengan membagi jumlah rekomendasi yang relevan dengan jumlah total rekomendasi yang diberikan. Semakin tinggi nilai presisi, semakin baik model dalam memberikan rekomendasi yang sesuai dengan preferensi pengguna.

   Dari Hasil Rekomendasi pada Tabel 1. dapat dihitung bahwa terdapat 5 rekomendasi yang relevan dari 5 rekomendasi yang diberikan. Artinya nilai presisinya tinggi.

### Evaluasi Model Collaborative Filtering

1. **Root Mean Squared Error (RMSE)**: Metrik evaluasi yang umum digunakan dalam collaborative filtering adalah RMSE. Metrik ini mengukur seberapa besar kesalahan model dalam memprediksi peringkat atau preferensi pengguna terhadap item. RMSE dihitung dengan menghitung selisih antara peringkat yang diprediksi oleh model dan peringkat yang sebenarnya, kemudian mengambil akar kuadrat dari rata-rata kuadrat selisih tersebut. Semakin rendah nilai RMSE, semakin baik performa model collaborative filtering dalam memprediksi preferensi pengguna.

Dengan menggunakan metrik evaluasi ini, kita dapat mengukur dan membandingkan performa model content-based filtering dan collaborative filtering dalam memberikan rekomendasi yang sesuai dengan preferensi pengguna.

## Conclusion

1.  Berdasarkan metrik evaluasi presisi, model content-based filtering mampu memberikan rekomendasi produk yang relevan dengan preferensi pengguna secara akurat. Pendekatan ini efektif dalam memanfaatkan fitur-fitur konten dari item untuk memprediksi preferensi pengguna dan memberikan rekomendasi yang sesuai. Namun, perlu diperhatikan bahwa keterbatasan model content-based filtering terletak pada kemampuannya dalam menemukan item baru yang tidak sesuai dengan preferensi sebelumnya pengguna.

2. Berdasarkan metrik evaluasi RMSE, model collaborative filtering mampu memberikan rekomendasi produk yang disukai oleh pengguna dengan akurat. Pendekatan ini memanfaatkan informasi dari pengguna lain untuk memprediksi preferensi pengguna tertentu. Dengan membandingkan pola perilaku dan preferensi pengguna serupa, model collaborative filtering dapat memberikan rekomendasi yang relevan dan menemukan item yang mungkin diminati oleh pengguna tersebut. Namun, perlu diperhatikan bahwa model collaborative filtering memiliki keterbatasan dalam situasi dengan data yang terbatas atau dalam menemukan item baru yang belum dikenal oleh pengguna.

## Refrensi

[1]   T. Badriyah, R. Fernando, and I. Syarif, “Sistem Rekomendasi Content Based Filtering Menggunakan Algoritma Apriori,” *Konf. Nas. Sist. Inf.*, vol. 1, no. 1, pp. 554–559, 2018.

[2]   A. E. Wijaya and D. Alfian, “Sistem Rekomendasi Laptop Menggunakan Collaborative Filtering Dan Content-Based Filtering,” *J. Comput. Bisnis*, vol. 12, no. 1, pp. 11–27, 2018.

[3]   E. Erlangga and H. Sutrisno, “Jurnal Manajemen Sistem Informasi dan Teknologi Sistem Rekomendasi Beauty Shop Berbasis Collaborative Filtering,” vol. 10, no. 2, pp. 2745–7265.
