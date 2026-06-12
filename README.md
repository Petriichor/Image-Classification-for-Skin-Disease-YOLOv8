# 🔬 Skin Disease Classification using YOLOv8

Repositori ini berisi *pipeline* eksperimen *Deep Learning* untuk mengklasifikasikan 22 jenis penyakit kulit berdasarkan citra medis. Pendekatan utama yang digunakan dalam repositori ini adalah arsitektur *Convolutional Neural Network* (CNN) mutakhir, yaitu **YOLOv8** (versi Klasifikasi).

## 🚀 Project Overview
Penyakit kulit seringkali memiliki kemiripan visual yang sangat tinggi (misalnya perbedaan mikroskopis antara *Cyst* dan *Nodule*, atau *Rosacea* dan *Acne*). Dataset citra medis umumnya juga memiliki distribusi kelas yang tidak seimbang (*imbalanced*). 

Proyek ini bertujuan untuk membangun *baseline model* AI yang sangat ringan, efisien dalam komputasi, namun tetap agresif dalam mengekstrak fitur lokal yang tajam untuk membedakan lesi kulit tersebut.

* **Arsitektur Model Dasar:** `YOLOv8n-cls` (YOLOv8 Nano Classification)
* **Jumlah Kelas:** 22 Kelas (Vitiligo, Rosacea, Actinic Keratosis, Skin Cancer, dll.)
* **Resolusi Input:** `224x224` piksel

## 📊 Performa Model
Berdasarkan hasil *training* menggunakan fitur pembatasan otomatis (*Early Stopping*), model menyadari konvergensi dan mencapai titik optimal pada **Epoch 80** (dari batas maksimal 200). 

Hasil pengujian pada data yang belum pernah dilihat sebelumnya (*Test Set*) menunjukkan:
* **Test Accuracy (22 Classes):** `75.10%`
* Model terbukti sangat percaya diri dalam memprediksi penyakit dengan ciri kontras visual tinggi (contoh: *Vitiligo* dikenali dengan *confidence score* **>99%** pada *random inference*).

## 💻 Cara Menjalankan (*How to Run*)

Ikuti petunjuk di bawah ini untuk menjalankan *notebook* inferensi atau melakukan *training* ulang di perangkat Anda (direkomendasikan menggunakan *environment* Linux/WSL dengan dukungan GPU NVIDIA).

### 1. Clone Repository
```bash
git clone [https://github.com/Petriichor/Image-Classification-for-Skin-Disease-YOLOv8.git](https://github.com/Petriichor/Image-Classification-for-Skin-Disease-YOLOv8.git)
cd Image-Classification-for-Skin-Disease-YOLOv8

### 2. Siapkan Virtual Environment
Sangat disarankan menggunakan lingkungan virtual untuk menghindari bentrok versi *library*. Contoh menggunakan Conda:
```bash
conda create -n skin-yolo python=3.11
conda activate skin-yolo
```

### 3. Install Dependencies
Install seluruh *library* utama (Ultralytics, TensorFlow, Jupyter) melalui `requirements.txt`:
```bash
pip install -r requirements.txt
```

### 4. Siapkan Dataset
Karena alasan privasi dan batasan ukuran *file*, dataset citra medis tidak disertakan dalam repositori ini. 
1. Download dataset dari Kaggle (https://www.kaggle.com/datasets/pacificrm/skindiseasedataset)
2. Ekstrak *file* hasil unduhan. Pastikan nama foldernya adalah `SkinDisease`.
3. Letakkan folder `SkinDisease` tersebut **sejajar (di luar)** folder repositori ini. 

Struktur direktori Anda harus terlihat persis seperti ini agar *notebook* dapat langsung dijalankan tanpa mengubah kode:

```text
📁 Direktori_Kerja_Anda/
├── 📁 SkinDisease/                  <-- Folder dataset hasil ekstrak dari Kaggle
│   ├── 📁 train/
│   └── 📁 test/
└── 📁 Image-Classification-for-Skin-Disease-Yolov8/                 <-- Folder repositori hasil clone
    ├── 📝 yolo.ipynb                <-- Notebook yang akan dieksekusi
    ├── 📝 README.md
    └── 📝 requirements.txt
```

### 5. Eksekusi Jupyter Notebook
Jalankan server Jupyter dari terminal Anda:
```bash
jupyter notebook
```
Buka file `yolo.ipynb` dan Anda dapat menjalankan seluruh *cell* secara berurutan untuk melihat proses inisiasi, *training*, validasi metrik, hingga inferensi gambar secara langsung.
 
