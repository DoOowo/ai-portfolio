# Project 09: Image Classification with a CNN

**Question:** How well can a small CNN classify CIFAR-10 images, and which categories does it confuse?

## What this project does
Compares: Training vs test performance, and per-category performance.

## Data and model
- **Dataset:** CIFAR-10 (32x32 color images, 10 classes)
- **Split:** 50,000 train / 10,000 test (no separate validation set)
- **Model:** Small CNN (2 conv layers + 2 linear layers)

## Settings
- 5 epochs (Adam, learning rate 0.001, batch size 64)
- Images normalized to the range -1 to 1
- Outputs: results/ folder (plots, weights, results.txt, ZIP)
- Seed: 42

## How to run
1. Open `09_computer_vision_image_classification.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `results/results.txt`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `results/training_curves.png`: Training loss and accuracy per epoch
- `results/confusion_matrix.png`: Confusion matrix on the test set
- `results/mistakes.png`: Twelve incorrect predictions
- `results/sample_images.png`: Ten example training images

## Files in this folder
- `09_computer_vision_image_classification.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- Small CNN, only 5 epochs, no augmentation.
- No validation set, so no settings were tuned.
- One run with one seed.
