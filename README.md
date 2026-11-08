# MachineLearning_ProjectA02

**UTS IF2116 Pembelajaran Mesin, Milestone 1 | Project ID: A02**
Nama kelompok: [isi] | Kelas: [isi] | Dosen pengampu: Al Hamidy, S.Kom, M.I.T., Ph.D. | Universitas Mikroskil

| NIM | Nama |
|---|---|
| 231110955 | Andika Dermawan |
| 231110822 | Bagas Arma Prayoga |
| 231111638 | Muhammad Rizki |

## Deskripsi masalah
Harga mobil bekas pada iklan online sangat bervariasi dan dipengaruhi banyak faktor, sehingga sulit menilai apakah suatu harga wajar. Proyek ini membangun model regresi untuk memprediksi harga mobil bekas (target: `price`, dimodelkan sebagai `log(price)`) dari tahun, kilometer, kapasitas mesin, transmisi, status iklan, model, provinsi, dan tipe bodi. Pendekatan: Supervised Learning (regresi) dengan classical machine learning.

## Dataset
- Nama: Used Car Analysis in Indonesia, file `P0M1_Ali_Abdurrahman_old.xlsx`
- Sumber: https://github.com/aliabdurrahman10/Used-Car-Analysis-in-Indonesia (web scraping mobil123, lisensi MIT, periode pengumpulan tidak disebutkan)
- 27.781 baris x 14 kolom; satu baris = satu iklan mobil
- Cara memperoleh: [isi]. File yang dipakai kelompok ada di repositori ini.
- Catatan versi: kolom `listing__type` pada file ini hanya berisi Baru/Bekas, berbeda dari file di repositori sumber.

## Isi repositori
| File | Keterangan |
|---|---|
| `ProyekA02_Harga_Mobil_Bekas.ipynb` | Notebook eksperimen lengkap (data understanding, EDA, preprocessing, baseline, kandidat model, validasi, ensemble, clustering dan PCA) |
| `P0M1_Ali_Abdurrahman_old.xlsx` | Dataset mentah yang dipakai |
| `mobil_bekas_siap_model.csv` | Data hasil pipeline preprocessing (27.399 baris) |

## Petunjuk menjalankan
1. Buka `ProyekA02_Harga_Mobil_Bekas.ipynb` di Google Colab (File, Upload notebook).
2. Unduh `P0M1_Ali_Abdurrahman_old.xlsx` dari repositori ini ke komputer.
3. Pilih Runtime, Run all. Pada sel pertama klik *Choose Files* dan pilih file Excel tersebut.
4. Semua eksperimen memakai seed 42. Sel UMAP memasang `umap-learn` secara otomatis.
5. Estimasi waktu menjalankan seluruh notebook: [isi dari jalankanmu]. Versi pustaka: [isi dari Colab].

## Hasil eksperimen awal (data uji 20%, 5.480 baris; CV = 5-fold pada data latih)
| Model | MAE uji (Rp juta) | R² uji (log) | MAE CV (Rp juta) |
|---|---|---|---|
| Dummy (rata-rata) | 296,0 | 0,000 | - |
| Linear Regression (baseline) | 135,4 | 0,826 | 136,6 |
| Ridge | 135,4 | 0,826 | - |
| Lasso | 135,9 | 0,826 | - |
| Polynomial (deg 2) + Ridge | 126,3 | 0,847 | 128,0 |
| Random Forest | 83,7 | 0,917 | 86,3 |
| HistGradientBoosting | 79,5 | 0,925 | 85,2 |

Model yang dilanjutkan: HistGradientBoosting (belum final, belum di-tuning). Data uji sudah dipakai untuk perbandingan awal sehingga dibaca sebagai konfirmasi.

## Keterbatasan dan rencana
Data didominasi Pulau Jawa (95,9%), harga adalah harga permintaan penjual, tidak ada kolom waktu. Rencana pasca-UTS: seleksi fitur, tuning HistGradientBoosting, dan error analysis segmen mewah dan mobil Baru (detail di laporan Subbab 5.5).
