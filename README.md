# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[I GUSTI AGUNG ADE SURYA ANANTA]`
- **NIM:** `[2515091033]`
- **Program Studi:** `[SISTEM INFORMASI]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan adalah data `data_statup_saas.csv` yang berisi informasi tentang `Dokumen ini merangkum kinerja bisnis berbagai startup SaaS di Indonesia dalam lima bidang utama, yaitu Keuangan, Proyek, SDM, Pemasaran, dan CRM. Data ini mencakup poin-poin penting seperti total pendapatan, biaya untuk mendapatkan pelanggan baru, nilai keuntungan dari pelanggan, serta persentase pelanggan yang berhenti berlangganan. Secara keseluruhan, informasi ini sangat berguna untuk menilai kesehatan finansial perusahaan, meskipun beberapa bagian data masih perlu dirapikan karena adanya angka yang tidak lengkap atau kurang akurat.`. Variabel kunci dalam dataset ini meliputi `Pendapatan_Tahunan_Miliar_IDR`, `Biaya_Akuisisi_Pelanggan_Juta_IDR`, dan `Nilai_Pelanggan_Juta_IDR`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `Pendapatan_Tahunan_Miliar_IDR` dan `Biaya_Akuisisi_Pelanggan_Juta_IDR` melalui analisis korelasi, serta memprediksi `Nilai_Pelanggan_Juta_IDR` menggunakan `Pendapatan_Tahunan_Miliar_IDR` sebagai prediktor melalui analisis regresi.

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
  - Mean = 33.5
  - Median = 33.08
  - Modus = 3.21
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - Kemiripan antara nilai rata-rata (33,5) dan median (33,08) menunjukkan bahwa distribusi data bisnis ini secara umum cukup stabil dan terpusat di titik tengah. Namun, munculnya angka 3,21 sebagai nilai yang paling sering muncul (modus) memberikan gambaran yang berbeda; meskipun rata-ratanya terlihat tinggi, mayoritas startup dalam dataset ini sebenarnya masih berada di skala yang jauh lebih kecil. Fenomena ini mengisyaratkan adanya ketimpangan, di mana angka rata-rata terangkat oleh beberapa startup besar, sementara sebagian besar pelaku usaha lainnya masih beroperasi di level bawah.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Standar Deviasi = 20.03
  - Range = 2.56 - 68.77
  - Kuartil =   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
                2.56   15.23   33.08   33.50   50.92   68.77 
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
  - Tingginya standar deviasi di angka 20,03 menjadi indikator kuat bahwa data ini sangat bervariasi. Jarak yang lebar antara nilai minimum 2,56 dan maksimum 68,77 memperlihatkan adanya kesenjangan skala bisnis yang cukup besar di antara objek yang diamati. Meskipun nilai median berada di 33,08, sebaran data pada setiap kuartil membuktikan bahwa posisi startup tidak mengumpul di satu titik, melainkan menyebar luas dari skala terkecil hingga terbesar. Secara keseluruhan, angka-angka ini menggambarkan profil pasar yang sangat dinamis dan tidak seragam.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/agungade901-ship-it/projek_statistika/blob/main/results/boxplot_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
  - Secara keseluruhan, pola distribusi data ini menggambarkan dinamika pasar yang didominasi oleh pemain kecil, meski secara statistik terlihat seimbang di angka menengah. Walaupun rata-rata dan median berada di level yang berdekatan, munculnya angka rendah sebagai nilai yang paling sering muncul (modus) menunjukkan bahwa mayoritas startup sebenarnya masih merintis di skala bawah. Hal ini membuktikan bahwa angka rata-rata yang tinggi lebih banyak didorong oleh performa segelintir perusahaan besar, bukan mencerminkan kondisi seluruh pelaku usaha. Singkatnya, terdapat kesenjangan yang nyata antara dominasi kelompok startup kecil dengan beberapa pemain besar yang menguasai nilai pasar.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - p-value = 4.138e-15
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
  - Hasil uji statistik menunjukkan angka p-value yang sangat kecil (4,138e-15), jauh di bawah ambang batas umum 0,05. Hal ini membuktikan bahwa data tidak mengikuti pola distribusi normal, sehingga kita perlu menolak asumsi bahwa sebarannya merata. Secara praktis, temuan ini mengharuskan penggunaan metode statistik non-parametrik dalam analisis lanjutan agar hasilnya tidak bias. Kondisi ini juga menjadi sinyal kuat adanya ketimpangan atau pencilan (data ekstrem) yang membuat karakteristik data menjadi tidak seragam.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/agungade901-ship-it/projek_statistika/blob/main/results/qqplot_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
  - Pada grafik Q-Q Plot, terlihat jelas bahwa titik-titik data tidak sejajar dengan garis lurus, terutama pada area ujung distribusi. Penyimpangan ini mengonfirmasi bahwa data tidak berdistribusi normal dan cenderung memiliki sebaran yang tidak simetris atau melenceng. Kondisi ini memperkuat analisis sebelumnya bahwa karakteristik antar startup sangat beragam, sehingga penerapan model analisis yang mengandalkan asumsi normalitas bisa memicu kesimpulan yang bias atau kurang tepat.n
    

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - Koefisien Korelasi (r) = 0.996
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
  - Nilai koefisien korelasi yang mencapai 0,996 menandakan adanya hubungan positif yang sangat kuat, bahkan hampir sempurna, antara kedua variabel tersebut. Angka ini memberikan gambaran bahwa variabel-variabel tersebut bergerak sangat selaras; ketika satu variabel meningkat, variabel lainnya cenderung ikut naik secara signifikan. Hubungan linear yang sangat erat ini menunjukkan tingkat ketergantungan yang tinggi, sehingga perubahan pada satu sisi dapat dijadikan indikator yang sangat akurat untuk memprediksi nilai pada sisi lainnya.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/agungade901-ship-it/projek_statistika/blob/main/results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
  - Tampilan scatter plot memperlihatkan keselarasan yang jelas dengan hasil koefisien korelasi yang telah dihitung. Titik-titik data membentuk pola garis lurus yang solid dan menanjak tanpa banyak penyimpangan, yang mengonfirmasi adanya hubungan linear yang sangat kuat antar variabel. Karena hampir tidak ada data yang terpencar jauh dari jalur utama, grafik ini secara visual membuktikan bahwa angka 0,996 bukan sekadar hasil hitungan di atas kertas, melainkan mencerminkan keterikatan variabel yang nyata dan sangat stabil.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - (b0) = -1.06
  - (b1) = 0.98
  - Y = -1.06 + 0.98X
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
  - Model regresi ini menunjukkan bahwa setiap kenaikan satu unit pada variabel X akan memicu peningkatan variabel Y sebesar 0,98. Hubungan yang hampir satu-banding-satu ini menandakan adanya pengaruh positif yang sangat kuat dan konsisten di antara keduanya. Sementara itu, nilai intercept sebesar -1,06 berfungsi sebagai titik dasar saat variabel X berada di angka nol. Secara logika bisnis, angka negatif ini bisa diartikan sebagai ambang batas atau beban biaya awal yang harus dilewati sebelum perusahaan mulai mencatatkan pertumbuhan nilai yang nyata.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - R-squared = 0.991 atau 99.1 %"
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
  - Nilai R-squared sebesar 0,991 membuktikan bahwa model regresi ini memiliki tingkat akurasi yang luar biasa, di mana 99,1% perubahan pada variabel dependen dapat dijelaskan secara tepat oleh variabel independennya. Angka ini menegaskan bahwa hampir seluruh pergeseran nilai dalam data dipengaruhi oleh faktor-faktor yang kita amati, dengan menyisakan kurang dari 1% pengaruh dari faktor luar lainnya. Dengan hasil sesolid ini, model tersebut bukan hanya sekadar representasi hubungan antar variabel, tetapi juga menjadi alat prediksi yang sangat andal dan presisi.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/agungade901-ship-it/projek_statistika/blob/main/results/plot_regresi_Biaya_Akuisisi_Pelanggan_Juta_IDR_vs_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
  - Garis regresi pada grafik tersebut menggambarkan hubungan linear yang sangat konsisten antara biaya akuisisi pelanggan dan pendapatan tahunan. Arah garis merah yang menanjak secara stabil menunjukkan bahwa setiap penambahan biaya akuisisi berkorelasi langsung dengan kenaikan pendapatan. Karena sebagian besar titik data berada tepat atau sangat dekat dengan garis tersebut, model ini membuktikan adanya pola ketergantungan yang kuat dan dapat diprediksi. Secara teknis, garis ini menjadi bukti visual bahwa biaya yang dikeluarkan untuk mendapatkan pelanggan merupakan pendorong utama yang sangat efektif bagi pertumbuhan pendapatan perusahaan.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
Secara keseluruhan, analisis ini menunjukkan bahwa biaya akuisisi pelanggan memiliki pengaruh yang sangat besar dan terukur terhadap pendapatan tahunan startup. Meskipun sebaran data memperlihatkan adanya kesenjangan skala bisnis yang cukup lebar di antara para pelaku usaha, model statistik yang digunakan terbukti sangat akurat dalam menggambarkan hubungan tersebut. Temuan utama dari studi ini menegaskan bahwa investasi pada strategi akuisisi pelanggan bukan hanya sekadar biaya operasional, melainkan pendorong utama pertumbuhan finansial yang hasilnya sangat konsisten. Dengan tingkat kepastian model yang hampir sempurna, perusahaan dapat menggunakan pola ini sebagai landasan yang kuat dalam merencanakan target pendapatan di masa depan.
