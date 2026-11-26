# UTS Machine Learning - Jalur B (Regresi)

## Prediksi Harga Sewa Per Malam Properti Airbnb di Bali

| | |
|---|---|
| **NIM** | 2301010304 |
| **Nama** | KADEK AGUS SAPUTRA |
| **Kelas** | XX |
| **Jalur** | B - Regresi |
| **Random state (SEED)** | 304 (3 digit terakhir NIM) |

## Ringkasan

Model regresi linear untuk memprediksi harga sewa per malam (USD) listing Airbnb di Bali dari jumlah kamar mandi, kapasitas tamu, jenis kamar, kawasan, dan fitur lain. Tiga model dibandingkan dengan 5-fold cross-validation pada data latih, lalu diuji satu kali pada data uji:

| Model | MAE uji (USD) | RMSE uji (USD) | R2 uji |
|---|---|---|---|
| DummyRegressor (baseline) | 126,64 | 157,81 | -0,001 |
| Regresi linear sederhana (`bathrooms`) | 91,36 | 130,32 | 0,317 |
| **Regresi linear berganda** | **79,55** | **107,56** | **0,535** |

Regresi berganda menurunkan MAE sekitar 37% dibanding baseline dan tidak overfit (R2 latih 0,523 vs R2 uji 0,535). Model berlaku untuk harga sampai 672 USD per malam. Penjelasan lengkap ada di notebook.

## Dataset

- **Nama:** Bali Airbnb April 2018
- **Penulis:** David Moriano
- **Sumber:** https://github.com/daben/m2851-prac1 (diakses 25 November 2026)
- **Lisensi:** Creative Commons Attribution-NonCommercial 4.0 (CC BY-NC 4.0), https://creativecommons.org/licenses/by-nc/4.0/
- **Ukuran:** 12.228 baris, 26 kolom (setelah kolom identitas dibuang)
- **Perubahan yang dilakukan:** kolom `user_id`, `user_name`, dan `name` (identitas host dan judul listing) dibuang dari salinan di repositori ini untuk anonimisasi (UU PDP). Data selebihnya tidak diubah. Pembersihan harga 0 dan outlier dilakukan di dalam notebook.

## Struktur Repositori

```
UTS-ML-2301010304-KadekAgusSaputra/
├── README.md
├── requirements.txt
├── notebook/UTS_ML_2301010304_KadekAgusSaputra.ipynb   # sudah Run all, output tampil
├── data/listings_bali_201804.csv
└── reports/                                # grafik hasil notebook
```

## Cara Menjalankan

```bash
pip install -r requirements.txt
cd notebook
jupyter notebook UTS_ML_2301010304_KadekAgusSaputra.ipynb   # lalu Run all
```

Notebook mencari file data otomatis di `../data/`, `data/`, atau folder yang sama dengan notebook.

**Google Colab:** upload notebook, lalu upload `listings_bali_201804.csv` ke panel Files (folder `/content`), dan jalankan **Run all**. Folder `reports/` dibuat otomatis.

## Pernyataan Penggunaan AI

> **Catatan: sesuaikan paragraf ini dengan apa yang benar-benar kamu lakukan, lalu hapus catatan ini.**

Saya menggunakan **Claude (Anthropic)** sebagai alat bantu untuk: (1) mencari dan menilai kelayakan dataset, (2) menyusun kerangka dan kode notebook sesuai 6 tahap CRISP-DM, dan (3) membantu menulis teks interpretasi dan README.

Pemeriksaan yang saya lakukan terhadap hasil AI: menjalankan ulang seluruh notebook, mencocokkan angka di teks interpretasi dengan output sel, memeriksa grafik, dan mempelajari tiap langkah (split sebelum preprocessing, penggunaan Pipeline, cross-validation, serta rumus MAE dan R2) agar dapat menjelaskan dan mengubah kode saat presentasi.

## Keterbatasan

Data berasal dari April 2018 dan hasil scraping yang tidak lengkap, model hanya berlaku untuk harga sampai 672 USD, serta kemampuan prediksi terbatas (R2 0,535). Lihat Tahap 6 di notebook.
