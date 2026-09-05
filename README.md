# CoinVision 🪙

### Computer Vision Coin Counting & Classification System

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge\&logo=python)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green?style=for-the-badge\&logo=opencv)
![NumPy](https://img.shields.io/badge/NumPy-Image%20Processing-blue?style=for-the-badge\&logo=numpy)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge\&logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> Computer Vision system for automatically **detecting, separating, counting, and classifying coins** using classical image-processing techniques including Otsu thresholding, morphological operations, distance transform, and Watershed segmentation.

---

# 📌 Project Overview

CoinVision is a university **Computer Vision & Digital Image Processing** project focused on automated coin analysis.

The system processes coin images and performs:

* 🪙 Automatic coin detection
* 🔢 Coin counting
* 🧩 Touching coin separation
* 📏 Size-based classification
* 💰 Total value calculation
* 📊 Detection performance evaluation
* 🔬 Failure-case analysis

The project uses a complete classical computer vision pipeline instead of deep learning.

---

# 🔄 Computer Vision Pipeline

```text
Input Image
     ↓
Grayscale Conversion
     ↓
CLAHE Enhancement
     ↓
Gaussian Blur
     ↓
Otsu Thresholding
     ↓
Morphological Processing
     ↓
Distance Transform
     ↓
Watershed Segmentation
     ↓
Connected Components
     ↓
Coin Detection
     ↓
Size Classification
     ↓
Count & Value
```

---

# 🧠 Methods Used

| Method                   | Purpose                        |
| ------------------------ | ------------------------------ |
| Grayscale Conversion     | Simplify image representation  |
| CLAHE                    | Improve local contrast         |
| Gaussian Blur            | Reduce image noise             |
| Otsu Thresholding        | Separate coins from background |
| Adaptive Thresholding    | Thresholding comparison        |
| Morphological Opening    | Remove small noise             |
| Morphological Closing    | Fill gaps and holes            |
| Distance Transform       | Estimate coin centers          |
| Watershed                | Separate touching coins        |
| Connected Components     | Identify individual regions    |
| Minimum Enclosing Circle | Estimate coin radius           |
| Radius Classification    | Classify coin sizes            |

---

# 🪙 Coin Classification

Detected coins are classified according to their estimated radius.

| Class | Category    |
| ----- | ----------- |
| XS    | Extra Small |
| S     | Small       |
| M     | Medium      |
| L     | Large       |
| XL    | Extra Large |

Each detected class can be assigned a value, allowing the system to calculate the **total value of all detected coins**.

---

# 📊 Evaluation Metrics

The predicted coin counts are compared against manually defined ground-truth values.

| Metric               | Purpose                    |
| -------------------- | -------------------------- |
| Count Accuracy       | Measures counting accuracy |
| MAE                  | Mean Absolute Error        |
| RMSE                 | Root Mean Squared Error    |
| Over-Detection Rate  | Measures extra detections  |
| Under-Detection Rate | Measures missed detections |

The system also automatically identifies **failure cases** for further analysis.

---

# 📂 Project Structure

```bash
coin-counting-classification/

├── Coin_Counting_Classification_Final.ipynb
├── README.md
├── requirements.txt
├── .gitignore
│
├── images/
│   └── sample_coin_images/
│
└── results/
    ├── detection_results/
    └── evaluation_results.csv
```

---

# 🚀 Quick Start

## 1️⃣ Clone Repository

```bash
git clone https://github.com/yourusername/coin-counting-classification.git
cd coin-counting-classification
```

---

## 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

Or:

```bash
pip install opencv-python numpy matplotlib pandas pillow ipywidgets
```

---

## 3️⃣ Open Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Coin_Counting_Classification_Final.ipynb
```

The notebook can also be uploaded and executed directly using **Google Colab**.

---

# 📸 System Features

* Upload and process coin images
* Automatic foreground segmentation
* Otsu vs Adaptive Thresholding comparison
* Separate touching coins using Watershed
* Detect individual coin regions
* Estimate coin radius
* Classify coins by size
* Calculate total coin count
* Calculate total value
* Visualize intermediate processing stages
* Batch process multiple images
* Compare predictions with ground truth
* Analyze over-detection and under-detection
* Export experiment results to CSV
* Interactive `ipywidgets` interface

---

# ⚙️ Tech Stack

| Technology   | Usage                              |
| ------------ | ---------------------------------- |
| Python       | Main Programming Language          |
| OpenCV       | Computer Vision & Image Processing |
| NumPy        | Numerical Operations               |
| Matplotlib   | Visualization                      |
| Pandas       | Results & Evaluation               |
| Pillow       | Image Handling                     |
| ipywidgets   | Interactive Interface              |
| Google Colab | Notebook Environment               |

---

# 🔍 Thresholding Comparison

The project evaluates two thresholding approaches:

| Method                     | Description                                        |
| -------------------------- | -------------------------------------------------- |
| Otsu Thresholding          | Automatically determines a global threshold        |
| Adaptive Mean Thresholding | Calculates thresholds based on local image regions |

This comparison helps analyze segmentation performance under different image and lighting conditions.

---

# 🧩 Touching Coin Detection

One of the main challenges is separating coins that touch each other.

CoinVision solves this using:

```text
Binary Mask
     ↓
Distance Transform
     ↓
Foreground Markers
     ↓
Connected Components
     ↓
Watershed Segmentation
     ↓
Separated Coins
```

This allows connected coin regions to be treated as individual objects.

---

# 📈 Results & Analysis

The system evaluates detection performance using:

* Count Accuracy
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* Over-detection analysis
* Under-detection analysis
* Per-image error analysis
* Failure-case visualization

Results can also be exported to **CSV** for further analysis.

---

# ⚠️ Limitations

The current classification method mainly depends on detected coin radius.

Performance can therefore be affected by:

* Camera distance
* Image resolution
* Lighting conditions
* Shadows and reflections
* Perspective distortion
* Coin overlap
* Segmentation errors
* Changes in image scale

Radius ranges may need to be recalibrated when using a different dataset or camera setup.

---

# 🔮 Future Improvements

* Automatic coin scale calibration
* Perspective correction
* Color-based coin classification
* Texture-based feature extraction
* Improved overlapping coin separation
* Automatic denomination recognition
* CNN-based coin classification
* Object detection using YOLO
* Web-based detection interface

---

# 👥 Team

| Member | Contribution                          |
| ------ | ------------------------------------- |
| Martin | Preprocessing & Segmentation          |
| Marwan | Thresholding & Morphology             |
| Amr    | Watershed & Detection                 |
| Seif   | Classification, Evaluation & Analysis |

---

# 🎯 Applications

* Automated coin counting
* Coin sorting systems
* Vending machine vision
* Currency analysis
* Educational computer vision systems
* Industrial object counting

---

# 📚 Project Type

**Computer Vision • Digital Image Processing • Classical Image Processing**

> This project uses traditional computer vision algorithms rather than Deep Learning, demonstrating how segmentation, morphology, and Watershed techniques can solve real-world object detection and counting problems.

---

# ⭐ Support

If you found this project useful or interesting, consider giving the repository a **⭐ Star**.

---

<p align="center">
  <b>Built with Python 🐍 + OpenCV 👁️</b>
</p>
