# Rice Nutrient Deficiency and Leaf Image Analysis (India-based, 2024)

## Problem addressed
- The study focuses on identifying deficiencies of the most important nutrients for rice: nitrogen (N), phosphorus (P), and potassium (K) in India.

## Dataset
- https://www.kaggle.com/datasets/guy007/nutrientdeficiencysymptomsinrice
- The dataset contains 440 images for Nitrogen deficiency, 333 images for Phosphorus deficiency, and 383 images for Potassium deficiency

## Preprocessing
- Color space conversion
- Cropping
- Filtering
- Enhancement
- Adjust contrast between foreground and background
- Noise removal

## Feature Extraction
- FCTH (Fuzzy Colour and Texture Histogram):
    - First split the image in blocks
    - Then find the gray-level co-occurence matrix, which is used to identify spatial relationships
    - Then we perform fuzzy clustering on this matrix to obtain texture clusters
    - Extract color information from each block
    - Combine both of these and we get the FCTH descriptor
    - Combine descriptors of all the blocks of the image to get the final descriptor

- CEDD (Colour and Edge Directivity Descriptor):
    - Input image is split into non overalapping blocks
    - Compute the color histogram for each block
    - Apply color quantization to reduce the number of colors
    - Normalize the histogram to reduce illumination effects
    - Capture the structure of the image using edge orientation histogram
    - Concatenate histograms from all blocks to form the final CEDD descriptor

## Model

Random Forest model is used for classifying deficiencies of nitrogen, phosphorus, and potassium by making use of the combined feature vectors from CEDD and FCTH

## Evalutation Metrics

- Random Forest Performance:
    - Class 0 (Nitrogen Deficient): Accuracy 94.66%, Precision 92.46%, Sensitivity 94.77%, Specificity 94.59%
    - Class 1 (Phosphorus Deficient): Accuracy 89.63%, Precision 83.96%, Sensitivity 80.18%, Specificity 93.58%
    - Class 2 (Potassium Deficient): Accuracy 89.71%, Precision 84.5%, Sensitivity 85.38%, Specificity 91.94%

By comparing these results with a standard Naive Bayes model, we find that random forest performs way better.