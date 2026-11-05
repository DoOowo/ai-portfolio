# Report: Pruning

## 1. Goal
How much accuracy do we lose when we set the smallest weights of a trained network to zero? 

## 2. Setup
| Item | Value |
|---|---|
| Dataset | Fashion-MNIST (28x28 grayscale clothing images, 10 classes) |
| Split | 12,000 train / 3,000 validation / 10,000 test |
| Model | MLP (784 -> 256 -> 128 -> 10) |
| Setting | One baseline trained for 3 epochs (Adam, learning rate 0.001, batch size 64) |
| Setting | Global L1 unstructured pruning of all Linear layers at 30% and 60% |
| Setting | Pruning is applied to copies of the same trained model, with no fine-tuning afterwards |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Model | Requested pruning | Actual sparsity | Test accuracy |
|---|---|---|---|
| Baseline | 0,0 | 0,0 | 84,06% |
| Pruned 30% | 0,3 | 0,30002 | 84,12% |
| Pruned 60% | 0,6 | 0,59999 | 84,15% |

## 4. Discussion
> **Remember to mention:** Pruned weights are still stored as zeros inside normal (dense) tensors, so the saved file is not smaller and inference is not automatically faster.

- Is the actual sparsity close to the requested amount?
  - Answer: Yes it relatively is
- Why might a high-sparsity model still work reasonably well?
  - Answer: Because the smallest weights of a trained network are small enough to be negligible, removing them will not alter the results much

## 5. Limitations
1. No fine-tuning after pruning, which is the normal next step in practice.
2. Only two pruning levels were tested.
3. One run with one seed.

## 6. Conclusion
In this experiment, pruning suprisingly improved our trained network's accuracy, we noticed that the higher the sparcity the more accurate the network is. Although a single run cannot rule out noise. A natural next step is to fine-tune after pruning, or test more pruning levels such as 80% and 90%.


## References
- Xiao, H., Rasul, K., Vollgraf, R. (2017). *Fashion-MNIST.* (for Fashion-MNIST projects)
- Han et al. (2015), Learning both Weights and Connections for Efficient Neural Networks
- PyTorch documentation: https://pytorch.org/docs/stable/
