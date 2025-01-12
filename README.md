# Analisis Nilai Pelanggan Maskapai Menggunakan KMeans Clustering

Repositori ini berisi analisis segmentasi pelanggan maskapai menggunakan metode KMeans Clustering berbasis model LRFMC.

## Teknologi yang Digunakan

- **Bahasa Pemrograman**: Python in Jupyter Notebook
- **Dataset**: `flight_data.csv` (Data Pelanggan Maskapai)

## Deskripsi Dataset

Dataset berisi beberapa fitur berikut:

1. **MEMBER_NO**: ID Anggota
2. **FFP_DATE**: Tanggal Bergabung Program Frequent Flyer
3. **FIRST_FLIGHT_DATE**: Tanggal Penerbangan Pertama
4. **GENDER**: Jenis Kelamin Pelanggan
5. **FFP_TIER**: Tingkatan Program Frequent Flyer
6. **WORK_CITY**: Kota Asal
7. **WORK_PROVINCE**: Provinsi Asal
8. **WORK_COUNTRY**: Negara Asal
9. **AGE**: Usia Pelanggan
10. **LOAD_TIME**: Tanggal Data Dikumpulkan
11. **FLIGHT_COUNT**: Jumlah Penerbangan
12. **BP_SUM**: Itinerary
13. **SUM_YR_1**: Total Poin Tahun Pertama
14. **SUM_YR_2**: Total Poin Tahun Kedua
15. **SEG_KM_SUM**: Total Jarak Tempuh (km)
16. **LAST_FLIGHT_DATE**: Tanggal Penerbangan Terakhir
17. **LAST_TO_END**: Jarak Waktu dari Penerbangan Terakhir ke Observasi
18. **AVG_INTERVAL**: Rata-rata Jarak Waktu
19. **MAX_INTERVAL**: Maksimum Jarak Waktu
20. **EXCHANGE_COUNT**: Jumlah Penukaran
21. **avg_discount**: Rata-rata Diskon yang Diperoleh
22. **Points_Sum**: Total Poin yang Diperoleh
23. **Point_NotFlight**: Poin yang Tidak Digunakan

## Model LRFMC

Model LRFMC merupakan pengembangan dari model RFM (Recency, Frequency, Monetary) untuk segmentasi pelanggan. Berdasarkan penelitian Saixin Wu (2022) dan Yang Tao (2020), indikator yang digunakan dalam LRFMC adalah:

1. **L (Length)**: Lama keanggotaan pelanggan (semakin lama, semakin loyal).
2. **R (Recency)**: Jarak waktu dari penerbangan terakhir hingga periode observasi (semakin kecil, semakin baik).
3. **F (Frequency)**: Jumlah penerbangan selama periode observasi (semakin banyak, semakin baik).
4. **M (Monetary)**: Total jarak tempuh penerbangan (semakin besar, semakin baik).
5. **C (Discount Coefficient)**: Rata-rata diskon yang digunakan (semakin kecil, semakin baik).

Fitur yang digunakan untuk analisis:

- **L**: `LOAD_TIME - FFP_DATE` (Lama keanggotaan dalam bulan)
- **R**: `LAST_TO_END`
- **F**: `FLIGHT_COUNT`
- **M**: `SEG_KM_SUM`
- **C**: `avg_discount`

## Hasil Segmentasi

### Cluster yang Terbentuk:

1. **Cluster 0 - (Occasional Flyers)**:
   Pelanggan yang sering terbang dalam jangka waktu terakhir, namun dengan jarak tempuh penerbangan yang pendek dan frekuensi yang rendah. Mereka jarang mendapatkan diskon, terlihat dari TIME_MONTH negatif, serta FLIGHT_COUNT dan avg_discount yang rendah.

2. **Cluster 1 - (Frequent Flyers)**:
   Pelanggan setia yang sering terbang dengan jarak tempuh jauh dan mendapatkan diskon moderat. Mereka memiliki frekuensi penerbangan tertinggi, terlihat dari FLIGHT_COUNT dan SEG_KM_SUM yang positif, dengan avg_discount mendekati rata-rata.

3. **Cluster 2 - (Inactive Members)**:
   Pelanggan yang jarang terbang dalam waktu terakhir dan memiliki jarak tempuh penerbangan yang pendek. Mereka cenderung tidak memanfaatkan diskon, terlihat dari TIME_MONTH tinggi dan avg_discount negatif

4. **Cluster 3 - (Discount Seekers)**:
   Pelanggan yang jarang terbang namun cenderung memanfaatkan diskon ketika melakukan perjalanan. Mereka memiliki avg_discount tertinggi, dengan FLIGHT_COUNT dan SEG_KM_SUM yang rendah.

## Rekomendasi Bisnis

- **Cluster 0 - (Occasional Flyers)** :
  - Membangun dan menjaga hubungan baik dengan Customer
  - Memberikan potongan harga (discount) dengan mengajak teman untuk menggunakan Maskapai
  - Memberikan potongan harga (discount) untuk penerbangan selanjutnya
  - Memberikan point/reward untuk setiap pemesanan maskapai yang dapat direedem dengan voucher diskon atau produk
- **Cluster 1 - (Frequent Flyers)** :
  - Memberikan Ucapan "Terima Kasih" setiap customer menggunakan Maskapai dan Memberikan "Customer Greeting" serta memberikan voucher/discount untuk penerbangan berikutnya.
  - Memberikan point/reward untuk setiap pemesanan maskapai yang dapat direedem dengan voucher diskon atau produk afiliasi dengan maskapai.
  - Memberikan Merchandise dan pelayanan yang spesial kepada customer karena sudah melakukan frekuensi penerbangan tinggi afiliasi dengan maskapai.
- **Cluster 2 - (Inactive Member)** :
  - Memberikan flyer campaign atau informasi terkait promo penerbangan
  - Memberikan newsletter kepada customer terkait discount dan program penerbangan dengan harapan customer untuk menggunakan maskapai kembali
- **Cluster 3 - (Discount Seekers)** :
  - Memberikan flyer campaign atau informasi terkait promo penerbangan
  - Memberikan spesial promo/program penerbangan dengan batas waktu yang ditentukan

## Penutup

Analisis ini membantu maskapai memahami karakteristik pelanggan untuk meningkatkan loyalitas dan memberikan layanan yang lebih personal.

## Instalasi

1. Clone repository ini ke computer/directory local Anda menggunakan perintah berikut:

   ```shell
   git clone https://github.com/danielanputri/Airline-Customer-Value-Analysis-with-KMeans-Clustering
   ```

2. Pastikan Anda memiliki requirements Python yang sesuai dan seluruh pustaka yang diperlukan.
   a. Install library yang diperlukan: scikit-learn, pandas, matplotlib, etc.
   b. Pastikan Python 3.x sudah terinstall
