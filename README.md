# Coin Counting and Classification System

A computer vision project for automatically detecting, counting, and classifying coins from images.

The system uses traditional image-processing and computer-vision techniques including CLAHE, Gaussian filtering, Otsu thresholding, morphological operations, distance transform, watershed segmentation, and connected-component analysis.

## Project Overview

The goal of this project is to detect individual coins in an image, including touching coins, classify them according to their size, count them, and calculate their corresponding total value.

### Processing Pipeline

```text
Original Image
      ↓
Grayscale
      ↓
CLAHE Contrast Enhancement
      ↓
Gaussian Blur
      ↓
Otsu Thresholding
      ↓
Morphological Cleanup
      ↓
Distance Transform
      ↓
Watershed Segmentation
      ↓
Connected Components
      ↓
Coin Classification
      ↓
Count & Value Calculation
```

## Features

* Automatic coin detection
* Coin counting
* Separation of touching coins using Watershed segmentation
* Size-based coin classification
* Total value calculation
* Otsu vs. Adaptive Thresholding comparison
* Batch processing of multiple images
* Evaluation using ground-truth counts
* Accuracy, MAE, and RMSE metrics
* Over-detection and under-detection analysis
* Failure-case analysis
* Visualization of intermediate processing stages
* Simple interactive GUI using `ipywidgets`
* CSV export of results

## Technologies Used

* Python
* OpenCV
* NumPy
* Pandas
* Matplotlib
* Pillow
* ipywidgets
* Google Colab

## Methodology

### 1. Preprocessing

The input image is converted to grayscale and enhanced using CLAHE (Contrast Limited Adaptive Histogram Equalization). Gaussian blur is then applied to reduce image noise.

### 2. Thresholding

Otsu's thresholding method is used to automatically separate the coins from the background.

The project also compares Otsu thresholding with Adaptive Mean Thresholding.

### 3. Morphological Processing

Morphological opening removes small noise regions, while morphological closing fills small holes inside detected coin regions.

### 4. Watershed Segmentation

A distance transform is calculated to identify coin centers.

Watershed segmentation is then used to separate coins that are touching or overlapping.

### 5. Detection and Classification

Each detected region is analyzed using contours and a minimum enclosing circle.

Coins are classified into size categories according to their detected radius:

* XS
* S
* M
* L
* XL

Each class can also be assigned a value for calculating the total value of the detected coins.

## Evaluation

The detected number of coins is compared with manually defined ground-truth values.

The project evaluates performance using:

* Count Accuracy
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* Over-detection Rate
* Under-detection Rate

Failure cases are also automatically identified for further analysis.

## Running the Project

The notebook is designed primarily for Google Colab.

1. Open `Coin_Counting_Classification_Final.ipynb` in Google Colab.
2. Run the import/setup cells.
3. Upload the coin images when prompted.
4. Run the calibration section to inspect detected coin radii.
5. Adjust the coin size ranges if necessary.
6. Run the full pipeline or batch-processing section.
7. Review the detection results and evaluation metrics.

## Installation

If running locally, install the required packages:

```bash
pip install opencv-python numpy matplotlib pandas pillow ipywidgets
```

Some notebook functionality, such as `google.colab.files`, is specific to Google Colab and may need to be changed when running locally.

## Team

| Member | Role                                  |
| ------ | ------------------------------------- |
| Martin | Preprocessing & Segmentation          |
| Marwan | Thresholding & Morphology             |
| Amr    | Watershed & Detection                 |
| Seif   | Classification, Evaluation & Analysis |

## Limitations

The current classification method relies mainly on the detected radius of each coin. Therefore, results can be affected by:

* Camera distance
* Image resolution
* Lighting conditions
* Perspective distortion
* Coin overlap
* Incorrect segmentation

The radius ranges may need to be recalibrated for a new dataset or camera setup.

## Future Improvements

Possible improvements include:

* Automatic scale calibration
* Classification using coin color and texture
* Perspective correction
* Deep-learning-based coin detection
* CNN-based coin denomination classification
* Improved handling of heavily overlapping coins
* Standalone desktop or web interface

## Project File

The main implementation is available in:

`Coin_Counting_Classification_Final.ipynb`
