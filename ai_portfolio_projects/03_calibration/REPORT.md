# Report: Calibration (Temperature Scaling)


## 1. Goal
Is the model's confidence honest, and can temperature scaling make it more honest without changing predictions? 
## 2. Setup
| Item | Value |
|---|---|
| Dataset | CIFAR-10 (32x32 color images, 10 classes) |
| Split | 10,000 train / 2,000 validation / 10,000 test |
| Model | Small CNN (2 conv layers + 2 linear layers) |
| Setting | Trained for 2 epochs (Adam, learning rate 0.001, batch size 64) |
| Setting | Temperature found by searching 0.5 to 5.0 (step 0.05) on the validation set only |
| Setting | ECE measured with 10 bins |
| Noise test | Gaussian noise with standard deviation 0.10 added to the test images |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Condition | Accuracy | Loss | ECE |
|---|---|---|---|
| Clean, before scaling | 52,96% | 1,303 | 0,008638 |
| Clean, after scaling | 52,96% | 1,303 | 0,008638 |
| Noisy, before scaling | 52,78% | 1,307 | 0,008377 |


## 4. Discussion

- Did ECE go down after temperature scaling? By how much?
  - Answer: The ECE went down by 0,000039
- Did accuracy stay the same? (It should.)
  - Answer: yes it stayed the same
- Was the fitted temperature above or below 1, and what does that say about the model (over- or under-confident)?
  - Answer: the fitted temperature was exactly 1(done on the validation set). The model is neither overconfident nor underconfident. It relies on what it learned during training.


## 5. Limitations

1. ECE depends on the number of bins.
2. Gaussian noise is only one simple stress test, not full robustness testing.
3. The CNN is trained for only 2 epochs on 10,000 images.

## 6. Conclusion
In this experiment, We used temperature scaling to adjust a model's confidence(CNN). Even though the fitted temperature was exactly 1, modern CNNs tend to be naturally overconfident.Although a single run cannot rule out noise. A natural next step is to plot a reliability diagram, or try a longer-trained model.

## References
- Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton at the University of Toronto (2009)(CIFAR10)
- 	Guo et al. (2017), On Calibration of Modern Neural Networks
- PyTorch documentation: https://pytorch.org/docs/stable/
