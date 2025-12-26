# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[Komang Arlan Airlangga]`
- **NIM:** `[2515091135]`
- **Program Studi:** `[Sistem Informasi]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan adalah data `data_startup_saas.csv` yang berisi informasi tentang `File tersebut berisi data tentang beberapa startup SaaS beserta kondisi usahanya. Di dalamnya tercantum nama startup dan jenis layanan yang mereka tawarkan. Selain itu, ada informasi mengenai pendapatan setiap tahun, biaya yang dikeluarkan untuk mendapatkan pelanggan, serta nilai pelanggan bagi perusahaan. Data ini juga menunjukkan tingkat churn, yaitu jumlah pelanggan yang berhenti menggunakan layanan. Secara keseluruhan, data tersebut membantu kita memahami bagaimana kinerja keuangan, strategi pemasaran, dan tingkat loyalitas pelanggan dari masing-masing startup.
`. Variabel kunci dalam dataset ini meliputi `Pendapatan_Tahunan_Miliar_IDR`, `Biaya_Akuisisi_Pelanggan_Juta_IDR`, dan `Nilai_Pelanggan_Juta_IDR`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `Pendapatan_Tahunan_Miliar_IDR` dan `Biaya_Akuisisi_Pelanggan_Juta_IDR` melalui analisis korelasi, serta memprediksi `Nilai_Pelanggan_Juta_IDR` menggunakan `Pendapatan_Tahunan_Miliar_IDR` sebagai prediktor melalui analisis regresi.

---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...*
  - Mean =  33.5"
  - Median = 33.08"
  - Modus =  3.21"
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
Nilai **mean sebesar 33,5** menunjukkan rata-rata data secara keseluruhan. Artinya, jika semua nilai dalam data dijumlahkan lalu dibagi dengan jumlah data, hasilnya berada di angka 33,5. **Median sebesar 33,08** berarti nilai tengah dari data, sehingga setengah data berada di bawah 33,08 dan setengah lainnya berada di atas nilai tersebut. Sementara itu, **modus sebesar 3,21** menunjukkan nilai yang paling sering muncul dalam data. Dari ketiga nilai ini dapat disimpulkan bahwa pusat data berada di kisaran 33, namun adanya perbedaan yang cukup jauh antara modus dan mean/median mengindikasikan bahwa data tidak tersebar secara merata dan kemungkinan terdapat nilai ekstrem yang memengaruhi sebaran data.

- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Standar Deviasi = 20.03"
  - Range = 2.56 - 68.77"
  - Kuartil =  Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
               2.56   15.23   33.08   33.50   50.92   68.77
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
Berdasarkan nilai **standar deviasi sebesar 20,03**, dapat diketahui bahwa data tersebar cukup jauh dari nilai rata-ratanya, sehingga variasi datanya tergolong besar. **Range data dari 2,56 hingga 68,77** menunjukkan selisih yang lebar antara nilai terendah dan tertinggi, menandakan adanya perbedaan yang cukup mencolok dalam data. Dari nilai **kuartil**, terlihat bahwa 50% data berada di antara **15,23 (kuartil pertama)** dan **50,92 (kuartil ketiga)**, dengan **median 33,08** sebagai titik tengah. Secara keseluruhan, nilai-nilai ini menunjukkan bahwa data memiliki sebaran yang luas dan tidak terkonsentrasi pada satu nilai saja.

- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/komang-arlan-airlangga/uas-project-Rstudio/blob/main/results/boxplot_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
Dari boxplot tersebut dapat dilihat bahwa **biaya akuisisi pelanggan** memiliki penyebaran yang cukup luas. Sebagian besar data berada di kisaran tengah, dengan median sekitar nilai rata-rata biaya akuisisi. Kotak yang relatif lebar menunjukkan bahwa perbedaan biaya antar startup cukup besar. Whisker yang memanjang ke nilai tinggi menandakan adanya beberapa startup yang mengeluarkan biaya akuisisi pelanggan jauh lebih besar dibandingkan yang lain. Secara keseluruhan, bentuk distribusi ini menunjukkan bahwa biaya akuisisi pelanggan tidak seragam dan sangat bergantung pada strategi serta kondisi masing-masing startup.


### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - p-value = 4.138e-15
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
  - Nilai p-value sebesar 4,138 × 10⁻¹⁵ sangat kecil dan jauh di bawah batas umum 0,05. Hal ini menunjukkan bahwa hipotesis nol (data berdistribusi normal) ditolak, sehingga data tidak terdistribusi normal.
  - Implikasinya, analisis yang mengasumsikan distribusi normal (seperti uji t atau ANOVA klasik) kurang tepat digunakan pada data ini tanpa transformasi terlebih dahulu. Oleh karena itu, lebih disarankan menggunakan metode statistik nonparametrik atau melakukan transformasi data agar hasil analisis menjadi lebih akurat dan dapat dipercaya.

Implikasinya, analisis yang mengasumsikan distribusi normal (seperti uji *t* atau ANOVA klasik) kurang tepat digunakan pada data ini tanpa transformasi terlebih dahulu. Oleh karena itu, lebih disarankan menggunakan **metode statistik nonparametrik** atau melakukan **transformasi data** agar hasil analisis menjadi lebih akurat dan dapat dipercaya.

- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text]https://github.com/komang-arlan-airlangga/uas-project-Rstudio/blob/main/results/qqplot_Biaya_Akuisisi_Pelanggan_Juta_IDR.png
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
  - Pada Q–Q plot tersebut, titik-titik data tidak mengikuti garis lurus secara konsisten. Terlihat adanya pola melengkung, terutama pada bagian awal dan akhir, di mana titik-titik menjauh dari garis referensi. Hal ini menunjukkan bahwa data tidak berdistribusi normal.
  - Artinya, sebaran data memiliki penyimpangan dari normalitas, kemungkinan berupa kemencengan (skewness) atau adanya nilai ekstrem. Temuan ini sejalan dengan hasil uji normalitas sebelumnya yang menghasilkan p-value sangat kecil. Oleh karena itu, analisis statistik yang mengasumsikan distribusi normal sebaiknya dihindari atau data perlu ditransformasikan terlebih dahulu.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - (r) = 0.996"
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
  - Nilai koefisien korelasi **(r) = 0,996** menunjukkan adanya **hubungan yang sangat kuat dan positif** antara dua variabel yang diuji. Artinya, ketika nilai salah satu variabel meningkat, nilai variabel lainnya juga cenderung ikut meningkat. Kekuatan korelasi yang mendekati 1 menandakan bahwa hubungan antarvariabel sangat erat dan perubahan pada satu variabel hampir selalu diikuti oleh perubahan yang searah pada variabel lainnya.

- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text]https://github.com/komang-arlan-airlangga/uas-project-Rstudio/blob/main/results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR.png
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
  - Pola pada scatter plot **mendukung hasil koefisien korelasi** yang sangat tinggi. Titik-titik data terlihat membentuk **pola naik yang jelas**, di mana semakin besar pendapatan tahunan, semakin tinggi pula biaya akuisisi pelanggan. Sebagian besar titik mengikuti arah **garis tren linear**, menunjukkan hubungan yang kuat dan searah. Hal ini konsisten dengan nilai korelasi **(r = 0,996)**, sehingga dapat disimpulkan bahwa terdapat **hubungan positif yang sangat kuat** antara pendapatan tahunan dan biaya akuisisi pelanggan.


### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - (b0) = -1.06
  - (b1) = 0.98
  - Y = -1.06 + 0.98X
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
  - Nilai intercept (b0) = −1,06 menunjukkan nilai variabel Y ketika variabel X bernilai nol. Dalam konteks data ini, artinya jika pendapatan tahunan dianggap nol, maka biaya akuisisi pelanggan diperkirakan bernilai −1,06. Nilai ini lebih bersifat matematis dan tidak terlalu bermakna secara nyata, tetapi tetap diperlukan untuk membentuk persamaan regresi.
  - Sementara itu, nilai slope (b1) = 0,98 menunjukkan arah dan besarnya pengaruh variabel X terhadap Y. Artinya, setiap kenaikan 1 satuan pendapatan tahunan, biaya akuisisi pelanggan diperkirakan meningkat sebesar 0,98 satuan. Nilai slope yang mendekati 1 ini menunjukkan hubungan positif yang sangat kuat, di mana peningkatan pendapatan tahunan diikuti oleh peningkatan biaya akuisisi pelanggan.

- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*`
  - R-squared = 0.991 atau 99.1 %"
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
  - **Interpretasi:**
  - Nilai **R-squared sebesar 0,991 atau 99,1%** menunjukkan bahwa **99,1% variasi pada variabel dependen** dapat dijelaskan oleh model regresi yang digunakan. Artinya, perubahan pada variabel independen memiliki pengaruh yang sangat besar dalam menjelaskan perubahan variabel dependen. Model regresi ini tergolong **sangat baik**, karena hanya sekitar **0,9% variasi data** yang dipengaruhi oleh faktor lain di luar model.

- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text]https://github.com/komang-arlan-airlangga/uas-project-Rstudio/blob/main/results/plot_regresi_Biaya_Akuisisi_Pelanggan_Juta_IDR_vs_Pendapatan_Tahunan_Miliar_IDR.png
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
  - Garis regresi pada grafik menunjukkan **hubungan linear yang sangat kuat dan searah** antara biaya akuisisi pelanggan dan pendapatan tahunan. Arah garis yang menanjak menandakan bahwa semakin besar biaya yang dikeluarkan untuk memperoleh pelanggan, semakin tinggi pula pendapatan tahunan yang dihasilkan.
  - Titik-titik data yang berada sangat dekat dengan garis regresi menunjukkan bahwa model mampu merepresentasikan hubungan antarvariabel dengan sangat baik. Hal ini sejalan dengan nilai **R-squared yang tinggi**, yang menandakan bahwa sebagian besar variasi pendapatan tahunan dapat dijelaskan oleh biaya akuisisi pelanggan. Secara keseluruhan, garis regresi ini menggambarkan bahwa perubahan pada biaya akuisisi pelanggan berpengaruh besar dan konsisten terhadap peningkatan pendapatan tahunan.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
