# Report: Knowledge Distillation

## 1. Goal

Can a small model(student) learn from a big model's(teacher) soft predictions, and can it beat the same small model trained normally?

## 2. Setup
| Item | Value |
|---|---|
| Dataset | Fashion-MNIST (28x28 grayscale clothing images, 10 classes) |
| Split | 12,000 train / 3,000 validation / 10,000 test |
| Model | Teacher: 1 hidden layer, 512 units (about 407,050 parameters). Student: 1 hidden layer, 32 units (about 25,450 parameters). |
| Epochs | 3 for every model |
| Optimizer | Adam, learning rate 0.001, batch size 64 |
| Distillation | temperature T = 3, alpha = 0.5 (weight on the teacher loss) |
| Seed | 42 |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0+cpu |

## 3. Results

| Model | Parameters | Test accuracy | Test loss | Training time (s) |
|---|---|---|---|---|
| Teacher | 407050 | 83,12% | 46,31% | 15 |
| Student (plain) | 25450 | 82,91% | 11,91% | 12 |
| Student (distilled) | 25450 | 82,61% | 13,56% | 14 |


## 4. Discussion

- Did the distilled student beat the plain student?
  - Answer: No, it did not. The point was to maximize accuracy, minimise loss and training time, which the distilled student failed to do
- How close is each student to the teacher?
  - Answer: Both students are close to the teacher by about 0,5%
- How many fewer parameters does the student have (as a percentage)?
  - Answer: about 6,25%
- What is a likely reason distillation helped or did not help? Label this as a guess.
  - Answer: My guess would be the applied optimization on the distilled student


## 5. Limitations

1. Only one run with one seed, so small differences may be noise.
2. Only one temperature (3) and one alpha (0.5) were tried.
3. Only 3 epochs of training.

## 6. Conclusion
In this experiment, sharing soft predicitons from a big model to a smaller one did not improve the smaller model's training in comparison to the same small model trained normally. Although a single run cannot rule out noise. A natural next step is to try several temperatures and alphas, or repeat with different seeds.

## References
- Xiao, H., Rasul, K., Vollgraf, R. (2017). *Fashion-MNIST.* (for Fashion-MNIST projects)
- Hinton, Vinyals & Dean (2015), Distilling the Knowledge in a Neural Network
- PyTorch documentation: https://pytorch.org/docs/stable/
