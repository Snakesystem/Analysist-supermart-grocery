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

Pada kolom `region` terdapat 1 wilayah yang merupakan outlier dimana hanya terdapat 1  nilai dan saya putuskan untuk menghapusbaris tersebut karena:
- Hanya ada 1 baris yang memiliki  nilai tersebut
- Letaknya kebetulan berada di awal index jadi tidak akan mempengaruhi index waktu

![rg](https://user-images.githubusercontent.com/90812378/178674690-a628ded3-eebf-4920-89f9-55f72a7fe237.png)

Ditemukan juga pada kolom `country` dimana dari banyaknya data ternyata hanya ada 1 negara maka kolom tersebut juga saya putuskan untuk menghapusnya terkait kolom tersebut tidak memiliki banyak informasi dan tidak terlalu bermanfaat pada analisis ini.

## Exploratory Data Analysis
Analisis ini digunakan untuk mencari nilai nilai tertentu yang bisa di peroleh dari dataset:

**Categorical data Distribution**

![spd](https://user-images.githubusercontent.com/90812378/178676333-9b59c76b-e7b9-47e2-9791-e30bba343afb.png)

Distribusi data `sale_price` terlihat memiliki keseragaman dimana dari distribusi ini `Supermart Grocary` tidak terjadi adanya penurunah penjualan yang signifikan, artinya dari tahun ke tahun penjualan selalu stabil

