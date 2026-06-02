# Smart Waste Detection and Segmentation

Proyek computer vision untuk klasifikasi dan segmentasi gambar sampah menggunakan teknik pengolahan citra dan model deep learning berbasis ResNet. Dibangun dengan Python, OpenCV, PyTorch, dan scikit-learn.

---

## Gambaran Umum

Proyek ini memproses gambar sampah dari dataset TrashNet. Alurnya mencakup seluruh pipeline — dari analisis gambar mentah hingga pelatihan model klasifikasi — yang dibagi menjadi 11 tahap pengolahan citra dilanjutkan dengan classifier berbasis CNN.

**Dataset:** TrashNet (resized)  
**Total gambar:** 2.527  
**Kelas:** cardboard (403), glass (501), metal (410), paper (594), plastic (482), trash (137)

---

## Struktur Proyek

```
UAS/
├── index.ipynb          # Notebook utama — semua kode ada di sini
├── best_model.pth       # Bobot model yang sudah disimpan (ResNet, ~44 MB)
├── dataset-resized/     # Dataset gambar yang diorganisir per kelas
│   ├── cardboard/
│   ├── glass/
│   ├── metal/
│   ├── paper/
│   ├── plastic/
│   └── trash/
└── .env/                # Virtual environment Python
```

---

## Persyaratan

- Python 3.13
- Jupyter Notebook atau JupyterLab
- Package Python berikut:

```
numpy
opencv-python
pandas
scikit-image
matplotlib
torch
torchvision
Pillow
scikit-learn
seaborn
```

---

## Cara Menjalankan

**Langkah 1 — Aktifkan virtual environment**

```bash
# Windows (PowerShell)
.\.env\Scripts\Activate.ps1

# Windows (CMD)
.\.env\Scripts\activate.bat
```

**Langkah 2 — Install dependensi (jika belum terpasang)**

```bash
pip install numpy opencv-python pandas scikit-image matplotlib torch torchvision pillow scikit-learn seaborn
```

**Langkah 3 — Jalankan Jupyter**

```bash
jupyter notebook
```

**Langkah 4 — Buka notebook**

Di tampilan Jupyter, klik file `index.ipynb` untuk membukanya.

**Langkah 5 — Jalankan semua sel**

Pilih menu `Kernel > Restart & Run All` untuk mengeksekusi notebook dari awal sampai akhir.

---

## Isi Notebook

Notebook disusun secara berurutan berdasarkan tahapan berikut:

| Tahap | Deskripsi |
|-------|-----------|
| Distribusi Dataset | Menghitung dan memvisualisasikan jumlah gambar per kelas |
| Sample Gambar | Menampilkan satu contoh gambar dari setiap kelas |
| 1. Read Image | Memuat gambar, menampilkan shape dan rentang nilai piksel |
| 2. RGB to Grayscale | Mengonversi gambar ke mode grayscale |
| 3. Analisis Histogram | Memplot distribusi intensitas piksel |
| 4. Brightness & Contrast | Mengatur kecerahan (beta) dan kontras (alpha) gambar |
| 5. Histogram Equalization | Menerapkan CLAHE dan histogram equalization |
| 6. Filtering | Menerapkan filter rata-rata, Gaussian, median, dan bilateral |
| 7. Konvolusi / Kernel | Demonstrasi kernel kustom: sharpen, emboss, edge |
| 8. Segmentasi Sederhana | Segmentasi objek sampah dengan Otsu thresholding dan morfologi |
| 9. Edge Detection | Menerapkan deteksi tepi Sobel, Laplacian, dan Canny |
| 10. Resize & Rotate | Mengubah ukuran ke berbagai dimensi, rotasi, dan flip gambar |
| 11. Drawing | Menggambar bounding box, kontur, dan label pada objek yang terdeteksi |

Setelah tahap pengolahan citra, notebook melatih CNN berbasis ResNet untuk klasifikasi sampah multi-kelas dan menyimpan model terbaik ke file `best_model.pth`.

---

## Catatan

- Notebook menggunakan virtual environment `.env` yang sudah ada di dalam proyek. Pastikan kernel Jupyter dipilih dengan nama `.env (3.13.7)`.
- Ukuran input gambar untuk CNN adalah 224x224 piksel (standar untuk ResNet).
- File `best_model.pth` adalah model yang sudah dilatih. Jika hanya perlu inferensi, file ini bisa langsung dimuat tanpa melatih ulang.
- Semua path di dalam notebook bersifat relatif, jadi pastikan Jupyter dijalankan dari direktori `UAS/`.
