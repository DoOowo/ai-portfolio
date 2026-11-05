# Project 06: Learning Rate Schedule

**Question:** Does cutting the learning rate during training (StepLR) help compared with a constant learning rate?

## What this project does
Compares: Constant vs StepLR.

## Data and model
- **Dataset:** Fashion-MNIST (28x28 grayscale clothing images, 10 classes)
- **Split:** 12,000 train / 3,000 validation / 10,000 test
- **Model:** MLP (784 -> 256 -> 128 -> 10)

## Settings
- Constant learning rate 0.001 vs StepLR (halve the rate every 2 epochs)
- 4 epochs each (Adam, batch size 64)
- The same seed is reset before each run
- Seed: 42

## How to run
1. Open `06_learning_rate.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/learning_rate_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/validation_loss.png`: Validation loss per epoch
- `outputs/learning_rate_schedule.png`: Learning rate per epoch

## Files in this folder
- `06_learning_rate.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- 4 epochs and one schedule cannot show that one scheduler is always better.
- The result depends on the dataset, optimizer, starting rate and schedule settings.
- One run with one seed.
