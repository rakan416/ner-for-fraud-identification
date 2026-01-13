# NER for Fraud Identification 🕵️‍♂️💸

> Identifikasi Pola Evolusi Modus Penipuan pada Forum Online berbasis Named Entity Recognition (NER) Menggunakan IndoBERT.

Project ini bertujuan untuk mendeteksi dan mengidentifikasi entitas penting terkait modus penipuan dari diskusi forum online (Twitter/X, Reddit, Quora) menggunakan pendekatan Deep Learning. Kami menggunakan model **IndoBERT** yang di-fine-tune untuk mengekstraksi entitas seperti modus operasi, pelaku, nominal uang, hingga platform yang digunakan.

---

## 📂 Dataset
Dataset yang digunakan dalam penelitian ini mencakup data teks berbahasa Indonesia dari tahun 2020 hingga pertengahan 2025. Data dikumpulkan melalui teknik *scraping* dengan kata kunci terkait penipuan (misal: "penipuan", "scam", "ketipu").

Dataset terdiri dari total **4.061 entri**, dengan **1.056 data** telah dianotasi secara semi-otomatis menggunakan skema BIO (Beginning, Inside, Outside) untuk pelatihan NER.

📥 **Unduh Dataset:**
Dataset lengkap dapat diakses dan diunduh melalui Kaggle pada tautan berikut:
**[Dataset](https://www.kaggle.com/datasets/rakan416/scamtags-indonesian-ner-for-fraud-identification)**

---

## 🧠 Methodology: Named Entity Recognition (NER)

Fokus utama repositori ini adalah pembangunan model NER untuk mengekstraksi informasi tidak terstruktur menjadi entitas terstruktur.


### 1. Data Preprocessing
Sebelum masuk ke model, data melalui tahapan pra-pemrosesan:
* Case folding (lowercase).
* Pembersihan tautan (links), hashtag, dan mention.

### 2. Labeling Scheme (Entitas)
Kami mendefinisikan skema label kustom untuk konteks penipuan:

| Label | Deskripsi | Contoh |
| :--- | :--- | :--- |
| **MODUS** | Jenis atau skema penipuan | *skema segitiga*, *investasi bodong* |
| **PERSON** | Pelaku atau identitas manusia | *penipu*, *admin*, *nama orang* |
| **REK** | Informasi rekening bank/e-wallet | *BCA 123xxxx*, *Dana* |
| **ACTION** | Tindakan atau instruksi penipuan | *transfer*, *klik link*, *blokir* |
| **NOMINAL** | Nilai atau jumlah uang kerugian | *5 juta*, *100rb* |
| **PRODUK** | Objek yang dijadikan umpan | *mobil*, *tanah*, *iPhone* |
| **LAYANAN** | Jasa yang ditawarkan | *jual beli*, *top up game* |
| **KONTAK** | Informasi kontak pelaku | *0812xxxx*, *email* |
| **PLATFORM** | Platform tempat kejadian | *WhatsApp*, *Instagram* |

### 3. Model Architecture & Training
Kami menggunakan **IndoBERT** ([pre-trained model dari HuggingFace](https://huggingface.co/indobenchmark/indobert-base-p2)) dengan spesifikasi sebagai berikut:

* **Base Model:** IndoBERT (12-layer, 110M parameters).
* **Tokenizer:** IndoBERT Tokenizer (WordPiece).
* **Fine-Tuning Config:**
    * *Epochs:* 5
    * *Learning Rate:* 2e-5
    * *Batch Size:* 16
    * *Optimizer:* AdamW
    * *Learning Rate Decay:* Cosine
    * *Warmup Ratio:* 0.1
    * *Weight Decay:* 0.01 (untuk mencegah overfitting)

Proses pelatihan memanfaatkan seluruh parameter model (full fine-tuning) yang berjumlah 123.865.363 parameter.

📥 **Unduh Model:**
Model hasil finetuning dapat di unduh di:
**[rakan416/indobert-ner-for-fraud-identification](https://huggingface.co/rakan416/indobert-ner-for-fraud-identification)**

---

## 💡 Acknowledgements & Quote

> *"We can only see a short distance ahead, but we can see plenty there that needs to be done."*
>
> — **Alan Turing**

Proyek ini hanyalah langkah kecil. Mari terus berinovasi untuk menciptakan ekosistem digital yang lebih aman.

---

## 👥 Authors
Project ini dikerjakan oleh tim mahasiswa S1 Sains Data, Universitas Negeri Surabaya:
* **Rakan Refaya Dewangga**
* **Moch. Faiz Febriawan**
* **Alisha Deana Tabina**
