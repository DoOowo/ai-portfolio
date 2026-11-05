# Project 08: Ensemble of Models

**Question:** Does averaging the predictions of three networks beat each single network?

## What this project does
Compares: Each single model vs the ensemble.

## Data and model
- **Dataset:** Fashion-MNIST (28x28 grayscale clothing images, 10 classes)
- **Split:** 12,000 train / 3,000 validation / 10,000 test
- **Model:** MLP (784 -> 256 -> 128 -> 10), trained three times

## Settings
- Three models with different seeds: 11, 22, 33
- 3 epochs each (Adam, learning rate 0.001, batch size 64)
- Ensemble = the average of the three models' predicted class probabilities

> **Note:** The ensemble costs about 3x the training time, storage and prediction work of one model.

## How to run
1. Open `08_ensemble.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/ensemble_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/accuracy_comparison.png`: Test accuracy of each model and the ensemble

## Files in this folder
- `08_ensemble.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- The three models share one architecture, so their mistakes may be similar.
- Only 3 models were used.
- One data split.
