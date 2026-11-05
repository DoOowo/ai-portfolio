# Report: Learning Rate Schedule

## 1. Goal

Does cutting the learning rate during training (StepLR) help compared with a constant learning rate?
## 2. Setup
| Item | Value |
|---|---|
| Dataset | Fashion-MNIST (28x28 grayscale clothing images, 10 classes) |
| Split | 12,000 train / 3,000 validation / 10,000 test |
| Model | MLP (784 -> 256 -> 128 -> 10) |
| Setting | Constant learning rate 0.001 vs StepLR (halve the rate every 2 epochs) |
| Setting | 4 epochs each (Adam, batch size 64) |
| Setting | The same seed is reset before each run |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Condition | Final val loss | Test accuracy | Test loss | Training time (s) |
|---|---|---|---|---|
| Constant |0.3927  | 0.8403 | 0.439023 | 12.014547 |
| StepLR | 0.3768 | 0.8416 | 0.422568 | 12.051690 |

## 4. Discussion

- Which setting reached a lower validation loss, and when?
  - Answer: StepLR reached the lowest validation loss at epoch 3/4
## 5. Limitations
1. 4 epochs and one schedule cannot show that one scheduler is always better.
2. The result depends on the dataset, optimizer, starting rate and schedule settings.
3. One run with one seed.

## 6. Conclusion
In this experiment, we compared a constant learning rate with one that is cut in half every 2 epochs(StepLR). We noticed a decline in the validation loss for the second condition with a learning rate cut in half as well. A natural next step is to try other schedules (cosine, exponential) and starting rates.

## References
- Xiao, H., Rasul, K., Vollgraf, R. (2017). *Fashion-MNIST.* (for Fashion-MNIST projects)
- Smith (2017), Cyclical Learning Rates for Training Neural Networks
- PyTorch documentation: https://pytorch.org/docs/stable/
