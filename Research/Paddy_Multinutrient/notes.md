# Paddy Multinutrient Deficiency Detection


## NOTE: The approach used here is not explicity ML based, i.e, no CNNs or neural networks were used.



## Problem Addressed

- Automate the identification of multiple nutrient element deficiencies in paddy leaves

## Novelty

- A unique aspect is its ability to accurately identify combinations of deficiencies such as nitrogen-phosphorus (NP), nitrogen-potassium (NK), and phosphorus-potassium (PK)

## Dataset

 A database was created consisting of 500 paddy leaf images. This includes approximately 100 images each of healthy, nitrogen-potassium defected, phosphorus-potassium defected, and phosphorus-nitrogen defected leaves. The remaining 100 images are used as test images

  Images were captured using a Sony digital camera with a 24-megapixel resolution. They were taken against a white background under fixed focal length and normal illumination conditions

## Preprocessing

- Resize the image to 256 x 256
- Noise reduction using a median filter

## Workflow

- Computing colour features (RGB values, G/R, G/B ratios, means, medians) and pattern analysis (identifying circles, their properties and colours) after preprocessing the image

- Storing calculated colour properties and pattern ranges for healthy and various defective leaves

- Comparing test image properties with the stored database to determine deficiency type

- The algorithm classifies the test image as healthy or unhealthy. If unhealthy, it detects combinations of deficiencies like nitrogen-potassium, phosphorus-potassium, and nitrogen-phosphorus. Specific G/R and G/B median values and ranges for circular spot colours are used for identification. For a healthy leaf, the test image's G/R and G/B median values must be at least 85% similar to the average healthy leaf values

## Evaluation Metric

- Used only accuracy, they got 90% average

