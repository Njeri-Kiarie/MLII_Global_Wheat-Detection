# MLII_Plant_Disease_Detection

# Plant Disease Classification Using Deep Learning

## Project Overview

This project develops a deep learning model for **plant disease classification** using the PlantVillage dataset. A Convolutional Neural Network (CNN) was trained to classify plant leaf images into **38 healthy and diseased plant categories**.

Although the original project brief refers to wheat detection, the provided PlantVillage dataset used in this project does not contain wheat classes. Therefore, the project focuses on general plant disease classification.

---

## Problem Statement

Plant diseases can affect crop health, productivity, and agricultural yields. Identifying diseases early can help support better crop management.

The objective of this project is to develop a CNN model capable of classifying plant leaf images into different healthy and diseased categories.

---

## Dataset

The PlantVillage dataset used in this project contains:

- **54,305 images**
- **38 classes**
- Images of size **256 × 256 pixels**
- **RGB** images with three color channels

The dataset contains healthy and diseased leaf images from different plants, including apple, corn, grape, potato, tomato, strawberry, peach, and others.

Exploratory analysis also showed that the dataset is **imbalanced**, with some classes containing considerably more images than others.

---

## Exploratory Data Analysis

The dataset was explored before model development to understand its structure.

The following steps were performed:

- Identified the number of classes
- Counted the number of images in each class
- Examined the class distribution
- Displayed sample plant images
- Checked image dimensions
- Checked the image color format

The images were consistently **256 × 256 pixels** and in **RGB format**.

---

## Data Preparation

The dataset was divided approximately into:

- **70% Training data**
- **15% Validation data**
- **15% Testing data**

The training data was used to train the CNN, validation data was used to monitor performance during training, and test data was reserved for final model evaluation.

Image pixel values were rescaled from the original `0–255` range to `0–1`.

### Data Augmentation

To introduce variation into the training images, the following augmentation techniques were applied:

- Random horizontal flipping
- Random rotation

---

## CNN Model

A **Convolutional Neural Network (CNN)** was developed using TensorFlow/Keras.

The model consisted of:

- Input layer: `256 × 256 × 3`
- Data augmentation
- Rescaling layer
- Conv2D layer with 16 filters
- MaxPooling2D
- Conv2D layer with 32 filters
- MaxPooling2D
- Conv2D layer with 64 filters
- MaxPooling2D
- Flatten layer
- Dense layer with 128 neurons
- Output layer with 38 classes

The model contained approximately **8.4 million trainable parameters**.

---

## Model Training

The CNN was trained using:

- **Optimizer:** Adam
- **Loss Function:** Sparse Categorical Cross-Entropy
- **Batch Size:** 32
- **Epochs:** 10
- **Evaluation Metric:** Accuracy

During training, accuracy increased to **94.88%**.

The best validation accuracy was **93.52% at epoch 8**, while the final validation accuracy was **91.30%**.

Training and validation accuracy and loss were visualized to examine how the model learned across the 10 epochs. The curves showed strong learning, with some fluctuations in validation performance during later epochs suggesting slight overfitting.

---

## Model Evaluation

The final CNN was evaluated using the unseen test dataset.

| Metric | Result |
|---|---:|
| Training Accuracy | 94.88% |
| Final Validation Accuracy | 91.30% |
| Test Accuracy | **90.44%** |
| Test Loss | **0.3366** |
| Weighted Precision | **92%** |
| Weighted Recall | **90%** |
| Weighted F1-Score | **90%** |
| Macro F1-Score | **87%** |

The model correctly classified approximately **90% of the unseen test images**.

---

## Classification Report

A classification report was generated to examine precision, recall, and F1-score for each of the 38 classes.

The model performed strongly across many classes, although some classes were more difficult to classify. Examples included **Corn Northern Leaf Blight, Corn Cercospora Leaf Spot, Potato Healthy, and Tomato Early Blight**.

The differences in performance between classes may partly reflect the class imbalance identified during exploratory analysis.

---

## Confusion Matrix

A confusion matrix was used to visualize correct and incorrect predictions across the 38 classes.

Most predictions were concentrated along the main diagonal, showing that the majority of test images were correctly classified.

Some confusion occurred between similar disease classes, particularly **Corn Northern Leaf Blight and Corn Cercospora/Gray Leaf Spot**. Some misclassification was also observed among tomato disease classes.

---

## Sample Predictions

Sample images from the test dataset were used to visually compare the:

**Actual Class → Predicted Class**

The displayed examples showed that the CNN could successfully classify different healthy and diseased plant leaves from the test dataset.

---

## Conclusion

A CNN model was successfully developed to classify plant leaf images into **38 healthy and diseased categories**.

The final model achieved **94.88% training accuracy, 91.30% validation accuracy, and 90.44% test accuracy**, with a weighted F1-score of **90%**.

The results show that the CNN learned useful visual patterns for plant disease classification while also highlighting a few classes where classification was more challenging.
