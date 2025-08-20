# Deep CNN for Plant Leaf Disease Identification(2019 - IEEE)

## Problem addressed
- Identification of diseases from images of plant leaves
- They propose a novel detection model based on a Deep CNN architecture
- It outperforms popular transfer learning approaches such as AlexNet, VGG16, Inception-v3, and ResNet when evaluated with validation data

## Dataset
- Images sourced from the PlantVillage Dataset
- We have **39** different classes of images:
    - 38 of them specifically relate to various plant leaves, categorised as either healthy or infected with a particular disease. For example, "Apple with black rot," "Healthy apple," "Tomato with early blight," and "Healthy soybean" are all individual classes within these 38.
    - In addition to the plant-related classes, there was also a dedicated class for background images, which did not contain any plant leaves.

- Initially the PlantVillage dataset just consisted of 54,305 images that covered 13 different types of plants. Using these, we further created the 38 specific healthy/diseased plant classes.
- They ended up performing data augmentation (image flipping, gamma correction, noise injection, principal component analysis (PCA) colour augmentation, rotation, and scaling),  and ended up with 61,486 images totally, out of which 55,636 images were used for the training dataset.
- 3900 images for validation, and 1950 images for testing.


## Methodology
- A nine layer deep CNN was constructed for the task, consisting of Conv, MaxPool, Dropout and Dense layers.
- Training and testing were performed on an NVIDIA DGX-1 V100 with 8X Tesla V100 GPUs
- We used mini-batch gradient descent instead of normal gradient descent, to achieve computational efficiency.
- For hyperparameters:
    - Optimal Training Epochs: 3000 epochs yielded the highest validation accuracy (97.87%)
    - Optimal Mini-batch Size: 64
    - Optimal Dropout Value: 0.2
    - Learning Rate: Varied from 0.01 to 0.0001

## Evaluation Metrics
- Accuracy
- AUC ROC score
- Precision
- Recall
- F1 score

## Results
- Overall classification accuracy : 96.46%
- Achieved the highest validation accuracy compared to popular transfer learning approaches (AlexNet, VGG16, Inception-v3, ResNet)
