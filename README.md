# Analysist Supermart Grocery
My documentation learn data analysis

## Introduction
Proyek analisis data ini dilakukan dengan menggunakan dataset Supermart Grocery Sales. Ini adalah kumpulan data umum dengan sekitar 10 ribu entri dan 11 kolom, dan dimaksudkan untuk digunakan sebagai kumpulan data praktik.

Dokumentasi Dataset bisa dilihat pada https://www.kaggle.com/datasets/mohamedharris/supermart-grocery-sales-retail-analytics-dataset

## Cleaning Dataset
Langkah - langkah :
1. Mengganti nama kolom yang memiliki spaci dan huruf kapital
2. Mengecek tipe data tiap kolomnya
3. Cek dan Mengatasi N/A serta data duplikat
4. Cek apakah ada anomali baik kesalahan input data atau yang lainya

#### 1. Rename column
langkah ini bertujuan untuk merubah nana kolom yang memiliki penamaan yang di awali huruf kapital dan menggunakan spasi daam dua kata menjadi `lowercase` dan `non space`
#### 2. Check type 
Langkah ini digunakan untuk melihat tipe - tipe data di setiap kolom. Dan ditemukan kolom `order_date` bertype object yang seharusnya adalah type datetime
#### 3. Check N/A
Dalam data ini tidak ditemukan missing value
#### 4. Check Anomali
Dalam kasus kali ini ditemukan beberapa keunikan dalam data yaitu:

Pada kolom `region` terdapat 1 wilayah yang merupakan outlier dimana hanya terdapat 1  nilai yaitu `North`. Maka saya putuskan untuk menghapusbaris tersebut karena:
- Hanya ada 1 baris yang memiliki  nilai tersebut
- Letaknya kebetulan berada di awal index jadi tidak akan mempengaruhi index waktu

