# Laporan Proyek: Analisis Transfer Learning untuk Klasifikasi Citra Burung
**Mata Kuliah:** Visi Komputer  
**Nama:** Federico Matthew Pratama (233405001)

---

## Ringkasan Proyek

Laporan ini mendokumentasikan eksperimen klasifikasi citra menggunakan dataset **CUB-200-2011**, yang berisi 200 spesies burung. Tujuan utama penelitian adalah membandingkan performa model yang dibangun **dari nol (scratch)** dengan model berbasis **Transfer Learning** menggunakan arsitektur **ResNet50**. Note : Untuk Visualisasinya lupa Rename, karena sebelumnya mencoba menggunakan EfficientNet50.

---

## Metodologi Eksperimen

Tiga pendekatan utama digunakan:

### 1. CNN from Scratch
Membangun arsitektur CNN sederhana tanpa bobot awal. Pendekatan ini dijadikan baseline, namun kurang efektif untuk dataset berkompleksitas tinggi seperti CUB-200-2011.

### 2. Feature Extraction (ResNet50)
Menggunakan ResNet50 pre-trained ImageNet, di mana semua layer konvolusi dibekukan. Hanya classifier baru yang dilatih.

### 3. Fine Tuning (ResNet50)
Membuka sebagian layer ResNet50 untuk dilatih ulang sehingga model dapat beradaptasi lebih baik terhadap karakteristik detail dari berbagai spesies burung.

---

## Hasil Komparasi (10 Epochs)

| Metode Model        | Akurasi Validasi | Kesimpulan |
|---------------------|------------------|------------|
| CNN Scratch         | ~12.16%          | Performa buruk karena arsitektur sederhana tidak mampu menangkap pola kompleks. |
| Feature Extraction  | ~62.33%          | Performa meningkat signifikan, namun terdapat indikasi overfitting dari gap train–validasi. |
| Fine Tuning         | ~68.90%          | Performa terbaik dan paling stabil dalam membedakan fitur antar spesies burung. |

---

## Cara Menjalankan Proyek (Google Colab)

Proyek ini dirancang agar dapat dijalankan sepenuhnya di Google Colab.

1. Download file `.ipynb`.
2. Upload ke Google Colab.
3. Siapkan file `kaggle.json` dari akun Kaggle Anda.
4. Klik **Runtime → Run all**.
5. Ketika diminta oleh script, upload `kaggle.json`.
6. Sistem akan otomatis:
   - Mengunduh dataset
   - Melakukan preprocessing
   - Melatih ketiga model
   - Menampilkan evaluasi dan visualisasi hasil

Seluruh eksperimen dijalankan menggunakan **Python**, **TensorFlow/Keras**, dan GPU **NVIDIA T4**.

---

