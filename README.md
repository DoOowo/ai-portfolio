# AI Portfolio: Small Experiments in PyTorch

Each folder has a notebook, a README and a report template.

| # | Project | Dataset | Question |
|---|---|---|---|
| 01 | [Knowledge Distillation](01_distillation/README.md) | Fashion-MNIST | Can a small model learn from a big model's soft predictions and beat the same small model trained normally? |
| 02 | [Pruning](02_pruning/README.md) | Fashion-MNIST | How much accuracy do we lose when we set the smallest weights of a trained network to zero? |
| 03 | [Calibration (Temperature Scaling)](03_calibration/README.md) | CIFAR-10 | Is the model's confidence honest, and can temperature scaling make it more honest without changing predictions? |
| 04 | [Regularization (Dropout and Weight Decay)](04_regularization/README.md) | Fashion-MNIST | Do dropout and weight decay reduce overfitting in a small network? |
| 05 | [Quantization (Dynamic INT8)](05_quantization/README.md) | Fashion-MNIST | How much smaller and faster does a network get when its Linear layers use 8-bit integers instead of 32-bit decimals? |
| 06 | [Learning Rate Schedule](06_learning_rate/README.md) | Fashion-MNIST | Does cutting the learning rate during training (StepLR) help compared with a constant learning rate? |
| 07 | [Data Augmentation](07_augmentation/README.md) | CIFAR-10 | Does showing the model randomly shifted and flipped training images improve accuracy on new images? |
| 08 | [Ensemble of Models](08_ensemble/README.md) | Fashion-MNIST | Does averaging the predictions of three networks beat each single network? |
| 09 | [Image Classification with a CNN](09_computer_vision_image_classification/README.md) | CIFAR-10 | How well can a small CNN classify CIFAR-10 images, and which categories does it confuse? |

## How to use this portfolio
1. Open a notebook in Google Colab (CPU runtime is enough) and run it top to bottom.
2. Download the CSV results and figures.
3. Fill in that project's `REPORT.md` using your real numbers.

## Tips
- Every project is a single run with one seed, so treat small differences as possibly noise.
- Colab deletes files when the runtime disconnects. Download your results first.
- Common setup: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
