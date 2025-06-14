---
title: "Assignment4"
date: 2025-06-07
---


# Assignment 4
**Student Name**: [liziao]  
**Student ID**: [ZY2457B15]  
**Submission Date**: [2025/06/07]

## Handwritten Digit Recognition System

### 1. Project Background

Handwritten digit recognition is a classical problem in the field of pattern recognition and a subset of optical character recognition (OCR). It involves the automatic recognition of handwritten digits, typically Arabic numerals, by computers. This project focuses on **offline handwritten digit recognition**, where static images (rather than real-time pen movements) are analyzed. With increasing digitalization, this technology finds wide applications in banking, form scanning, and postal code reading. The goal is to develop a fast, high-accuracy system with low false recognition and rejection rates.

### 2. Core Features

- **User Interface for Handwriting Input**: A handwriting pad implemented using PyQt5 allows users to draw digits using a mouse.
- **Data Preprocessing**: Converts hand-drawn white-on-black images into grayscale tensors compatible with the neural network.
- **Neural Network Based on LeNet-5**: A convolutional neural network (CNN) architecture inspired by LeNet-5 is implemented and trained.
- **Interactive Prediction**: The system performs real-time recognition of the drawn digit using the trained model.
- **Activation Function Experimentation**: Relu, tanh, and sigmoid functions were tested to optimize accuracy.
- **Softmax Output Layer**: Converts raw output to probabilities to better reflect prediction confidence.

### 3. Key Technical Challenges

- **Image Polarity Mismatch**: MNIST dataset images are black background with white digits, while PyQt5 default is white background with black strokes. This required reversing the drawing mode.
- **Stroke Merging Errors**: When drawing multiple strokes (e.g., digit "4"), lines between strokes were mistakenly connected. This was resolved by inserting conditional breakpoints between strokes.
- **Activation Function Optimization**: Different activation functions impacted model accuracy. ReLU provided the best performance (~99.2% accuracy after 100 epochs).
- **Non-Probability Output**: Output vectors initially didn't resemble probabilities (often negative or non-normalized). Applying softmax transformed them into interpretable probabilities.

### 4. Development Environment (Key Software & Versions)

| Component               | Version / Tool                |
|------------------------|-------------------------------|
| Programming Language    | Python 3.x                    |
| Deep Learning Framework | PyTorch 1.x                   |
| GUI Framework           | PyQt5                         |
| Dataset                 | MNIST (via torchvision)       |
| IDE / Editor            | Visual Studio Code / PyCharm  |
| Operating System        | Windows 10/11                 |

### 5. Development Process

#### Step 1: Dataset Preparation
- Downloaded MNIST dataset using `torchvision.datasets.MNIST`.
- Each image is grayscale, 28×28 pixels, and single-channel.

#### Step 2: CNN Model Architecture
- Based on LeNet-5 but customized:
  - First convolution: 5×5 kernel → output 24×24
  - Max pooling → down to 12×12
  - Second convolution: 3×3 kernel → output 10×10
  - Output channels: 20
  - Reshape to a 2000-dimensional feature vector
  - Two fully connected layers
  - ReLU activation
  - Softmax output for prediction

#### Step 3: GUI Design using PyQt5
- **initUI function**:
  - Defined window size, font styles, and control buttons
- **Drawing logic**:
  - Recorded mouse events and path
  - Used a black canvas with white pen to match dataset
  - Saved image on click for inference

#### Step 4: Model Training
- Tested three activation functions:
  - ReLU → ~99.2% accuracy
  - Tanh → ~99.0%
  - Sigmoid → ~97.5%
- ReLU selected based on best performance
- Adam optimizer used instead of SGD due to:
  - Faster convergence
  - Less sensitivity to learning rate

#### Step 5: Inference & Prediction
- Load `.pt` model weights
- Convert drawn image into tensor
- Feed into model
- Output 10-dimensional vector → apply softmax for probability

#### Step 6: Debugging and Refinement
- Fixed stroke overlap bugs using conditional breakpoints
- Aligned PyQt5 image output with model input format
- Improved GUI usability and model prediction reliability



### 4. Results
![software](./software.jpg "software")

### 5. Source Code:
  <a href="./digit.zip" download>download code zip</a>

