# 🪙 Coin Counting & Classification System

> A computer vision system for automatically **detecting, separating, counting, and classifying coins** from images using classical image-processing techniques.

<p align="center">
  <b>Python • OpenCV • Watershed Segmentation • Otsu Thresholding • Image Processing</b>
</p>

---

## 📌 Overview

This project implements an end-to-end **coin detection and classification pipeline** using Python and OpenCV.

The system processes an input image, separates coins from the background, handles touching coins using **Watershed Segmentation**, detects individual coins, classifies them according to their size, and calculates the final coin count and value.

The project also includes **evaluation metrics, failure-case analysis, batch processing, visualizations, and an interactive interface** for testing images.

---

## ✨ Features

| Feature                         | Description                                                         |
| ------------------------------- | ------------------------------------------------------------------- |
| 🔍 **Coin Detection**           | Automatically detects coins from input images                       |
| 🔢 **Coin Counting**            | Counts the number of detected coins                                 |
| 🧩 **Touching Coin Separation** | Uses Watershed Segmentation to separate connected coins             |
| 🪙 **Coin Classification**      | Classifies detected coins using their measured radius               |
| 💰 **Value Calculation**        | Calculates the total value based on predicted classes               |
| 🖼️ **Image Preprocessing**     | CLAHE, Gaussian Blur, thresholding, and morphology                  |
| 📊 **Evaluation**               | Calculates accuracy, MAE, RMSE, over-detection, and under-detection |
| ⚖️ **Threshold Comparison**     | Compares Otsu and Adaptive Thresholding                             |
| 🔬 **Failure Analysis**         | Identifies and analyzes incorrectly processed images                |
| 📁 **Batch Processing**         | Processes multiple coin images automatically                        |
| 💾 **CSV Export**               | Saves experiment results for further analysis                       |
| 🖥️ **Interactive GUI**         | Provides an `ipywidgets` interface for testing images               |

---

## 🧠 How It Works

The project follows this image-processing pipeline:

```text
                    ┌─────────────────┐
                    │   Input Image   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Grayscale    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │      CLAHE      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Gaussian Blur  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Otsu Threshold  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   Morphology    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │Distance Transform│
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Watershed    │
                    │  Segmentation   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Coin Detection  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Classification  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Count & Value   │
                    └─────────────────┘
```

---

## 🔬 Image Processing Pipeline

### 1. Image Preprocessing

The input image is converted to **grayscale** before applying **CLAHE (Contrast Limited Adaptive Histogram Equalization)** to improve local contrast.

A **Gaussian Blur** is then applied to reduce noise and create a cleaner image for segmentation.

### 2. Thresholding

The enhanced image is converted into a binary mask using **Otsu's Thresholding**.

Otsu's method automatically determines an appropriate threshold based on the image intensity distribution.

The project also compares:

* Otsu Thresholding
* Adaptive Mean Thresholding

This allows the behavior of both segmentation approaches to be examined under different image conditions.

### 3. Morphological Processing

Morphological operations improve the binary mask before segmentation.

**Opening** is used to remove small noise regions, while **Closing** helps fill small gaps and holes inside detected coin regions.

### 4. Distance Transform

A **Distance Transform** is applied to estimate the centers of foreground objects.

These regions are used to generate markers for separating individual coins.

### 5. Watershed Segmentation

Touching coins are one of the main challenges in coin detection.

The project uses the **Watershed algorithm** to divide connected foreground regions into separate objects.

This allows coins that touch or partially overlap to be processed individually.

### 6. Coin Detection

After segmentation, connected components and contours are analyzed.

For each valid region, the system determines properties such as its position and approximate radius using a **minimum enclosing circle**.

### 7. Classification

Detected coins are classified according to their measured radius.

The current implementation uses five size categories:

```text
XS  → Extra Small
S   → Small
M   → Medium
L   → Large
XL  → Extra Large
```

Each class can be associated with a value, allowing the system to calculate the total value of the detected coins.

---

## 📊 Evaluation

The system compares its predicted coin counts against manually defined **ground-truth counts**.

Several metrics are calculated to evaluate performance.

### Count Accuracy

Measures how closely the predicted count matches the expected number of coins.

