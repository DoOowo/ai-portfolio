# Report: Image Classification with a CNN

## 1. Goal
How well can a small CNN classify CIFAR-10 images, and which categories does it confuse?

## 2. Setup
| Item | Value |
|---|---|
| Dataset | CIFAR-10 (32x32 color images, 10 classes) |
| Split | 50,000 train / 10,000 test (no separate validation set) |
| Model | Small CNN (2 conv layers + 2 linear layers) |
| Setting | 5 epochs (Adam, learning rate 0.001, batch size 64) |
| Setting | Images normalized to the range -1 to 1 |
| Outputs | results/ folder (plots, weights, results.txt, ZIP) |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Metric | Value |
|---|---|
| Test accuracy | 72.23% |
| Test loss | 0.8135 |
| Last training accuracy | 78.56% |
| Training time (min) | 8.29 |

## 4. Discussion

- How does training accuracy compare with test accuracy? What could a big gap mean?
  - Answer: the last training accuracy is higher that the actual test accuracy, a big cap would mean that the model struggled to recognise osme images
- Which categories have the lowest and highest accuracy?
  - Answer: the lowest accuracy is for cat and dog class(~57%), and the highest is for airplane, frog, and ship(>80%)
- Which pairs are confused most often ?
  - Answer: the pairs are usually cat and dog, automobile and truck, and airplane and ship according to the confusion matrix
- Why might some images be hard to classify ?
  - Answer: some images may be harder to classify because of the size of the subject, their shape, odd poses ...

## 5. Limitations
1. Small CNN, only 5 epochs, no augmentation.
2. No validation set, so no settings were tuned.
3. One run with one seed.

## 6. Conclusion
In this experiment, we trained a small CNN on a database to recognise 10 kinds of pictures. We realised that some pictures are easy to classify, other are not depending on the conent of the image. A natural next step is to train longer, add augmentation, or try a deeper network.

## References
- Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton at the University of Toronto (2009)(CIFAR10)
- Krizhevsky, A. (2009). *Learning Multiple Layers of Features from Tiny Images.* (for CIFAR-10 projects)
- PyTorch documentation: https://pytorch.org/docs/stable/
