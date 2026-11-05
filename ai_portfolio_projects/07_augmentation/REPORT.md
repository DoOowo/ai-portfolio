# Report: Data Augmentation

## 1. Goal
Does showing the model randomly shifted and flipped training images improve accuracy on new images?

## 2. Setup
| Item | Value |
|---|---|
| Dataset | CIFAR-10 (32x32 color images, 10 classes) |
| Split | 10,000 train / 2,000 validation / 10,000 test |
| Model | Small CNN (2 conv layers + 2 linear layers) |
| Setting | Baseline vs augmented training images (random crop with padding 4 + random horizontal flip) |
| Setting | Same image indices for both, so only the augmentation differs |
| Setting | 2 epochs each (Adam, learning rate 0.001, batch size 64) |
| Setting | Validation and test images are never augmented |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Condition | Test accuracy | Test loss | Training time (s) |
|---|---|---|---|
| Baseline | 0.5357 | 1.289844 | 25.584208 |
| Augmented | 0.5020 | 1.389334 | 26.801982 |

## 4. Discussion

- Did augmentation improve test accuracy?
  - Answer: No it did not
- Did it change training time?
  - Answer: It actually increased training time
- If it did not help, why might that be? 
  - Answer: Since augmentation was only used for training, the model had a hard time recognising mirrored shapes compared to shapes it's familiar with

## 5. Limitations

1. Only 2 epochs: augmentation usually pays off with longer training.
2. Only two types of augmentation were used.
3. One run with one seed.

## 6. Conclusion
In this experiment, we wanted to experiment whether mirroring images will improve accuracy(augmentation), we deduced that it does not comparet to a regular approach. A natural next step is to train for more epochs and try other augmentations.

## References
- Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton at the University of Toronto (2009)(CIFAR10)
- Krizhevsky (2009), Learning Multiple Layers of Features from Tiny Images
- PyTorch documentation: https://pytorch.org/docs/stable/
