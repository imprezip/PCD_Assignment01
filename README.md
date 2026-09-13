# PCD Assignment 01. Down Sampling dan Up Sampling

Tugas mata kuliah Pengolahan Citra Digital. Membuat dan menganalisis tiga metode down sampling, yaitu Max, Average, dan Median pooling. Membuat dan menganalisis tiga metode up sampling, yaitu Nearest Neighbor, Bilinear, dan Bicubic. Pengujian dilakukan pada empat gambar dengan ciri berbeda beda, yaitu foto biasa, foto dengan tepi tegas, pola frekuensi tinggi, dan gambar gradient yang halus.

## Isi Folder

- **PCD_Assignment01.ipynb**, notebook utama untuk Google Colab. Berisi semua kode program, gambar hasil perbandingan, angka PSNR dan SSIM, serta analisis tertulis. Notebook ini sudah dijalankan penuh, jadi hasilnya bisa langsung terlihat kalau dibuka di GitHub.
- **images/**, empat gambar yang dipakai sebagai bahan uji.
- **outputs/**, semua gambar hasil perbandingan dan file tabel_metrik.csv.
- **REPORT.md**, laporan analisis dalam bentuk tulisan.

## Cara Menjalankan

1. Buka file PCD_Assignment01.ipynb di Google Colab.
2. Jalankan semua cell dari atas sampai bawah lewat menu Runtime, lalu pilih Run all.
3. Notebook akan membuat sendiri gambar gambar uji yang dibutuhkan, jadi tidak perlu upload file apapun.

## Ringkasan Hasil

Max pooling membuat gambar jadi lebih terang dan kehilangan detail gelap. Average dan Median pooling lebih menjaga tampilan asli gambar dan Median lebih tahan terhadap noise.

Bicubic memberikan hasil paling halus saat gambar diperbesar, diikuti Bilinear, lalu Nearest Neighbor. Untuk gambar dengan garis lurus dan kotak tegas, Nearest Neighbor justru bisa lebih baik karena tidak membuat tepinya buram.

Penjelasan lengkap ada di file REPORT.md.
