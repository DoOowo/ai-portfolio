# Report: Quantization (Dynamic INT8)

## 1. Goal
How much smaller and faster does a network get when its Linear layers use 8-bit integers instead of 32-bit decimals? 

## 2. Setup
| Item | Value |
|---|---|
| Dataset | Fashion-MNIST (28x28 grayscale clothing images, 10 classes) |
| Split | 12,000 train / 3,000 validation / 10,000 test |
| Model | MLP (784 -> 256 -> 128 -> 10) |
| Setting | FP32 model trained for 3 epochs (Adam, learning rate 0.001, batch size 64) |
| Setting | Dynamic INT8 quantization of the Linear layers (CPU only) |
| Latency | median of 5 repeats over 20 test batches of size 64 |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Model | Test accuracy | File size (MB) | Time per batch (ms) |
|---|---|---|---|
| FP32 | 0.8419 | 0.943345 | 0.440812 |
| Dynamic INT8 | 0.8416 | 0.241097 | 0.336969 |

## 4. Discussion
- How much smaller is the INT8 file (percentage)?
  - Answer: the file is smaller by 75%
- Did accuracy change?
  - Answer: Accuracy stayed the same
- Was INT8 actually faster?
  - Answer: Yes it is faster by 25%


## 5. Limitations

1. Timing is noisy on a shared Colab CPU.
2. Results may not carry over to other hardware.
3. Only the Linear layers were quantized, not every tensor in the model.

## 6. Conclusion
In this experiment, time and file size were reduced in INT8 compared to FP32 with no loss in accuracy. although a single run cannot rule out noise. A natural next step is to try a CNN, or static quantization.

## References
- Xiao, H., Rasul, K., Vollgraf, R. (2017). *Fashion-MNIST.* (for Fashion-MNIST projects)
- 	Jacob et al. (2018), Quantization and Training of Neural Networks for Efficient Integer-Arithmetic-Only Inference
- PyTorch documentation: https://pytorch.org/docs/stable/
