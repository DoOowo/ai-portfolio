# Project 02: Pruning

**Question:** How much accuracy do we lose when we set the smallest weights of a trained network to zero?

## What this project does
Compares: Baseline vs 30% pruned vs 60% pruned.

## Data and model
- **Dataset:** Fashion-MNIST (28x28 grayscale clothing images, 10 classes)
- **Split:** 12,000 train / 3,000 validation / 10,000 test
- **Model:** MLP (784 -> 256 -> 128 -> 10)

## Settings
- One baseline trained for 3 epochs (Adam, learning rate 0.001, batch size 64)
- Global L1 unstructured pruning of all Linear layers at 30% and 60%
- Pruning is applied to copies of the same trained model, with no fine-tuning afterwards
- Seed: 42

> **Note:** Pruned weights are still stored as zeros inside normal (dense) tensors, so the saved file is not smaller and inference is not automatically faster.

## How to run
1. Open `02_pruning.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/pruning_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/pruning_accuracy.png`: Test accuracy vs percentage of weights set to zero

## Files in this folder
- `02_pruning.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- No fine-tuning after pruning, which is the normal next step in practice.
- Only two pruning levels were tested.
- One run with one seed.
