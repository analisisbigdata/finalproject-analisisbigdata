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

tsibble: Struktur data untuk analisis time-series.

feasts: Ekstraksi fitur dan statistik untuk data time-series.

fable: Pemodelan prediktif untuk forecasting time-series.

Dataset dapat diakses melalui file hotels.csv yang disertakan dalam repositori ini.


### Cara Mengakses Data

Gunakan perintah berikut untuk membaca dataset:

```python
import pandas as pd

# Membaca dataset dari file CSV
data = pd.read_csv('/content/drive/MyDrive/ANALISIS BIG DATA/DATASET/hotels.csv')

# Menampilkan beberapa baris pertama dari dataset
print(data.head())
```

### Data Dictionary

Berikut adalah penjelasan variabel dalam dataset:

# Data Description

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


Selengkapnya, data dictionary dapat dilihat di dokumentasi resmi dataset.

### Pembersihan Data

#### Langkah 1 Pemeriksaan Nilai Hilang

```
# Periksa nilai yang hilang
missing_values = data.isnull().sum()
print("\nNilai yang hilang di setiap kolom:\n", missing_values)

data_cleaned = data.dropna()
```

#### Langkah 2 Mengisi Nilai yang Hilang
```
# Hapus kolom agent, company, dan country
data = data.drop(columns=['agent', 'company'])
# Mengisi nilai hilang pada kolom 'children' dengan median
data['children'].fillna(data['children'].median(), inplace=True)
# Mengisi nilai hilang pada kolom 'country' dengan mode
data['country'].fillna(data['country'].mode()[0], inplace=True)
```
#### Langkah 3 pemeriksaan dan menampilkan jumlah nilai yang hilang 
```
print("Nilai yang hilang setelah pembersihan:\n", data.isnull().sum())
```
#### Ringkasan Dataset Setelah Pembersihan

Sebelum Pembersihan:

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


Setelah Pembersihan:

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


# Analisis dan Code

Analisis data mencakup:

1. Pembersihan data

2. Eksplorasi dan visualisasi data

3. Pemodelan untuk mengidentifikasi tren utama

Kode tersedia di file [BOOKING HOTEL.ipynb](BOOKING%20HOTEL.ipynb). Notebook ini mencakup semua langkah yang dilakukan untuk analisis dataset ini.


# Storyboard

Storyboard proyek ini tersedia dalam file Storyboard.pdf yang mencakup:

Evolusi industri perhotelan

Perilaku pemesanan pelanggan

Pola pemesanan dan pembatalan

Strategi harga berdasarkan paket

Pola Average Daily Rate (ADR) dan durasi menginap

Optimalisasi musiman

Strategi retensi untuk City Hotel

Kesimpulan dan rencana aksi

File storyboard memberikan visualisasi dan alur cerita dari analisis yang dilakukan, serta rekomendasi untuk implementasi bisnis.



