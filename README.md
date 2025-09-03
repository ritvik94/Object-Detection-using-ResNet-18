# Object-Detection-using-ResNet-18

This project involves building and training a ResNet-18 model from scratch for the CIFAR-10 dataset, with a focus on robust training strategies and performance evaluation.
## Project Overview & Goals

The primary objectives of this study were to:
- Implement a ResNet-18 architecture for CIFAR-10 image classification.
- Apply advanced training techniques to improve generalization:
  - Data Augmentation: RandomHorizontalFlip, RandomCrop (32×32 with 4-pixel padding), ColorJitter, and RandomRotation (15°).
  - Regularization & Optimization: Label smoothing, cosine annealing learning rate scheduler.
  - Mixed-Precision Training (AMP) to accelerate training on CUDA-enabled devices.
- Evaluate model performance using accuracy, confusion matrix, and prediction visualizations.

## Features Implemented & Work Done

1. **Full Precision (FP32) Model Training**:
   - Implemented and trained ResNet-18 from scratch on CIFAR-10.
   - Used advanced data augmentation to prevent overfitting and enhance model robustness.
   - Applied label smoothing and cosine annealing to improve generalization.
   - Used mixed-precision training (AMP) on CUDA-enabled devices for faster training.
   - **Outputs**: Training/validation accuracy and loss curves, Confusion matrix, Sample prediction visualizations.


#### Evaluation & Visualizations
- **Visualizations**:
  - **Confusion Matrix**: The confusion matrix shows the per-class performance with the highest accuracy classes are Car (973/1000), Ship (972/1000) and Truck(959/1000).
  - **Sample predictions**: Displays a set of test images from the CIFAR-10 dataset along with their true labels and the model’s predictions.

## Key Results and Analysis

### Results
| Model Type | Accuracy (%) | Model Size (MB) | Inference Time (ms/sample) |
|------------|--------------|-----------------|---------------------------|
| FP32       | 94.02        | 42.70           | 27.67                     |

This project demonstrates that a ResNet-18 model built from scratch can achieve state-of-the-art performance (~94% accuracy) on CIFAR-10 when combined with strong augmentation, regularization, and efficient training techniques.
