# Report: Regularization (Dropout and Weight Decay)


## 1. Goal

Do dropout and weight decay reduce overfitting in a small network?
## 2. Setup
| Item | Value |
|---|---|
| Dataset | Fashion-MNIST (28x28 grayscale clothing images, 10 classes) |
| Split | 12,000 train / 3,000 validation / 10,000 test |
| Model | MLP (784 -> 256 -> 128 -> 10) |
| Four versions | baseline, dropout 0.3, weight decay 0.001, and both |
| Setting | 3 epochs each (Adam, learning rate 0.001, batch size 64) |
| Setting | The same seed is reset before each run so starting weights match |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Condition | Dropout | Weight decay | Final train loss | Final val loss | Test accuracy |
|---|---|---|---|---|---|
| Baseline | 0 | 0 | 0.3852 | 0.3902 | 84,06% |
| Dropout | 0,3 | 0 | 0.4562 | 0.4193 | 83,73% |
| Weight decay | 0 | 0,001 | 0.3982 | 0.4036 | 83.68% |
| Both | 0,3 | 0,001 | 0.4700 | 0.4295 | 83,04% |

## 4. Discussion

- For each version, how big is the gap between training and validation loss?
  - Answer: The gaps is usually big by about 0,05
- Did any method shrink the gap?
  - Answer: weight decay shrunk the gap by 0,04
- Does any version look underfit (both losses still high)?
  - Answer: the version with both versions looks underfit

## 5. Limitations

1. One setting per method, so this is a demo and not a tuning search.
2. Only 3 epochs, which may be too short for overfitting to appear.
3. One run with one seed.

## 6. Conclusion
In this experiment, we compared way to stop a network from overfitting with dropout, weight decay, as well as both of them together. We deduced that weight decay was the most effective in reducing that overfitting. A natural next step is to try several dropout rates and weight decay values, and train for more epochs.

## References
- Xiao, H., Rasul, K., Vollgraf, R. (2017). *Fashion-MNIST.* (for Fashion-MNIST projects)
- Srivastava et al. (2014), Dropout: A Simple Way to Prevent Neural Networks from Overfitting
- PyTorch documentation: https://pytorch.org/docs/stable/
