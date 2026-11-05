# Report: Ensemble of Models

## 1. Goal
Does averaging the predictions of three networks beat each single network?  

## 2. Setup
| Item | Value |
|---|---|
| Dataset | Fashion-MNIST (28x28 grayscale clothing images, 10 classes) |
| Split | 12,000 train / 3,000 validation / 10,000 test |
| Model | MLP (784 -> 256 -> 128 -> 10), trained three times |
| Three models with different seeds | 11, 22, 33 |
| Setting | 3 epochs each (Adam, learning rate 0.001, batch size 64) |
| Setting | Ensemble = the average of the three models' predicted class probabilities |
| Hardware | Google Colab CPU runtime |
| PyTorch version | 2.11.0 |

## 3. Results

| Model | Test accuracy | Test loss |
|---|---|---|
| MLP seed 11 | 0.8280 | 0.465000 |
| MLP seed 22 | 0.8430 | 0.431854 |
| MLP seed 33 | 0.8305 | 0.478040 |
| Ensemble | 0.8562 | 0.407862 |

## 4. Discussion
- Did the ensemble beat the best single model (not only the average one)?
  - Answer: The ensemble beat all 3 models separately in both test accuracy and test loss
- What is the cost: training time, storage and prediction time?
  - Answer: The cost in training time is 24.8s, since we ensemble 3 models, it will take 3x more time, storage and prediciton work of 1 model

## 5. Limitations
1. The three models share one architecture, so their mistakes may be similar.
2. Only 3 models were used.
3. One data split.

## 6. Conclusion
In this experiment, we attempted to train 3 networks and average their predicitons to improve accuracy. Although it did work, it came at the cost of 3x more resources of training a single model. A natural next step is to try more models or different architectures.

## References
- Xiao, H., Rasul, K., Vollgraf, R. (2017). *Fashion-MNIST.* (for Fashion-MNIST projects)
- 	Lakshminarayanan, Pritzel & Blundell (2017), Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles
- PyTorch documentation: https://pytorch.org/docs/stable/
