# Hotel Bookings Data: Unveiling Consumer Trends and Patterns

![image](https://github.com/user-attachments/assets/e849cb15-9487-4143-b02d-68f6516b854a)


## Table of Contents
- [About](#about)
- [Dataset](#dataset)
- [Analisis dan Code](#analisis-dan-code)
- [Storyboard](#storyboard)
- [Dependencies](#dependencies)
- [Tutorial](#tutorial)
- [Summary](#summary)
- [Hasil](#hasil)
- [Anggota Kelompok](#anggota-kelompok)







## About

Proyek ini bertujuan untuk menganalisis data pemesanan hotel guna memahami berbagai pola dan faktor yang memengaruhi keputusan pelanggan. Data yang digunakan mencakup informasi dari dua jenis hotel, yaitu Resort Hotel dan City Hotel. Analisis ini bertujuan untuk memberikan wawasan kepada manajemen hotel dalam meningkatkan pengalaman pelanggan, mengoptimalkan tingkat hunian, dan memaksimalkan pendapatan.

<details>
  <summary>Click here for more details about the project</summary>
  
  ### Fokus Analisis
  - **Perilaku Pelanggan:**
    - **Memahami kapan pelanggan cenderung melakukan pemesanan:** Analisis ini bertujuan untuk mengidentifikasi pola-pola tertentu terkait waktu pemesanan, misalnya, apakah ada periode tertentu dalam setahun ketika pemesanan lebih tinggi.
    - **Mengidentifikasi pola pembatalan pemesanan:** Menganalisis data untuk melihat alasan umum atau pola pembatalan pemesanan, yang dapat memberikan wawasan tentang kebijakan pembatalan yang lebih efektif.

  - **Strategi Harga dan Promosi:**
    - **Menentukan faktor yang memengaruhi harga rata-rata per malam (ADR):** Mengidentifikasi faktor-faktor yang dapat mempengaruhi harga per malam seperti musim, jenis hotel, dan tingkat permintaan.
    - **Menentukan paket layanan yang paling diminati pelanggan:** Menganalisis data untuk mengetahui layanan atau paket yang lebih sering dipesan oleh pelanggan, sehingga dapat menyesuaikan penawaran di masa depan.

  - **Optimalisasi Musiman:**
    - **Mengidentifikasi musim puncak untuk memaksimalkan tingkat hunian:** Menganalisis data untuk mengetahui musim atau bulan tertentu yang menunjukkan tingkat hunian yang lebih tinggi, yang dapat digunakan untuk perencanaan kapasitas.
    - **Strategi untuk meningkatkan pendapatan selama musim sepi:** Mengidentifikasi strategi yang dapat diterapkan untuk meningkatkan tingkat hunian dan pendapatan selama periode permintaan rendah.

  - **Durasi Menginap dan Segmentasi Pasar:**
    - **Menganalisis hubungan antara durasi menginap, jenis pelanggan, dan ADR:** Meneliti durasi menginap rata-rata pelanggan berdasarkan jenis pelanggan untuk menyesuaikan harga dan penawaran yang relevan.
    - **Mengidentifikasi segmen pelanggan dengan kontribusi pendapatan tertinggi:** Menganalisis segmen pasar berdasarkan umur, preferensi, atau perilaku lain untuk fokus pada pelanggan yang memberikan kontribusi pendapatan terbesar.

  ### Manfaat Proyek
  Hasil dari analisis ini dapat digunakan untuk:
  - **Mengembangkan kebijakan harga dinamis:** Berdasarkan data harga dan permintaan, kebijakan harga dapat disesuaikan dengan lebih baik untuk memaksimalkan pendapatan.
  - **Menyesuaikan penawaran promosi sesuai kebutuhan pelanggan:** Menyesuaikan promosi agar lebih relevan dengan segmen pasar dan musim tertentu.
  - **Merancang strategi loyalitas untuk mengurangi tingkat pembatalan:** Mengembangkan program loyalitas yang lebih efektif untuk mengurangi pembatalan pemesanan.
  - **Menentukan kebijakan operasional yang lebih efisien berdasarkan wawasan data:** Memanfaatkan analisis ini untuk merancang kebijakan operasional yang lebih efisien, mengoptimalkan sumber daya, dan meningkatkan pengalaman pelanggan.

</details>







## Dataset

Sumber Dataset

Dataset ini berasal dari data permintaan pemesanan hotel yang dibuka oleh Antonio, Almeida, dan Nunes pada tahun 2019. Data ini mencakup informasi tentang pemesanan hotel baik untuk Resort Hotel maupun City Hotel, serta faktor-faktor yang memengaruhi keputusan pemesanan, pembatalan, dan durasi tinggal.

Dataset ini juga mendukung eksplorasi menggunakan paket analisis data dan time-series seperti tidyverts, yang mencakup:

- **tsibble: Struktur data untuk analisis time-series.**

- **feasts: Ekstraksi fitur dan statistik untuk data time-series.**

- **fable: Pemodelan prediktif untuk forecasting time-series.**

Dataset dapat diakses melalui file [hotels.csv](Dataset/hotels.csv) yang disertakan dalam repositori ini.


### Data Dictionary

Berikut adalah penjelasan variabel dalam dataset:

| **Variabel**                 | **Tipe**  | **Deskripsi**                                                                                                                                               |
|------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| hotel                        | character | Jenis hotel: H1 = Resort Hotel, H2 = City Hotel                                                                                                               |
| is_canceled                  | double    | Status pembatalan: 1 jika dibatalkan, 0 jika tidak                                                                                                           |
| lead_time                    | double    | Jumlah hari antara pemesanan dan tanggal kedatangan                                                                                                         |
| arrival_date_year            | double    | Tahun kedatangan                                                                                                                                             |
| arrival_date_month           | character | Bulan kedatangan                                                                                                                                             |
| stays_in_weekend_nights      | double    | Jumlah malam akhir pekan yang dipesan atau ditempati                                                                                                       |
| adults                       | double    | Jumlah orang dewasa                                                                                                                                          |
| children                     | double    | Jumlah anak-anak                                                                                                                                             |
| babies                       | double    | Jumlah bayi                                                                                                                                                 |
| meal                         | character | Jenis paket makanan (SC, BB, HB, FB)                                                                                                                         |
| country                      | character | Negara asal tamu dalam format ISO 3155–3:2013                                                                                                               |
| market_segment               | character | Segmen pasar (TA = Travel Agents, TO = Tour Operators)                                                                                                      |
| adr                          | double    | Rata-rata biaya harian per malam (Average Daily Rate)                                                                                                      |

Selengkapnya, data dictionary dapat dilihat di dokumentasi resmi datasetnya.


### Cara Mengakses Data

Gunakan perintah berikut untuk membaca dataset:

```python
import pandas as pd

# Membaca dataset dari file CSV
data = pd.read_csv('/content/drive/MyDrive/ANALISIS BIG DATA/DATASET/hotels.csv')

# Menampilkan beberapa baris pertama dari dataset
print(data.head())
```

#### Pembersihan Data

##### Langkah 1 Pemeriksaan Nilai Hilang

```
# Periksa nilai yang hilang
missing_values = data.isnull().sum()
print("\nNilai yang hilang di setiap kolom:\n", missing_values)

data_cleaned = data.dropna()
```

##### Langkah 2 Mengisi Nilai yang Hilang
```
# Hapus kolom agent, company, dan country
data = data.drop(columns=['agent', 'company'])
# Mengisi nilai hilang pada kolom 'children' dengan median
data['children'].fillna(data['children'].median(), inplace=True)
# Mengisi nilai hilang pada kolom 'country' dengan mode
data['country'].fillna(data['country'].mode()[0], inplace=True)
```
##### Langkah 3 pemeriksaan dan menampilkan jumlah nilai yang hilang 
```
print("Nilai yang hilang setelah pembersihan:\n", data.isnull().sum())
```
##### Ringkasan Dataset Setelah Pembersihan

**Sebelum Pembersihan:**

| **Variabel**                    | **Nilai yang Hilang** |
|----------------------------------|-----------------------|
| hotel                            | 0                     |
| is_canceled                      | 0                     |
| lead_time                        | 0                     |
| arrival_date_year                | 0                     |
| arrival_date_month               | 0                     |
| arrival_date_week_number         | 0                     |
| arrival_date_day_of_month        | 0                     |
| stays_in_weekend_nights          | 0                     |
| stays_in_week_nights             | 0                     |
| adults                           | 0                     |
| children                         | 4                     |
| babies                           | 0                     |
| meal                             | 0                     |
| country                          | 488                   |
| market_segment                   | 0                     |
| distribution_channel             | 0                     |
| is_repeated_guest                | 0                     |
| previous_cancellations           | 0                     |
| previous_bookings_not_canceled   | 0                     |
| reserved_room_type               | 0                     |
| assigned_room_type               | 0                     |
| booking_changes                  | 0                     |
| deposit_type                     | 0                     |
| agent                            | 16340                 |
| company                          | 112593                |
| days_in_waiting_list             | 0                     |
| customer_type                    | 0                     |
| adr                              | 0                     |
| required_car_parking_spaces      | 0                     |
| total_of_special_requests        | 0                     |
| reservation_status               | 0                     |
| reservation_status_date          | 0                     |


**Setelah Pembersihan:**

| **Variabel**                    | **Nilai yang Hilang** |
|----------------------------------|-----------------------|
| hotel                            | 0                     |
| is_canceled                      | 0                     |
| lead_time                        | 0                     |
| arrival_date_year                | 0                     |
| arrival_date_month               | 0                     |
| arrival_date_week_number         | 0                     |
| arrival_date_day_of_month        | 0                     |
| stays_in_weekend_nights          | 0                     |
| stays_in_week_nights             | 0                     |
| adults                           | 0                     |
| children                         | 0                     |
| babies                           | 0                     |
| meal                             | 0                     |
| country                          | 0                     |
| market_segment                   | 0                     |
| distribution_channel             | 0                     |
| is_repeated_guest                | 0                     |
| previous_cancellations           | 0                     |
| previous_bookings_not_canceled   | 0                     |
| reserved_room_type               | 0                     |
| assigned_room_type               | 0                     |
| booking_changes                  | 0                     |
| deposit_type                     | 0                     |
| days_in_waiting_list             | 0                     |
| customer_type                    | 0                     |
| adr                              | 0                     |
| required_car_parking_spaces      | 0                     |
| total_of_special_requests        | 0                     |
| reservation_status               | 0                     |
| reservation_status_date          | 0                     |


Langkah-langkah pembersihan data selengkapnya dilakukan dalam file notebook [BOOKING HOTEL.ipynb](BOOKING%20HOTEL.ipynb) yang terdapat dalam repositori ini.






## Analisis dan Code

Analisis data mencakup:

1. Pembersihan data

2. Eksplorasi dan visualisasi data

3. Pemodelan untuk mengidentifikasi tren utama

Kode tersedia di file [BOOKING HOTEL.ipynb](BOOKING%20HOTEL.ipynb). Notebook ini mencakup semua langkah yang dilakukan untuk analisis dataset ini.







## Storyboard

Storyboard proyek ini tersedia dalam file [Storyboard.pdf](Storyboard/Storyboard.pdf) yang mencakup:

1. Evolusi industri perhotelan

2. Perilaku pemesanan pelanggan

3. Pola pemesanan dan pembatalan

4. Strategi harga berdasarkan paket

5. Pola Average Daily Rate (ADR) dan durasi menginap

6. Optimalisasi musiman

7. Strategi retensi untuk City Hotel

8. Kesimpulan dan rencana aksi

File storyboard memberikan visualisasi dan alur cerita dari analisis yang dilakukan, serta rekomendasi untuk implementasi bisnis.







## Dependencies

Berikut adalah pustaka dan perangkat lunak yang diperlukan:

- **windows 10**
- **Python 3.9+**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter Notebook** (opsional untuk menjalankan kode)







## Tutorial

  Langkah- langkah untuk menjalankan proyek ini:

**1. Clone repository**

   ```
   git clone https://github.com/analisisbigdata/finalproject-analisisbigdata.git
   ```
   Perintah ini akan mendownload seluruh repositori ke direktori lokal.

**2. Install Dependencies**

   Setelah repositori berhasil dikloning, langkah berikutnya adalah menginstal dependensi yang diperlukan untuk menjalankan proyek ini. Proyek ini membutuhkan beberapa pustaka Python yang terdaftar dalam file requirements.txt.

Untuk menginstal dependensi, jalankan perintah berikut di terminal atau command prompt setelah memasuki folder repositori yang telah dikloning:

```
pip install -r requirements.txt
```
Perintah ini akan menginstal semua pustaka yang diperlukan, seperti:

- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter Notebook** (opsional, jika ingin menjalankan kode dalam notebook)
Pastikan Python 3.9+ sudah terinstal di sistem.

**3. Jalankan Jupyter Notebook**

   Untuk menjalankan analisis data, buka Jupyter Notebook. Jika Jupyter belum terinstal, gunakan perintah berikut untuk menginstalnya:

   ```
   pip install jupyter
   ```
   Perintah ini akan membuka Jupyter Notebook di browser. Kemudian, buka file BOOKING HOTEL.ipynb untuk memulai analisis data.

**4. Menjalankan Analisis Data**

   Di dalam Jupyter Notebook, terdapat berbagai langkah analisis data, termasuk:

- **Pembersihan data untuk mempersiapkan dataset**
- **Eksplorasi data untuk mencari pola dan wawasan**
- **Pemodelan data untuk mengidentifikasi tren utama**

  Jalankan setiap sel di dalam notebook untuk mengikuti proses analisis.

**5. Lihat Dokumentasi Lengkap**

Untuk informasi lebih lanjut mengenai proyek ini, dapat dilihat dokumentasi lengkapnya melalui tautan berikut:

[README di GitHub](https://github.com/analisisbigdata/finalproject-analisisbigdata/blob/main/README.md)









## Summary


Proyek ini memberikan wawasan mendalam tentang pola pemesanan hotel berdasarkan analisis data yang dikumpulkan dari dua jenis hotel: Resort Hotel dan City Hotel. Tujuan utama dari proyek ini adalah untuk memahami perilaku pelanggan, tren pemesanan, serta faktor-faktor yang mempengaruhi keputusan pelanggan saat memilih hotel. Beberapa temuan kunci yang dihasilkan dari analisis data ini antara lain:

<details>
**1. Waktu Pemesanan yang Paling Sibuk (Bulan Tertentu)**

Analisis mengungkapkan bulan-bulan tertentu yang menunjukkan puncak pemesanan, baik untuk Resort Hotel maupun City Hotel. Pemesanan cenderung lebih tinggi pada bulan-bulan tertentu, yang bisa dipengaruhi oleh musim liburan, perayaan, atau promosi khusus. Dengan pemahaman ini, manajemen hotel dapat merencanakan sumber daya dan mempersiapkan penawaran untuk memenuhi permintaan yang meningkat.

**2. Durasi Tinggal Rata-Rata untuk Setiap Jenis Hotel**

Proyek ini juga menganalisis durasi rata-rata penginapan di kedua jenis hotel. Data menunjukkan bahwa tamu di Resort Hotel cenderung menginap lebih lama dibandingkan tamu di City Hotel. Ini memberikan wawasan mengenai preferensi pelanggan serta kebutuhan untuk menyesuaikan harga dan layanan untuk kedua jenis hotel, agar lebih sesuai dengan tipe pengunjung yang menginap.

**3. Faktor-faktor yang Memengaruhi Pembatalan Pemesanan**

Pembatalan pemesanan adalah isu yang perlu diperhatikan oleh manajemen hotel. Analisis data ini mengidentifikasi berbagai faktor yang dapat menyebabkan pembatalan, seperti harga, jenis paket makanan, dan segmen pasar pelanggan. Dengan mengetahui faktor-faktor ini, hotel dapat merancang strategi untuk mengurangi tingkat pembatalan, seperti penawaran lebih fleksibel atau penyesuaian harga yang lebih kompetitif.

**4. Rekomendasi Strategis untuk Meningkatkan Tingkat Pemesanan**

Berdasarkan temuan analisis, beberapa rekomendasi strategis yang dapat diterapkan oleh hotel untuk meningkatkan tingkat pemesanan antara lain:

- **Penyesuaian Harga Dinamis: Menggunakan harga yang lebih fleksibel berdasarkan permintaan musiman atau waktu pemesanan untuk menarik lebih banyak tamu.**
- **Promosi yang Disesuaikan: Menawarkan paket promo yang menarik, seperti diskon untuk masa menginap lebih lama atau penawaran eksklusif pada bulan dengan pemesanan lebih rendah.**
- **Peningkatan Pengalaman Pelanggan: Meningkatkan pengalaman tamu melalui layanan tambahan yang menarik, seperti layanan transportasi, aktivitas tambahan, atau pengalaman personalisasi.**
- **Meningkatkan Kebijakan Pembatalan: Menawarkan kebijakan pembatalan yang lebih fleksibel untuk meningkatkan rasa aman bagi pelanggan dalam melakukan pemesanan.**
  
**5. Manfaat Proyek**

Analisis ini memberikan manfaat bagi manajemen hotel dalam beberapa hal:

- **Memungkinkan hotel untuk mengoptimalkan harga dan meningkatkan tingkat hunian dengan memanfaatkan data pemesanan untuk menyesuaikan strategi harga.**
- **Memberikan wawasan berharga tentang pelanggan dan tren pemesanan yang dapat digunakan untuk merancang strategi pemasaran yang lebih efektif.**
- **Memberikan data yang dapat digunakan untuk menyesuaikan promosi dan penawaran hotel berdasarkan pola pembatalan atau preferensi pelanggan.**

</details>









## Hasil

Analisis ini bertujuan untuk memahami pola pemesanan hotel berdasarkan data yang tersedia. Dengan mengeksplorasi berbagai fitur seperti jenis hotel, waktu pemesanan, tingkat pembatalan, dan pola musiman, hasil ini memberikan wawasan yang dapat digunakan untuk meningkatkan strategi operasional dan pemasaran hotel. Pemahaman mendalam tentang data pemesanan dapat membantu hotel mengidentifikasi peluang untuk meningkatkan pendapatan dan mengoptimalkan pengalaman pelanggan.

<details>
**Visualisasi Utama**

**1. Grafik Distribusi Jenis Hotel Berdasarkan Pemesanan**

Grafik ini menunjukkan distribusi jumlah pemesanan berdasarkan jenis hotel (Hotel Kota dan Hotel Resor). Hasil analisis mengungkapkan bahwa:

- **Hotel Kota memiliki jumlah pemesanan yang jauh lebih tinggi dibandingkan dengan Hotel Resor.**

- **Hal ini menunjukkan preferensi pelanggan untuk menginap di hotel yang dekat dengan pusat aktivitas seperti perkantoran, tempat wisata perkotaan, atau lokasi strategis lainnya.**

**2. Heatmap Korelasi Antar Fitur**

Visualisasi heatmap digunakan untuk menunjukkan hubungan korelasi antar fitur dalam dataset. Beberapa poin penting dari analisis korelasi adalah:

- **Lead Time memiliki korelasi positif dengan pembatalan (‘is_canceled’), yang berarti semakin lama waktu antara pemesanan dan kedatangan, semakin besar kemungkinan pemesanan akan dibatalkan.**

- **Jumlah tamu dewasa (‘adults’) dan anak-anak (‘children’) menunjukkan korelasi yang signifikan terhadap jumlah total tamu, yang memberikan wawasan tentang komposisi tamu hotel.**

**3. Tren Musiman dalam Pemesanan Hotel**

Tren musiman divisualisasikan menggunakan grafik batang jumlah pemesanan per bulan. Hasilnya menunjukkan:

- **Peningkatan jumlah pemesanan di bulan musim panas, khususnya pada bulan Juli dan Agustus.**

- **Penurunan pemesanan di awal tahun, terutama pada bulan Januari dan Februari, yang menunjukkan pola musiman dalam industri perhotelan.**

- **Pola ini dapat membantu hotel mempersiapkan strategi pemasaran berdasarkan musim, seperti diskon di bulan sepi atau promosi khusus musim liburan.**

</details>

**Kesimpulan**

Hasil visualisasi memberikan wawasan penting bagi manajemen hotel untuk meningkatkan kinerja mereka. Dengan memahami preferensi pelanggan, pola musiman, dan faktor yang memengaruhi pembatalan, hotel dapat:

- **Menyesuaikan strategi harga berdasarkan musim.**

- **Memfokuskan promosi pada jenis hotel tertentu.**

- **Mengelola kebijakan pembatalan untuk mengurangi kerugian akibat pembatalan mendadak.**

  
   




## Anggota Kelompok 

- [Liska Ayuningsih](https://github.com/LiskaAyuningsih) - 202110370311106
- [Ida Masluha](https://github.com/Idamasluha) - 202110370311372
- Dwi Rakhmawati - 202110370311087




