# P2_Probstat_B_5025201077
Praktikum Probabilitas dan Statistik

### Handitanto Herprasetyo
### 5025201077

#### 1. Seorang peneliti melakukan penelitian mengenai pengaruh aktivitas 𝐴 terhadap kadar saturasi oksigen pada manusia. Peneliti tersebut mengambil sampel sebanyak 9 responden. Pertama, sebelum melakukan aktivitas 𝐴, peneliti mencatat kadar saturasi oksigen dari 9 responden tersebut. Kemudian, 9 responden tersebut diminta melakukan aktivitas 𝐴. Setelah 15 menit, peneliti tersebut mencatat kembali kadar saturasi oksigen dari 9 responden tersebut. Berikut data dari 9 responden mengenai kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas 𝐴
 
 ![image](https://user-images.githubusercontent.com/94664744/170866990-92a01846-6b99-4f01-971a-bb212c810d1a.png)

#### Berdasarkan data pada tabel diatas, diketahui kadar saturasi oksigen dari responden ke-3 ketika belum melakukan aktivitas 𝐴 sebanyak 67, dan setelah melakukan aktivitas 𝐴 sebanyak 70.

```
Responden = c(1, 2, 3, 4, 5, 6, 7, 8, 9)
x = c(78, 75, 67, 77, 70, 72, 78, 74, 77)
y = c(100, 95, 70, 90, 90, 90, 89, 90, 100)
```
 #### a. Carilah Standar Deviasi dari data selisih pasangan pengamatan tabel diatas!
 
 Menggunakan `sdev` untuk mencari standar deviasi
 ```
 Data_Frame = data.frame(Responden, x, y)
 sdev = sd(Data_Frame$x-Data_Frame$y)
 sdev
 ```
 sehingga didapatkan hasil
 # ![image](https://user-images.githubusercontent.com/94664744/170868073-f8baaea8-616b-4e45-8e5e-b6518fcbb453.png)

 #### b. Carilah nilai t (p-value)!
 
 Menggunakan `pval` untuk mencari nilai t
 ```
 h = Data_Frame$y - Data_Frame$x
 t_mu = mean(h)
 t_zbar = mean(h[1:6])
 t_n = 6
 t_s = sd(h[1:6])
 t = (t_zbar - t_mu) / (t_s/sqrt(t_n))
 t
 pval = 2 * pt(-abs(t), df = t_n - 1)
 pval
 ```
 sehingga didapatkan hasil
 # ![image](https://user-images.githubusercontent.com/94664744/170868263-ec132dfa-e18d-4bc7-9ca6-e92d90a89b25.png)

 #### c. tentukanlah apakah terdapat pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴 jika diketahui tingkat signifikansi 𝛼 = 5% serta H0 : “tidak ada pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴”
 
 ```
 Tingkat signifikansi = 5%, maka dapat disimpulkan bahwa H0 ditolak dan H1 diterima, yaitu terdapat pengaruh 
 signifikan secara statistika dalam hal kadar saturasi oksigen sebelum dans esuah melakuan aktivitas A
```

#### 2. Diketahui bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun. Untuk menguji klaim ini, 100 pemilik mobil yang dipilih secara acak diminta untuk mencatat jarak yang mereka tempuh. Jika sampel acak menunjukkan rata-rata 23.500 kilometer dan standar deviasi 3900 kilometer. 
 
 ```
 install.packages("BSDA")
 library(BSDA)
 zsum.test(mean.x=23500, sigma.x = 3900, n.x = 100,  
          alternative = "less", mu = 0,
          conf.level = 0.95)
 ```
          
 #### a. Apakah Anda setuju dengan klaim tersebut?
 
 ```
 Setuju. Karena bila kita mengacu pada pengujian z, didapat kesimpulan bahwa H0 ditolak sehingga mobil rata-rata dikemudikan lebih
 >20000 km
 ```
 
 #### b. Jelaskan maksud dari output yang dihasilkan!
 ```
 Output dari pengujian z-nya adalah hipotesis alternatif yang mana >20000 atau H1 diterima sehingga klaim benar
 ```
 
 #### c. Buatlah kesimpulan berdasarkan P-Value yang dihasilkan!
 ```
 nilai t dari uji z adalah mendekati 0, dari hasil nilai t tersebut hipotesis awal dapat ditolak dan H1 diterima
 ```

 #### 3. Diketahui perusahaan memiliki seorang data analyst ingin memecahkan permasalahan pengambilan keputusan dalam perusahaan tersebut. Selanjutnya didapatkanlah data berikut dari perusahaan saham tersebut.
 
 ![image](https://user-images.githubusercontent.com/94664744/170867215-ed37bdd8-185f-4ccb-ab09-871fe4246d50.png)

 #### Dari data diatas berilah keputusan serta kesimpulan yang didapatkan dari hasil diatas. Asumsikan nilai variancenya sama, apakah ada perbedaan pada rata-ratanya (α= 0.05)? Buatlah :
 
 
 #### a. H0 dan H1
 ```
 H0 = (miu1 = miu2)
 H1 = (miu1 != miu2) 
 ```

 #### b. Hitung Sampel Statistik!
 ```
 tsum.test(mean.x=3.64, s.x = 1.67, n.x = 19, 
          mean.y=2.79, s.y = 1.32, n.y = 27, 
          alternative = "two.sided", mu = 0, var.equal = TRUE,
          conf.level = 0.95)
 ```
 didapatkan hasil
 # ![image](https://user-images.githubusercontent.com/94664744/170872530-187f0175-8ce4-47b3-95eb-6510e3f1915c.png)

 #### c. Lakukan Uji Statistik (df =2)!
 ```
 plotDist(dist ='t', df = 2, col="green")
 ```
 didapatkan grafik
 # ![image](https://user-images.githubusercontent.com/94664744/170872589-741d356a-e2b6-48fa-9cc0-b333ce9106c8.png)

 #### d. Nilai Kritikal
 ```
 qt(p = 0.05, df = 2, lower.tail = FALSE)
 ```
 didapatkan hasil
 # ![image](https://user-images.githubusercontent.com/94664744/170872682-025aa063-97ea-42f9-aca7-f8d29b92699f.png)

 #### e. Keputusan
 ```
 karena nilai t < a, maka hipotesis awal ditolak
 ```
 #### f. Kesimpulan
 ```
 Dengan tingkat keyakinan 95%, diyakini bahwa tidak terdapat perbedaan rata-rata saham pada perusahaan di Bandung 
 dan Bali
 ```


 #### 4. Seorang Peneliti sedang meneliti spesies dari kucing di ITS . Dalam penelitiannya ia mengumpulkan data tiga spesies kucing yaitu kucing oren, kucing hitam dan kucing putih dengan panjangnya masing-masing.Jika :
 #### diketahui dataset https://intip.in/datasetprobstat1
 #### H0 : Tidak ada perbedaan panjang antara ketiga spesies atau rata-rata panjangnya sama
 #### Maka Kerjakan atau Carilah:

 #### a. Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1,grup 2,grup 3). Lalu Gambarkan plot kuantil normal untuk setiap kelompok dan lihat apakah ada outlier utama dalam homogenitas varians.

 #### b. carilah atau periksalah Homogeneity of variances nya , Berapa nilai p yang didapatkan? , Apa hipotesis dan kesimpulan yang dapat diambil ?

 #### c. Untuk uji ANOVA (satu arah), buatlah model linier dengan Panjang versus Grup dan beri nama model tersebut model 1.

 #### d. Dari Hasil Poin C, Berapakah nilai-p ? , Apa yang dapat Anda simpulkan dari H0?

 #### e. Verifikasilah jawaban model 1 dengan Post-hoc test Tukey HSD, dari nilai p yang didapatkan apakah satu jenis kucing lebih panjang dari yang lain? Jelaskan.

 #### f. Visualisasikan data dengan ggplot2


 #### 5. Data yang digunakan merupakan hasil eksperimen yang dilakukan untuk mengetahui pengaruh suhu operasi (100˚C, 125˚C dan 150˚C) dan tiga jenis kaca pelat muka (A, B dan C) pada keluaran cahaya tabung osiloskop. Percobaan dilakukan sebanyak 27 kali dan didapat data sebagai berikut: Data Hasil Eksperimen. Dengan data tersebut:
 
 #### a.  Buatlah plot sederhana untuk visualisasi data

 #### b. Lakukan uji ANOVA dua arah

 #### c. Tampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi)

 #### d. Lakukan uji Tukey

 #### e. Gunakan compact letter display untuk menunjukkan perbedaan signifikan antara uji Anova dan uji Tukey
