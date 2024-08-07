# Project Title

COLLISION AVOIDANCE AND ALERTING SYSTEM

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Processing](#processing)
- [Results](#results)
## Introduction

This project focuses on thermal image object detection utilizing the Fair-Thermal-Images dataset, a well-established standard in the field. By leveraging the power of the YOLOv8s model and YOLO algorithms, our implementation demonstrates the potential of thermal imaging technology in enhancing object detection tasks under challenging conditions.

## Installation

Follow these steps to install YOLOv8s and set up the environment:


## **Note:** First Use [Google Colab](https://colab.research.google.com/) or [kaggle](https://www.kaggle.com/) to run the code

### 1. Install Python and pip

Make sure you have Python 3.8+ and pip installed on your system. You can download Python from the official website: [https://www.python.org/downloads/](https://www.python.org/downloads/).

### 2. Create a Virtual Environment

Creating a virtual environment is a good practice to manage dependencies.

```bash
# Create a virtual environment
python -m venv yolov8-env

# Activate the virtual environment
# On Windows
yolov8-env\Scripts\activate

```
### 3. VS Code Setup

Setting up the Vs code environment for the project.


1. Install the Python extension for Visual Studio Code

2. Press Ctrl+Shift+X to open the Extensions view, then search for Python and install it.

3. Open the project folder in Visual Studio Code

4. Open the Command Palette (Ctrl+Shift+P) and select the Python: Select Interpreter command.

5. Select the Python environment to use for the project.

6. Install the required packages

7. Open the terminal and run the following command to install the required packages:

8. Install jupitor notebook form extension tab

### 4. Usage
```bash

# Run the the cells one after the other to get the results

import os

import glob

from IPython.display import Image, display

# First cell is for the imports then nvidia-smi to check the GPU then so on and so forth execute the cells serially

!nvidia-smi

!pip install -U ultralytics

import ultralytics

ultralytics.checks()
```
### 5. Processing
```bash
# The processing of the data is done in the following steps:

# make sure to have the dataset in the dataset folder
# make the dataset in the yolo format
# Train the yolov8s model with the dataset using GPU enabled

## Traning the model

!yolo task=detect mode=train model=yolov8s.pt data='/kaggle/input/flir-rgb-blurring-dataset/data.yaml' epochs=75 imgsz=640

# validate the model

!yolo task=detect mode=val model='/kaggle/working/runs/detect/train/weights/best.pt' data='/kaggle/input/flir-thermal-dataset-autorobo-self/data.yaml'

#visualize the results

Image(filename = f"/kaggle/working/runs/detect/train2/confusion_matrix_normalized.png", height = 400)

#predict the results

!yolo task=detect mode=predict model='/kaggle/working/runs/detect/train/weights/best.pt' conf=0.45 source='/kaggle/input/flir-rgb-blurring-dataset/test/images'

```

### 6. Results

The results of the project are as follows:

1. Confusion Matrix
![Result 1](https://imgur.com/DAMbC6Q)
*This is the confusion matrix*



2. Results of the predictions
![Result 2](https://imgur.com/y1sWlkj)
*This is the result of the predictions, ran on different set of images*