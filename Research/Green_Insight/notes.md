# Green Insight (2023 - IEEE)

## The Problem Addressed

- It addresses the challenge of differentiating between Nitrogen, Phosphorus, and Potassium deficiencies in paddy crops, which often exhibit similar features, by focusing on color pattern analysis

- The study specifically focuses on automating the detection and classification of common macro-nutrient deficiencies: Nitrogen (N), Phosphorus (P), and Potassium (K).
- We use a general purpose Kaggle dataset, not region specific
- Tries to handle the intricate shape of paddy leaves and tries to differentiate properly between N,P and K deficiencies - since they all exhibit similar characteristics.
- Since traditional approaches used multiple different machine learning models for different deficiencies, in this paper we try to integrate everything into a single **HSV** color model



## Data and Preprocessing Steps

- The study used a dataset obtained from Kaggle, consisting of 426 images(no reference to the dataset found :()

- 7:3 ratio split used, 100 images per deficiency category for **thresholding** and 42 images for **testing** 
- Images resized to 300 x 3000 resolution, because the paddy leaf has an elongated shape
- Since OpenCV and PIL couldn't distinguish backgrounds and foregrounds correctly, they simply removed the background.
- Then the images were converted to the HSV color space (Hue, Saturation, Value).
- Hue - Represents the **color** itself (e.g., red, green, blue) and is typically expressed as an angle on a color wheel (0-360 degrees). 
-  Represents the purity or **intensity** of the color, ranging from 0 (gray) to 1 (fully saturated)
- Represents the **brightness** or lightness of the color, also ranging from 0 (black) to 1 (white)
- The reason they converted to HSV was to - **separate color information from brightness**, making it easier to work with colors independently. Thereby we are removing lighting dependencies in the image and can purely focus on the color.

## Methodology

- HSV color range for nitrogen deficiencies:

    - (Greenish): Lower Limit (Hue=50, Saturation=40, Value=40), Upper Limit (Hue=138, Saturation=255, Value=255)
    - (Yellowish-brown): Lower Limit (Hue=20, Saturation=40, Value=40), Upper Limit (Hue=50, Saturation=255, Value=255)

- HSV color range for phosphorus and potassium deficiencies:
    - (Greenish): Lower Limit (Hue=36, Saturation=65, Value=125), Upper Limit (Hue=138, Saturation=255, Value=255))
    - (Yellow): Lower Limit (Hue=0, Saturation=0, Value=20), Upper Limit (Hue=29, Saturation=255, Value=255)

- We then divide the paddy leaf into top and bottom halves using horizontal partitioning to examine color pattern on both sides.

- We then calculate the percentage of greenish and yellowish-brown pixels for both segments using:

    - Pixel Ratio (%) = (Count of Green or Yellow Pixels / Total Count of Green and Yellow Pixels in the region) × 100%

- After calculating these ratios, we compare them with thresholds:
    - Nitrogen Deficiency: Yellowish pixel ratio > 90% in the upper half, < 1% in the lower half. Greenish pixel ratio < 1% in both halves
    - Phosphorus Deficiency: Yellowish pixel ratio > 35% in the upper half, < 30% in the lower half. Greenish pixel ratio < 65% in the upper half, < 75% in the lower half
    - Potassium Deficiency: Yellowish pixel ratio > 50% in the upper half, > 30% in the lower half. Greenish pixel ratio < 55% in the upper half, < 70% in the lower half

- We assess N first, then P if N is not detected, and finally K if neither N nor P is detected, based on recalculated pixel percentages

## Evaluation Metric

- Accuracy is the primary metric
- Pretty high accuracy rates : 96% for nitrogen, 90% for phosphorus, and 92% for potassium deficiency detection 

## Limitations

- We need to capture these symptoms when the plant is in the **moderate** stage of growth.
- We only focus on N,P and K.
- We do not handle multiple deficiencies in a single plant image. We are limited to dentifying only one nutrient deficiency per analysis. 
