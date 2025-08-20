# ILink - SqueezeNet

## Problem addressed
- Identify multi-nutrient deficiencies in paddy plants

## Novelty

- Improved Balanced Iterative Reducing and Clustering using Hierarchies (I-BIRCH)
    - Automatically adjust the threshold value rather than keeping it static

- Improved Multi-Resolution Extended Local Binary Pattern (Improved MRE-LBP)
    - A more refined filtering approach to cut down noise and preserve finer details and textures.

- Hybrid ILink-SqueezeNet model
    - Use an improved RELU activation function to remove vanishing gradients, efficient learning and enhanced stability

## Data and Preprocessing

- https://www.kaggle.com/datasets/guy007/nutrientdeficiencysymptomsinrice

- Pass the images through a Gaussian Filter to refine the quality of the image

## Methodology

- Pass the preprocessed image into another preprocessing step to extract relevant features, map them to cluster labels, and remove outliers

- Use Improved MRE-BLP to adopt more precise clusters

- BIRCH subclustering is used to allot data points to sub clusters based on a similarity metric

- The I-BIRCH algorithm is then used to produce the clusters, which are in turn used to construct the segmented image.

- Improved LinkNet
    - CNN architecture for semantic segmentation which uses a special RELU activation with a small positive constant added to not make the gradients completely zero

- SqueezeNet
    - We use conv layers, max pooling layers and fire modules
    - These fire modules combine intelligent spatial and channel-wise feature reduction

## Evalutation Metrics

- Sensitivity, False Negative Rate (FNR), Negative Predictive Value (NPV), Specificity, F-measure, 
Precision, False Positive Rate (FPR), Matthews Correlation Coefficient (MCC), and Accuracy


## Results

- Accuracy scores - 0.865 to an impressive 0.966 across different training data percentages
- Sensitivity - 0.941% and specificity - 0.925