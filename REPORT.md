# Laporan Analisis PCD Assignment 01
### Down Sampling (Max, Average, Median) dan Up Sampling (Nearest Neighbor, Bilinear, Bicubic)

## 1. Tujuan

Tugas ini membuat program untuk memperkecil gambar dengan tiga metode, yaitu Max pooling, Average pooling, dan Median pooling. Tugas ini juga membuat program untuk memperbesar gambar dengan tiga metode, yaitu Nearest Neighbor, Bilinear, dan Bicubic. Semua kode ditulis dan dijalankan di file PCD_Assignment01.ipynb.

## 2. Gambar yang Digunakan

Ada empat gambar berukuran 512 kali 512 piksel yang dipakai sebagai bahan uji, supaya perilaku setiap metode bisa dilihat pada kondisi yang berbeda beda.

| Nama file | Jenis | Ciri khas |
|---|---|---|
| img_natural_astronaut.png | Foto berwarna | Campuran warna kulit, tekstur, dan bagian halus |
| img_edges_camera.png | Foto hitam putih | Ada garis dan tepi yang tegas |
| img_highfreq_checkerboard.png | Pola buatan | Kotak kotak yang berulang dan sangat rapat |
| img_smooth_gradient.png | Gambar buatan | Perubahan warna yang pelan dan lembut |

Semua file gambar ada di folder images.

## 3. Cara Kerja Program

Untuk down sampling, gambar dibagi menjadi blok blok kecil berukuran 4 kali 4 piksel. Setiap blok diubah menjadi satu piksel dengan mengambil nilai maksimum, nilai rata rata, atau nilai tengah, tergantung metodenya.

Untuk up sampling, sebagian kecil dari gambar dipotong lalu diperbesar 8 kali menggunakan fungsi resize dari OpenCV. Tiga pilihan interpolasi yang dipakai adalah Nearest Neighbor, Bilinear, dan Bicubic.

Cara membandingkan hasilnya dilakukan secara visual, yaitu gambar asli diletakkan berdampingan dengan hasil dari tiap metode sehingga perbedaannya bisa langsung dilihat.

Sebagai tambahan, ada juga pengujian dengan angka. Gambar diperkecil dulu, lalu diperbesar lagi ke ukuran semula, kemudian dibandingkan dengan gambar aslinya memakai ukuran PSNR dan SSIM. Semakin tinggi nilainya, semakin dekat hasilnya dengan gambar asli. Nilai lengkapnya ada di file outputs/tabel_metrik.csv.

## 4. Hasil Down Sampling

Max pooling membuat gambar terlihat lebih terang dari aslinya. Ini terjadi karena metode ini selalu memilih nilai paling terang di setiap blok sehingga detail yang gelap sering hilang.

Average pooling menghasilkan gambar yang halus dan warnanya masih dekat dengan aslinya. Metode ini seperti menghaluskan gambar dulu sebelum diperkecil.

Median pooling hasilnya cukup mirip dengan average pooling untuk gambar biasa. Bedanya, median lebih tahan terhadap gangguan seperti titik terang atau gelap yang muncul tiba-tiba karena nilai ekstrim seperti itu tidak akan terpilih sebagai nilai tengah.

Pada gambar checkerboard yang polanya sangat rapat, semua metode down sampling sama sama kehilangan sebagian detail. Ini wajar terjadi karena ukuran hasil yang lebih kecil memang sudah tidak cukup untuk menyimpan pola sepadat itu.

## 5. Hasil Up Sampling

Nearest Neighbor menghasilkan gambar yang terlihat kotak kotak kalau diperbesar, terutama pada bagian tepi atau garis. Cara ini paling ringan tapi kurang halus dan detail.

Bilinear menghasilkan gambar yang jauh lebih halus dan detail dibanding Nearest Neighbor. Bagian tepi tidak lagi terlihat seperti tangga walaupun sedikit lebih buram dibanding gambar aslinya.

Bicubic menghasilkan gambar paling halus dan detailnya paling terjaga di antara ketiga metode. Prosesnya sedikit lebih berat karena setiap piksel baru dihitung dari area yang lebih luas.

Pada gambar checkerboard, hasilnya justru terbalik. Nearest Neighbor tetap terlihat tajam karena pola kotak kotaknya sejajar dengan piksel, sedangkan Bilinear dan Bicubic malah membuat tepi kotaknya jadi buram. Ini menunjukkan bahwa metode terbaik tergantung jenis gambarnya. Untuk foto biasa, Bicubic lebih unggul. Untuk gambar dengan garis lurus dan kotak tegas, Nearest Neighbor bisa lebih baik.

## 6. Ringkasan Angka

Berdasarkan pengujian tambahan dengan PSNR, urutan kualitas hasil up sampling dari yang paling rendah ke paling tinggi pada gambar foto biasa adalah Nearest Neighbor, kemudian Bilinear, kemudian Bicubic. Detail angka lengkapnya ada di file outputs/tabel_metrik.csv dan grafik outputs/grafik_psnr_up.png.

## 7. Kesimpulan

Untuk memperkecil foto biasa, Average pooling atau Median pooling lebih disarankan dibanding Max pooling karena Max pooling membuat gambar jadi terlalu terang.
Median pooling lebih cocok dipakai kalau gambarnya mengandung gangguan atau noise.
Untuk memperbesar foto biasa, Bicubic memberikan hasil paling baik, diikuti Bilinear, lalu Nearest Neighbor.
Untuk memperbesar gambar dengan garis lurus dan kotak tegas seperti pola pixel art, Nearest Neighbor bisa jadi pilihan yang lebih baik karena tidak membuat tepinya jadi buram.

Down sampling adalah proses yang membuang sebagian informasi gambar. Proses up sampling sesudahnya hanya bisa menebak kembali nilai piksel yang hilang dan tidak bisa mengembalikan gambar persis seperti aslinya.

## 8. Daftar Berkas

```
PCD_Assignment01.ipynb   Notebook utama, sudah dijalankan lengkap dengan hasilnya
images/                  Empat gambar yang dipakai sebagai bahan uji
outputs/                 Semua gambar hasil perbandingan dan tabel_metrik.csv
REPORT.md                Laporan ini
README.md                Penjelasan singkat tentang isi folder
```
