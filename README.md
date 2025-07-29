# Laporan Proyek: Segmentasi dan Prediksi Perilaku Konsumen pada Data Penjualan Minuman

## 1. Latar Belakang
Perusahaan retail minuman menghadapi tantangan dalam memahami perilaku konsumen secara lebih mendalam untuk meningkatkan efektivitas strategi pemasaran dan loyalitas pelanggan. Oleh karena itu, proyek ini bertujuan untuk melakukan segmentasi pelanggan menggunakan pendekatan unsupervised learning (clustering) dan membangun model prediktif menggunakan supervised learning untuk mengklasifikasikan pelanggan berdasarkan pola pembelian mereka.

Dataset yang digunakan bersumber dari [Kaggle - Beverage Sales Dataset](https://www.kaggle.com/datasets/sebastianwillmann/beverage-sales), yang mencakup data transaksi penjualan berbagai kategori minuman.


## 2. Tujuan Proyek
- Mengidentifikasi pola pembelian dan karakteristik pelanggan menggunakan algoritma KMeans Clustering.

- Membangun model klasifikasi untuk memprediksi segmen pelanggan menggunakan pendekatan supervised learning.

- Memberikan rekomendasi strategis berbasis data untuk pemasaran, promosi, dan pengelolaan hubungan pelanggan (CRM).


## 3. Unsupervised Learning: Segmentasi Pelanggan dengan KMeans

Pendekatan clustering digunakan untuk mengelompokkan pelanggan berdasarkan pola perilaku pembelian menggunakan metode **KMeans**. Berdasarkan hasil eksplorasi dan evaluasi, ditentukan jumlah optimal cluster sebanyak **4**.
### Metodologi

- Dilakukan clustering terhadap data menggunakan algoritma KMeans.

- Penentuan jumlah cluster optimal dilakukan menggunakan metode elbow method.

- Hasil akhir menunjukkan terdapat 4 segmen pelanggan yang berbeda secara karakteristik.

### Karakteristik Setiap Cluster:

#### 🔹 Cluster 1

* **Recency:** 2.83 hari
* **Frequency:** 300.49 transaksi
* **Monetary:** \$44,881.74
* **Discount Usage:** Tidak ada
* **Average Order Value (AOV):** \$149.33
* **Produk Favorit:** Alcoholic Beverages
  **➡ Pelanggan aktif, loyal tanpa diskon, fokus pada produk alkohol.**

#### 🔹 Cluster 2

* **Recency:** 2.82 hari
* **Frequency:** 299.83 transaksi
* **Monetary:** \$41,979.81
* **Discount Usage:** Tidak ada
* **Average Order Value (AOV):** \$140.01
* **Produk Favorit:** Juices
  **➡ Pelanggan aktif dengan preferensi minuman sehat, tidak bergantung pada diskon.**

#### 🔹 Cluster 3

* **Recency:** 2.85 hari
* **Frequency:** 299.93 transaksi
* **Monetary:** \$248,460.94
* **Discount Usage:** Tinggi (88.56 USD & 899 produk)
* **Average Order Value (AOV):** \$828.51
* **Produk Favorit:** Water
  **➡ Pelanggan dengan pembelian volume besar, memanfaatkan diskon, kemungkinan untuk keperluan bisnis.**

#### 🔹 Cluster 4

* **Recency:** 2.95 hari
* **Frequency:** 300.05 transaksi
* **Monetary:** \$265,821.11
* **Discount Usage:** Tinggi (94.80 USD & 899 produk)
* **Average Order Value (AOV):** \$885.91
* **Produk Favorit:** Alcoholic Beverages
  **➡ Pelanggan dengan nilai pembelian tertinggi, responsif terhadap diskon, cocok untuk program loyalitas premium.**

---

## 4. Supervised Learning: Klasifikasi Pelanggan

Setelah klasterisasi, label cluster digunakan untuk membangun model klasifikasi dengan pendekatan supervised learning.

### Metodologi:

* Pemodelan dilakukan dengan **algoritma supervised**
* **Grid Search** digunakan untuk tuning hyperparameter
* Evaluasi menggunakan **akurasi**, **precision**, **recall**, dan **F1-score**

### 📈 Hasil Evaluasi:

- Akurasi awal: 70.15%

- Akurasi setelah tuning: 79.58%

- Confusion Matrix Insight:
    - Kelas 1 memiliki recall terendah (0.66), walau precision tinggi (0.83)

    - F1-score menunjukkan ketidakseimbangan kelas masih menjadi isu

  <img width="683" height="547" alt="image" src="https://github.com/user-attachments/assets/dcf2058a-4b27-4115-a006-77c20fba2456" />

### 📌 Catatan:

Meskipun peningkatan performa terlihat setelah tuning, nilai **F1-Score** yang rendah pada kelas tertentu menunjukkan adanya ketidakseimbangan kelas. **Overfitting tidak terdeteksi**, namun generalisasi masih dapat ditingkatkan.


---

## 5. Kesimpulan

- Terdapat 4 segmen pelanggan utama dengan karakteristik unik berdasarkan analisis clustering.

- Model klasifikasi yang dibangun memiliki performa yang cukup baik, dan dapat digunakan untuk memetakan pelanggan baru ke dalam segmen yang tepat.

- Segmentasi dan klasifikasi ini dapat digunakan untuk mengarahkan strategi pemasaran yang lebih personal dan efisien.
---

## 6. Rekomendasi:

- Perbanyak data kelas minoritas melalui strategi pengumpulan data atau augmentasi data untuk meningkatkan kemampuan generalisasi model.

- Bangun program loyalitas tersegmentasi, misalnya:

- Diskon khusus untuk pelanggan diskon-sensitif (Cluster 3 & 4)

- Program tanpa promosi untuk pelanggan loyal (Cluster 1)

- Integrasikan hasil model ke dalam sistem CRM untuk melakukan penargetan otomatis berbasis segmen.

- Pertimbangkan penggunaan model klasifikasi lainnya (XGBoost, LightGBM) dan strategi balancing seperti SMOTE.