### Mean Absolute Error — MAE

Measures the average absolute difference between the predicted and true coin counts.

### Root Mean Squared Error — RMSE

Places a larger penalty on images with larger counting errors.

### Detection Error Analysis

The project also tracks:

* **Over-detection** — the system detects more coins than expected.
* **Under-detection** — the system detects fewer coins than expected.
* **Exact detection** — the predicted count matches the ground truth.

Failure cases can then be inspected individually to understand where the pipeline struggles.

---

## 🛠️ Technologies

| Technology       | Purpose                              |
| ---------------- | ------------------------------------ |
| **Python**       | Main programming language            |
| **OpenCV**       | Image processing and computer vision |
| **NumPy**        | Numerical and array operations       |
| **Matplotlib**   | Image and result visualization       |
| **Pandas**       | Evaluation and result analysis       |
| **Pillow**       | Image handling                       |
| **ipywidgets**   | Interactive notebook interface       |
| **Google Colab** | Notebook execution environment       |

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/coin-counting-classification.git
```

Move into the project directory:

```bash
cd coin-counting-classification
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

Or install the packages manually:

```bash
pip install opencv-python numpy matplotlib pandas pillow ipywidgets
```

### 3. Open the Notebook

The main project is contained in:

```text
Coin_Counting_Classification_Final.ipynb
```

The notebook is designed primarily for **Google Colab**.

You can upload the notebook to Colab and run the cells sequentially.

---

## ▶️ Running the Project

1. Open `Coin_Counting_Classification_Final.ipynb`.
2. Run the library import and setup cells.
3. Upload the coin images when prompted.
4. Run the preprocessing and segmentation pipeline.
5. Inspect the detected coin radii.
6. Calibrate the classification ranges when necessary.
7. Run the complete detection pipeline.
8. Review the predicted counts and classifications.
9. Run the evaluation section to analyze performance.

> **Note:** Radius-based classification depends on image scale. Images captured at significantly different distances or resolutions may require recalibration.

---

## 📂 Suggested Repository Structure

```text
coin-counting-classification/
│
├── Coin_Counting_Classification_Final.ipynb
├── README.md
├── requirements.txt
├── .gitignore
│
├── images/
│   ├── sample_01.jpg
│   └── sample_02.jpg
│
└── results/
    ├── detection_example.png
    └── evaluation_results.csv
```

---

## 📸 Example Results

Add some of your best detection results here before publishing the repository.

For example:

```markdown
![Coin Detection Result](results/detection_example.png)
```

A good screenshot should show the **original image and final detected/classified coins** so visitors can immediately understand what the project does.

---

## ⚠️ Limitations

Because the current classifier relies primarily on the **detected coin radius**, its performance can be affected by:

* Different camera distances
* Changes in image resolution
* Perspective distortion
* Poor or uneven lighting
* Shadows and reflections
* Strongly overlapping coins
* Incorrect foreground segmentation
* Different coin scales between images

The classification radius ranges may therefore need to be recalibrated when using a new image dataset or camera setup.

---

## 🔮 Future Improvements

Possible extensions to the project include:

* [ ] Automatic scale calibration
* [ ] Perspective correction
* [ ] Color-based coin features
* [ ] Texture-based classification
* [ ] More robust overlapping-coin detection
* [ ] Automatic denomination recognition
* [ ] CNN-based coin classification
* [ ] Deep-learning object detection
* [ ] Standalone desktop application
* [ ] Web-based user interface

---

## 👥 Team

| Member     | Contribution                          |
| ---------- | ------------------------------------- |
| **Martin** | Preprocessing & Segmentation          |
| **Marwan** | Thresholding & Morphology             |
| **Amr**    | Watershed & Detection                 |
| **Seif**   | Classification, Evaluation & Analysis |

---

## 📚 Project Type

**Computer Vision • Digital Image Processing • Classical Image Processing**

This project focuses on classical computer-vision algorithms rather than deep-learning-based object detection.

---

## ⭐ Support

If you found this project useful or interesting, consider giving the repository a **⭐ star**.

---

<p align="center">
  <b>Built with Python 🐍 and OpenCV 👁️</b>
</p>
