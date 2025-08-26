# Object-Detection-using-ResNet-18

The project explores model compression techniques, including **quantization** (Post-Training Quantization and Quantization-Aware Training), to reduce model size and improve inference speed while maintaining high accuracy.

## Project Overview & Goals

The primary objectives of this study were to:
- Establish a robust full-precision (FP32) baseline for image classification on CIFAR-10.
- Implement and evaluate model compression techniques:
  - **Quantization**: Reducing precision of weights and activations (e.g., from 32-bit floating-point to 8-bit integers).
      - **Post Training Quantization**
      - **Quantization Aware Training**
- Compare optimized models against the baseline across key metrics: **accuracy**, **model size**, and **inference time**.
- Provide clear visualizations to illustrate the impact and trade-offs of each optimization strategy.

## Features Implemented & Work Done

#### Quantization Techniques
1. **Full Precision (FP32) Model Training**:
   - Trained a ResNet18 model from scratch on CIFAR-10.
   - Applied advanced data augmentation: `RandomHorizontalFlip`, `RandomCrop` (32x32 with 4-pixel padding), `ColorJitter` (brightness, contrast, saturation, hue), and `RandomRotation` (15 degrees).
   - Used mixed-precision training (AMP) on CUDA-enabled devices for faster training.
   - Saved the best-performing model as `best_float_model.pth`.
   - **Outputs**: Training/validation loss and accuracy curves, confusion matrix, and sample prediction visualizations.

2. **Post-Training Quantization (PTQ)**:
   - Applied static 8-bit integer quantization to `best_float_model.pth`.
   - Fused modules (Conv-BN-ReLU) for optimized quantized operations.
   - Calibrated activation ranges using a subset of the training dataset (8192 samples).
   - Saved the quantized model as `final_ptq_quantized_model.pth`.
   - **Outputs**: Confusion matrix and sample prediction visualizations.

3. **Quantization-Aware Training (QAT)**:
   - Fine-tuned `best_float_model.pth` with simulated quantization to adapt weights to quantization noise.
   - Saved the best QAT model as `best_qat_model.pth`.
   - **Outputs**: Confusion matrix and sample prediction visualizations.

#### Evaluation & Visualizations
- **Metrics**: Compared **Test Accuracy (%)**, **Model Size (MB)**, and **Inference Time (ms/sample)** for FP32, PTQ, and QAT models.
- **Visualizations**:
  - **Accuracy Comparison**: Bar chart comparing FP32, PTQ, and QAT model accuracies.
  - **Model Size Comparison**: Bar chart showing disk size of model variants.
  - **Inference Time Comparison**: Bar chart displaying average inference time per sample.



## Key Results and Analysis

### Quantization Results
| Model Type | Accuracy (%) | Model Size (MB) | Inference Time (ms/sample) |
|------------|--------------|-----------------|---------------------------|
| FP32       | 94.02        | 42.70           | 27.67                     |
| PTQ        | 94.04        | 10.79           | 9.53                      |
| QAT        | 93.98        | 10.78           | 8.80                      |

### Observations
- **Model Size Reduction**: PTQ and QAT achieved a ~75% reduction in model size (42.70 MB to 10.79 MB).
- **Inference Speedup**: Quantized models reduced inference time by ~65% (27.67 ms to ~9 ms).
- **Accuracy Retention (PTQ)**: PTQ maintained accuracy (94.04% vs 94.02%), indicating robust calibration.
- **Accuracy Retention (QAT)**: QAT achieved 93.98% accuracy, with a minor ~0.3% drop, confirming effective adaptation to quantization.

These results highlight the efficacy of quantization for resource-constrained environments.
