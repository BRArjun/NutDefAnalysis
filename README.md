# Plant Nutrition Deficiency Detection

An AI-powered system designed to automatically detect nutritional deficiencies in plant leaves using deep learning and image processing techniques. The primary goal is to provide a fast, reliable, and user-friendly diagnostic tool for farmers, particularly in remote areas, who may lack access to expert agronomic support.

## The Problem

Farmers, especially those in villages and remote areas, often lack access to expert help for crop health. When plants are nutrient-deficient, their leaves show warning signs like color changes or spots. However, most farmers rely on manual inspection, which can be slow, confusing, and inaccurate, potentially leading to severe crop damage, reduced harvests, and financial losses. This project addresses the need for a simple, affordable, and accessible tool that empowers farmers to identify problems early by simply taking a photo of a leaf.

## The Solution

An intelligent, image-based system that uses deep learning to analyze visual symptoms on plant leaves and provide an accurate diagnosis. The system is specifically tailored for three major crops: **banana**, **groundnut**, and **rice**. It leverages lightweight, optimized models to ensure fast inference and low computational load. The system is deployed through Hugging Face-hosted APIs, making it a scalable and accessible solution.

## Methodology

<img src="Images/Screenshot from 2025-08-20 20-00-07.png">

## Comparison of Default Model Performances

The models were selected and evaluated based on their performance and suitability for practical use on edge devices.

| Model | Accuracy | Pros | Cons | Suitability |
| :--- | :--- | :--- | :--- | :--- |
| **EfficientNet B0 (Banana)** | 83.10%  | Balanced in size and performance, pretrained, efficient. | May underperform compared to deeper variants. | Good choice for edge devices and banana disease classification. |
| **MobileNet V2 (Groundnut)** | 96.13%  | Very high accuracy, lightweight, mobile-friendly. | May miss complex patterns compared to larger models. | Ideal for on-device classification in field conditions. |
| **MobileNet V2 (Rice)** | 88%  | Fast inference, good performance on moderate datasets. | Less accurate than EfficientNet in some tasks. | Suitable for real-time crop diagnosis in mobile apps. |
| Advanced UNet Classifier | 51.93%  | Handles pixel-wise segmentation, useful when symptoms are spatially distinct. | Low accuracy, overkill for simple classification tasks. | When precise segmentation is required, not ideal for basic classification. |
| Histogram Equalization with SVM | 73.56%  | Simple, interpretable, improves contrast. | Not robust to complex patterns, feature engineering required. | Basic traditional CV pipeline, suitable for low-resource settings. |

## Tech Stack

  * **Programming Language**: Python 
  * **Deep Learning Framework**: PyTorch 
  * **Pre-trained Models**: MobileNet, EfficientNet 
  * **UI Framework**: Gradio 
  * **Model Deployment**: Hugging Face 
  * **Visualization & Analysis**: Matplotlib, Seaborn, Pandas 
  * **Image Processing**: PIL (Python Imaging Library) 
  * **Model Evaluation**: scikit-learn 
  * **Others**: NumPy, Pickle

<img src="Images/Screenshot from 2025-08-20 20-00-29.png">
