# Tugas NLP 1: Sentiment Analisys Menggunakan Machine Learning

Repositori ini berisi pipeline lengkap untuk **Analisis Sentimen Teks (Bahasa Indonesia)** menggunakan **Machine Learning klasik** (Naive Bayes & Logistic Regression) dengan representasi fitur **TF-IDF n-gram**.

Pipeline ini disusun dalam **9 langkah** yang mencakup: *data preprocessing, training, evaluasi, hingga packaging & deployment*.

---

## 📑 Daftar Isi

- [Step 1: Load Data & EDA](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 2: Data Cleaning & Label Normalization](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 3: Split Dataset](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 4: Feature Engineering (TF-IDF + n-gram)](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 5: Model Comparison (Naive Bayes vs Logistic Regression)](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 6: Confusion Matrix Visualization](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 7: Final Model + Save Artifacts](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 8: Inference Demo (List & CSV)](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Step 9: Export Metrics & Upload to Drive](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Pipeline Flowchart](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Cara Penggunaan](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Contoh Inference](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)
- [Lisensi](https://www.notion.so/Final-Untuk-GitHub-281660e5a316803f8317f1e6bfd1b42d?pvs=21)

---

## Step 1: Load Data & EDA

- Membaca dataset CSV (misalnya kumpulan tweet).
- Deteksi otomatis kolom teks (`tweet`) dan label (`sentimen`).
- Tampilkan beberapa sample data.
- Periksa distribusi label (imbalanced dataset bisa diketahui dari sini).

---

## Step 2: Data Cleaning & Label Normalization

- Normalisasi label agar konsisten (misal: `"Positif"` → `"positive"`).
- Membersihkan teks:
    - lowercasing
    - hapus URL, mention, hashtag
    - hapus karakter non-alfabet (opsional stopwords)
- Hasil akhir: teks lebih bersih, siap untuk feature extraction.

---

## Step 3: Split Dataset

- Membagi data menjadi **train / validation / test**.
- Tujuan:
    - Train → melatih model
    - Validation → memilih model terbaik & tuning parameter
    - Test → evaluasi akhir (generalization check)

---

## Step 4: Feature Engineering (TF-IDF + n-gram)

- Gunakan **TfidfVectorizer** dari `scikit-learn`.
- Konfigurasi:
    - `ngram_range=(1,2)` → unigram + bigram
    - `max_features=30000`
    - `min_df=2`, `max_df=0.95`
- Output: matriks sparse yang siap dipakai di model ML klasik.

---

## Step 5: Model Comparison (Naive Bayes vs Logistic Regression)

- **Multinomial Naive Bayes (NB)**: ringan, cepat, cocok untuk teks.
- **Logistic Regression (LR)**: baseline kuat untuk klasifikasi teks.
- Evaluasi menggunakan **akurasi** dan **classification report** (precision, recall, F1).

---

## Step 6: Confusion Matrix Visualization

- Visualisasi hasil prediksi validasi set untuk kedua model.
- Tersedia 2 versi:
    - absolute counts
    - normalized (proporsi per kelas)
- File output disimpan sebagai PNG di `./outputs/`.

---

## Step 7: Final Model + Save Artifacts

- Pilih model terbaik berdasarkan validasi (antara NB vs LR).
- Refit model terbaik pada **train + validation set**.
- Simpan artefak:
    - `tfidf_vectorizer_xxx.joblib`
    - `model_xxx.joblib`
- Salin otomatis ke Google Drive (jika ter-mount).

---

## Step 8: Inference Demo (List & CSV)

- Prediksi langsung dari **list Python**:
    - Negatif → `"Layanannya lambat banget dan sering error, saya kecewa."`
    - Positif → `"Aplikasinya sangat membantu, fiturnya lengkap dan mudah dipakai!"`
    - Netral → `"Saya baru mencoba sebentar, masih perlu waktu untuk menilai."`
- Prediksi dari **CSV** (kolom wajib: `text`).
- Output hasil disimpan ke `./outputs/predictions.csv`.

---

## Step 9: Export Metrics & Upload to Drive

- Ringkasan hasil evaluasi otomatis ditulis ke:
    - `./outputs/summary_metrics.md`
- Isi file:
    - akurasi validasi (NB & LR)
    - metrik macro-F1 & weighted-F1
    - path artefak model/vectorizer
    - path confusion matrix
- File disalin ke Google Drive: `/Proyek/OutputSentimentNew/reports/`.

---

## Pipeline Flowchart

Visualisasi keseluruhan alur (Step 1–11):

---

## Cara Penggunaan

1. Clone repo atau buka notebook di Google Colab.
2. Jalankan setiap step (1–11) secara berurutan.
3. Hasil:
    - Artefak model → `./artifacts`
    - Laporan & gambar → `./outputs`
   
---

## Contoh Inference

```python
import joblib

# Load artifacts
vectorizer = joblib.load("artifacts/tfidf_vectorizer_LogisticRegression_xxx.joblib")
model = joblib.load("artifacts/model_LogisticRegression_xxx.joblib")

# Prediksi teks baru
texts = [
    "Layanannya lambat banget dan sering error, saya kecewa.",  # Negatif
    "Aplikasinya sangat membantu, fiturnya lengkap dan mudah dipakai!",  # Positif
    "Saya baru mencoba sebentar, masih perlu waktu untuk menilai."  # Netral
]
X = vectorizer.transform(texts)
preds = model.predict(X)
print(preds)

```

---

## Lisensi

Proyek ini menggunakan lisensi **MIT**.

Silakan gunakan dan modifikasi sesuai kebutuhan.
