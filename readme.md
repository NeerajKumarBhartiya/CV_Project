# Weed Detection with YOLOv8

A complete end‑to‑end pipeline for detecting weeds in agricultural images using the YOLOv8 framework. This README covers project overview, repository structure, requirements, and all the steps you need—described in prose—to prepare data, train the model, evaluate performance, run inference, and push your work to GitHub.

---

## 📝 Project Overview

Detect and localize different weed species in field images by:

* Cleaning and filtering out invalid or corrupted image files
* Converting COCO‑format annotations into YOLO‑compatible labels
* Splitting the data into training and validation subsets
* Generating the dataset configuration for YOLOv8
* Visualizing sample bounding‑box annotations
* Training a custom YOLOv8 model on your dataset
* Evaluating and plotting key performance metrics
* Performing single‑image inference and providing an interactive notebook for batch predictions

---

## 📂 Repository Structure

* **scripts/**
  Contains all the standalone Python scripts and notebooks for each stage of the pipeline.
* **yolo\_format/**
  Intermediate folder holding YOLO‑formatted images and labels before final splitting.
* **dataset/**
  Final dataset organized into `images/train`, `images/val`, `labels/train`, and `labels/val`.
* **runs/**
  YOLOv8 training outputs, including checkpoint weights and validation results.
* **.gitignore**
  Specifies files and folders to exclude from version control.
* **README.md**
  This file.

---

## 📦 Prerequisites

Ensure you have:

* Python 3.8 or higher
* The Ultralytics YOLOv8 library
* Pillow for image handling
* scikit‑learn for dataset splitting
* tqdm for progress bars
* matplotlib for plotting
* (Optional) Google Colab or any Jupyter environment for notebooks

---

## 🚀 Pipeline Steps

1. **Clean Invalid Files**
   Use the provided script to scan your source folder and move or delete any non‑image or corrupted files, ensuring only valid images remain.

2. **Convert COCO to YOLO Format**
   Run the conversion script on both your train and test COCO JSON files. This will output YOLO‑style TXT label files and copy the corresponding images into `yolo_format/train` and `yolo_format/test`.

3. **Split into Training and Validation Sets**
   Execute the split script on the YOLO‑formatted training data. It randomly allocates a specified percentage (e.g., 80%) for training and the rest for validation, then arranges them under `dataset/images` and `dataset/labels`.

4. **Generate Dataset Configuration**
   Produce a `dataset.yaml` file that points to the root dataset folder, declares the relative paths for training and validation images, specifies the number of classes, and lists their names.

5. **Visualize Sample Annotations**
   Use the visualization script or notebook to draw bounding boxes on a few random images. This sanity‑checks that your labels align correctly with the images before training.

6. **Train the YOLOv8 Model**
   Launch training with your chosen YOLOv8 variant (e.g., small, medium, large) against the dataset defined in `dataset.yaml`. Monitor loss curves and validation metrics as training progresses.

7. **Evaluate Model Performance**
   After training, review metrics such as Precision, Recall, mAP\@0.5, and mAP\@0.5–0.95. Optionally, plot these scores in a notebook to visualize model effectiveness.

8. **Run Inference**
   Perform single‑image inference by loading the best weights file from training and applying it to new test images. An interactive notebook is also provided for batch uploads and automated prediction saving.

---

## ☁️ Pushing to GitHub

1. **Initialize** your local repository and add all files.
2. **Commit** with a descriptive message.
3. **Create** a new remote repository on GitHub.
4. **Add** the remote URL and push your `main` (or `master`) branch.
5. **Verify** that all folders, scripts, and the README appear correctly on GitHub.

---

## 📄 License

This project is released under the MIT License. Refer to the LICENSE file for full terms and conditions.
