Weed Detection Using YOLOv8 Variants
This repository contains the implementation and evaluation of deep learning-based object detection models for identifying weeds in natural outdoor environments using YOLOv8 variants: Nano (YOLOv8n), Small (YOLOv8s), and Medium (YOLOv8m). The project aims to support sustainable agriculture through precise weed detection under varied lighting conditions.

Project Overview
Weeds compete with crops for water, sunlight, and nutrients, which negatively impacts yield and biodiversity. Traditional detection methods are labor-intensive and inefficient for large-scale farming. This project leverages computer vision and deep learning to automate weed detection and reduce excessive herbicide use.

Research Question
Can deep-learning-based object detection models (YOLOv8n, YOLOv8s, YOLOv8m) effectively detect weeds in natural conditions, especially under varying lighting environments?

Dataset
Source: Roboflow Weed Detection Dataset

Format: YOLOv8

Structure:

train/: 2877 images

valid/: 278 images

test/: 138 images

Models and Tools
Models Used: YOLOv8n, YOLOv8s, YOLOv8m (from Ultralytics)

Development Tools: Python, PyTorch, Roboflow API, Kaggle Notebooks

Training Platform: Kaggle GPU (Tesla P100)

Training and Evaluation
YOLOv8n (Nano)
Epochs: 10

mAP@50: 95.7%

mAP@50-95: 59.7%

Use Case: Lightweight deployments (e.g., edge devices, drones)

YOLOv8s (Small)
Epochs: 30

mAP@50: 95.6%

mAP@50-95: 54.4%

Observation: Did not outperform Nano variant despite longer training

YOLOv8m (Medium)
Epochs: 30

mAP@50: 97.6%

mAP@50-95: 73.3%

Observation: Best performance among all; better bounding box localization

Generalization and Unseen Data Testing
Method: Tested on real-world images captured on iPhone XS under different lighting in Leeds, UK

Issue: Significant performance drop under bright sunlight

Solution: Applied data augmentation (hue shift, brightness adjustment, flipping, geometric transforms)

Data Augmentation Techniques
Hue shift (hsv_h=0.015)

Brightness adjustment (hsv_v=0.8)

Rotation, scaling, translation, shearing

Horizontal and vertical flipping

Results Summary
Model	mAP@50	mAP@50-95	Precision	Recall
YOLOv8n	95.7%	59.7%	0.93	0.89
YOLOv8s	95.6%	54.4%	0.92	0.87
YOLOv8m	97.6%	73.3%	0.94	0.93

How to Test
To evaluate the model on a custom image using the testing script:

Run the testing code provided in the notebook.

It will prompt you to upload a trained weight file (e.g., best.pt for YOLOv8n, YOLOv8s, or YOLOv8m). These weight files are included in the ZIP archive of the repository.

Once the model is loaded, you will be prompted to upload an image you want to test.

The code will return the image with detected weeds highlighted via bounding boxes.

This allows for convenient visual verification of the model’s performance.

Key Challenges
Model bias towards shaded images in the training set

Difficulty in detecting weeds under harsh lighting

Need for more diverse and balanced datasets

Future Work
Collect more data under varied lighting

Experiment with transformer-based or two-stage models (e.g., Faster R-CNN)

Train separate models for bright vs. shadowed images and ensemble results

Ensure compliance with data privacy (e.g., GDPR) when collecting real-world images