![rg](https://user-images.githubusercontent.com/90812378/178674690-a628ded3-eebf-4920-89f9-55f72a7fe237.png)

Ditemukan juga pada kolom `country` dimana dari banyaknya data ternyata hanya ada 1 negara maka kolom tersebut juga saya putuskan untuk menghapusnya terkait kolom tersebut tidak memiliki banyak informasi dan tidak terlalu bermanfaat pada analisis ini.

## Exploratory Data Analysis
Analisis ini digunakan untuk mencari nilai nilai tertentu yang bisa di peroleh dari dataset:

**Numerical data Distribution**

![spd](https://user-images.githubusercontent.com/90812378/178676333-9b59c76b-e7b9-47e2-9791-e30bba343afb.png)

Distribusi data `sale_price` terlihat memiliki keseragaman dimana dari distribusi ini `Supermart Grocary` tidak terjadi adanya penurunah penjualan yang signifikan, artinya dari tahun ke tahun penjualan selalu stabil

![prd](https://user-images.githubusercontent.com/90812378/178680013-a3b8bc57-9ac5-4a34-973a-150c33efd9e7.png)

Jika dilihat dari distribusi `profit`, distribusinya lebih condong ke kiri. Ini semakin menarik apakah distribusi ini dikarenakan laba perusahaan semakin menurun atau ada hal lain yang mempengaruhinya.

**Trend Sale & Profit/year

![ty](https://user-images.githubusercontent.com/90812378/178680743-c7413808-c166-4aba-b2a6-4527a4a920a9.png)

Ternyata `sale_price` dan `profit` selalu naik di setiap tahunya meskipun kenaikan laba tidak setinggi kenaikan tingkat penjualannya. Namun saya semakin penasaran jika setiap tahunya jika penjualan naik maka laba juga akan naik ? bagaimana jika dilihat dari penjualan dan laba perbulanya ?

![tb](https://user-images.githubusercontent.com/90812378/178681600-37aaed5c-b12a-4c1d-b409-7d9974679eda.png)

Ternyata benar, jika penjualan naik maka laba juga naik jika turun maka laba juga akan turun. Namun ada yang menarik, dimana tren di setiap bulanya mengalami keadaan yang sama baik naik ataupun turun.

![tb2](https://user-images.githubusercontent.com/90812378/178682596-ecf672eb-36d4-4d0b-9ec9-7b5de840b5f9.png)

Tren tersebut terjadi karena di awal bulan penjualan selalu pengalami penurunan namun diakhir bulan penjualan mengalami kenaikan. dari sini saya menjadi penasaran kira-kira berapa nilai korelasi antara `profit` dan `sale_price`

![hm](https://user-images.githubusercontent.com/90812378/178683143-9e952062-820d-4c91-9b5f-c1dc111035af.png)

Dari korelasi heatmap nilai keterkaitan antara `profit` dan `sale_price` sebesar 65% pantas saja setiap kali penjualan naik atau turun maka laba akan mengalami hal yang sama. Kemudian saya akan mencobanya untuk menentukan seberapa dekat korelasinya dengan scatter plot

![sp](https://user-images.githubusercontent.com/90812378/178683674-6f818135-29b0-4028-8b5d-9c029dfee230.png)

**Get variance Product**

Setelah melihat hubungan antara kolom-kolom numerical maka kemudian saya akan mencari tahu tentang variasi antar `category` produk

![cp](https://user-images.githubusercontent.com/90812378/178684862-781e2dd2-45cc-4bc0-a1d9-a13ae9fa736e.png)

Berdasarkan `category` produk terlihat angka antara harga asli pendapatan dan penerapan discount terlihat tidak begitu jauh perbandinganya. Namun apakah untuk penjualan per `sub_category` memiliki variance yang tidak begitu jauh juga ?

![sd](https://user-images.githubusercontent.com/90812378/178686139-dcd24f25-004e-4695-9fa4-2beb594afdce.png)

Ternyata jika dilihat dari standar deviasi penjualan produk memang tidak ada keberagman yang jauh dimana penjualan produk di data ini terlihat laku terjual untuk setiap produk yang tersedia. Namun produk dengan tingkat pemesanan yang tinggi pasti adanya dimana produk produk tersebut adalah sebagai berikut:

![ring](https://user-images.githubusercontent.com/90812378/178687727-3fc78d62-087d-4b5a-88e7-1b9e87f5a8c9.png)
![hight](https://user-images.githubusercontent.com/90812378/178687122-fa7c9f8d-b7d4-406e-b4fa-5b47d20b06f6.png)

Dari tabel rangkuman ini terlihat bahwa meskipun kategori Minuman Kesehatan memiliki jumlah penjualan tertinggi, dan juga memiliki keuntungan per pesanan yang relatif tinggi. Baik jumlah penjualan maupun keuntungan per pesanan yang tinggi memberikan kontribusi pada kategori minuman kesehatan yang memiliki total keuntungan tertinggi dari semua produk.

Selain itu, melihat sub kategori Ikan, meskipun memiliki jumlah penjualan yang lebih rendah dari rata-rata (434 seperti yang ditunjukkan di atas), ia mampu memiliki total keuntungan yang lebih tinggi berkat memiliki laba per pesanan tertinggi hampir 400.

Sedangkan untuk sub kategori Beras, keuntungan per pesanan sebenarnya tidak rendah, yaitu 384 per pesanan, namun jumlah penjualannya rendah sehingga laba keseluruhannya lebih rendah.

Terakhir, melihat sub kategori ayam, ia menderita karena tidak ada penjualan dan laba per pesanan yang lebih rendah, sehingga tidak mengherankan jika laba keseluruhannya juga lebih rendah.

## Conclution
Hasil temuan pada analisis data ini afdalah sebagai berikut:

1. Harga jual barang didistribusikan secara merata, sedangkan jumlah keuntungan dan diskon adalah distribusi miring yang tepat.
2. Tren peningkatan dari waktu ke waktu dalam jumlah penjualan, jumlah penjualan, dan laba diamati
3. Sebuah pola diamati ketika pesanan dikategorikan berdasarkan bulan,
  - Ada jumlah penjualan yang lebih tinggi di bulan September, November dan Desember
  - Ada jumlah penjualan yang lebih rendah di bulan Januari dan Februari
3. Tingkat korelasi positif tertentu ada ketika memeriksa laba terhadap harga jual (corr = 0,25) dan jumlah diskon (corr = 0,35) Dengan mengelompokkan data dengan sub kategori dan menggunakan metrik total laba, jumlah penjualan, dan laba per pesanan, 4 sub kategori dipilih.
4. Performa lebih baik - Minuman Kesehatan dan Ikan, Performa lebih buruk - Nasi dan Ayam









