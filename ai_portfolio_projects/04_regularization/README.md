# Project 04: Regularization (Dropout and Weight Decay)

**Question:** Do dropout and weight decay reduce overfitting in a small network?

## What this project does
Compares: Baseline vs dropout vs weight decay vs both.

## Data and model
- **Dataset:** Fashion-MNIST (28x28 grayscale clothing images, 10 classes)
- **Split:** 12,000 train / 3,000 validation / 10,000 test
- **Model:** MLP (784 -> 256 -> 128 -> 10)

## Settings
- Four versions: baseline, dropout 0.3, weight decay 0.001, and both
- 3 epochs each (Adam, learning rate 0.001, batch size 64)
- The same seed is reset before each run so starting weights match
- Seed: 42

> **Note:** Compare training and validation curves, not test accuracy alone.

## How to run
1. Open `04_regularization.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/regularization_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/loss_curves.png`: Training (solid) and validation (dashed) loss per epoch
- `outputs/accuracy_comparison.png`: Test accuracy of the four versions

## Files in this folder
- `04_regularization.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- One setting per method, so this is a demo and not a tuning search.
- Only 3 epochs, which may be too short for overfitting to appear.
- One run with one seed.
