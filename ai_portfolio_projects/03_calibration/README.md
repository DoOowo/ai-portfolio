# Project 03: Calibration (Temperature Scaling)

**Question:** Is the model's confidence honest, and can temperature scaling make it more honest without changing predictions?

## What this project does
Compares: Clean test data before and after scaling, plus a noisy test set.

## Data and model
- **Dataset:** CIFAR-10 (32x32 color images, 10 classes)
- **Split:** 10,000 train / 2,000 validation / 10,000 test
- **Model:** Small CNN (2 conv layers + 2 linear layers)

## Settings
- Trained for 2 epochs (Adam, learning rate 0.001, batch size 64)
- Temperature found by searching 0.5 to 5.0 (step 0.05) on the validation set only
- ECE measured with 10 bins
- Noise test: Gaussian noise with standard deviation 0.10 added to the test images
- Seed: 42

> **Note:** The temperature was fitted on validation data only, never on the test set.

## How to run
1. Open `03_calibration.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/calibration_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/ece_comparison.png`: ECE for each condition

## Files in this folder
- `03_calibration.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- ECE depends on the number of bins.
- Gaussian noise is only one simple stress test, not full robustness testing.
- The CNN is trained for only 2 epochs on 10,000 images.
