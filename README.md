# Object-Detection-using-ResNet-18





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
