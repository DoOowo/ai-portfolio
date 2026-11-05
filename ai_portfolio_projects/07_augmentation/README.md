# Project 07: Data Augmentation

**Question:** Does showing the model randomly shifted and flipped training images improve accuracy on new images?

## What this project does
Compares: Baseline vs augmented.

## Data and model
- **Dataset:** CIFAR-10 (32x32 color images, 10 classes)
- **Split:** 10,000 train / 2,000 validation / 10,000 test
- **Model:** Small CNN (2 conv layers + 2 linear layers)

## Settings
- Baseline vs augmented training images (random crop with padding 4 + random horizontal flip)
- Same image indices for both, so only the augmentation differs
- 2 epochs each (Adam, learning rate 0.001, batch size 64)
- Validation and test images are never augmented
- Seed: 42

> **Note:** Validation and test images stay unchanged so the comparison is fair.

## How to run
1. Open `07_augmentation.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/augmentation_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/augmented_examples.png`: Eight augmented training images
- `outputs/accuracy_comparison.png`: Test accuracy of the two versions

## Files in this folder
- `07_augmentation.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- Only 2 epochs: augmentation usually pays off with longer training.
- Only two types of augmentation were used.
- One run with one seed.
