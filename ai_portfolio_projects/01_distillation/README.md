# Project 01: Knowledge Distillation

**Question:** Can a small model learn from a big model's soft predictions and beat the same small model trained normally?

## What this project does
Compares: Teacher vs plain student vs distilled student.

## Data and model
- **Dataset:** Fashion-MNIST (28x28 grayscale clothing images, 10 classes)
- **Split:** 12,000 train / 3,000 validation / 10,000 test
- **Model:** Teacher: 1 hidden layer, 512 units (about 407,050 parameters). Student: 1 hidden layer, 32 units (about 25,450 parameters).

## Settings
- Epochs: 3 for every model
- Optimizer: Adam, learning rate 0.001, batch size 64
- Distillation: temperature T = 3, alpha = 0.5 (weight on the teacher loss)
- Seed: 42

## How to run
1. Open `01_distillation.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/distillation_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/accuracy_comparison.png`: Test accuracy of the three models

## Files in this folder
- `01_distillation.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- Only one run with one seed, so small differences may be noise.
- Only one temperature (3) and one alpha (0.5) were tried.
- Only 3 epochs of training.
