# Project 05: Quantization (Dynamic INT8)

**Question:** How much smaller and faster does a network get when its Linear layers use 8-bit integers instead of 32-bit decimals?

## What this project does
Compares: FP32 vs dynamic INT8.

## Data and model
- **Dataset:** Fashion-MNIST (28x28 grayscale clothing images, 10 classes)
- **Split:** 12,000 train / 3,000 validation / 10,000 test
- **Model:** MLP (784 -> 256 -> 128 -> 10)

## Settings
- FP32 model trained for 3 epochs (Adam, learning rate 0.001, batch size 64)
- Dynamic INT8 quantization of the Linear layers (CPU only)
- Latency: median of 5 repeats over 20 test batches of size 64
- Seed: 42

> **Note:** State your hardware (Colab CPU), PyTorch version, batch size (64) and how you timed it.

## How to run
1. Open `05_quantization.ipynb` in Google Colab (CPU runtime is fine) or Jupyter.
2. Install the libraries if needed: `pip install torch torchvision numpy pandas matplotlib scikit-learn`
3. Run the cells from top to bottom. The dataset downloads automatically into `data/` the first time.
4. Download your results before the Colab runtime disconnects, because its files are deleted.

## Outputs
- `outputs/quantization_results.csv`: the results table (saved automatically)
- Figures (add a `plt.savefig(...)` line before each `plt.show()`):
- `outputs/model_size.png`: Saved file size (MB)
- `outputs/latency.png`: CPU time per batch (ms)

## Files in this folder
- `05_quantization.ipynb`: the notebook
- `README.md`: this file
- `REPORT.md`: report template (fill in after running)

## Results
Fill in after running. Copy the numbers from the notebook output or the CSV file into `REPORT.md`.

## Limitations
- Timing is noisy on a shared Colab CPU.
- Results may not carry over to other hardware.
- Only the Linear layers were quantized, not every tensor in the model.
