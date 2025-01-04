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


Cara Mengakses Data

Gunakan perintah berikut untuk membaca dataset:

# Membaca dataset langsung
data=read_csv('path/to/hotels.csv')

Data Dictionary

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

Pembersihan Data

Langkah-langkah pembersihan data dilakukan dalam file notebook BOOKING HOTEL.ipynb yang terdapat dalam repositori ini.

