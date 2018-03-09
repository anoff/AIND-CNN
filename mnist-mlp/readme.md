# Notes on mini-project modifications

> Base performance of the model is `98.21%` in `10 epochs` with `669,706` parameters.

## Increase (or decrease) the number of nodes in each of the hidden layers. Do you notice evidence of overfitting (or underfitting)?

> ⬇️ By reducing the complexity of the model by `~ 1/7` (going from 512x512 to 128x64) the accuracy dropped from `98.2% to 97.8%` within the existing 10 epochs. This could be classified as minor underfitting.

> ⬇️ Reducing the complexity even further to just `25,818` parameters (64x32 nodes) in the hidden layer yields an accuracy of `95.4%`. The reduced complexity allows for higher epoch count to train in the same time. Which is not beneficial to the overall accuracy as the best accuracy is reached within the first 10 epochs.

> ⬆️ Increasing the complexity by `2` (1024x512) gives an accuracy of `97.6%`. As the loss on the training set kept decreasing over the whole 10 epochs but the validation accuracy reached peak at epoch#3 this is a clear sign of overfitting.

## Increase (or decrease) the number of hidden layers. Do you notice evidence of overfitting (or underfitting)?

> ⬇️ Going to `1 hidden layer` with 512 nodes the model achieves `97.97%` accuracy but keeps improving on the validation set for quite some time.

> ⬇️ `1 hidden layer` with `128` nodes still yields `97.7%` performance so further decreasing the model complexity seems reasonable. Although it reached peak accuracy at epoch `8/10`.

> ⬇️ `1 hidden layer` with `32` nodes still yields `95.7%`. As the model stagnates on the training loss it is a clear sign of *underfitting*.

> ⬇️ Going to `3 hidden layer` with 512 nodes the model achieves `97.4%` accuracy. As the base model is also more prone to overfitting with the given complexity, this even more complex architecture also results in a very early peak accuracy (epoch `3/10`) and would start overfitting if it weren't for _dropouts_.

## Remove the dropout layers in the network. Do you notice evidence of overfitting?

> The model reaches peak accuracy on the validation set on epoch `2` and shows clear signs of overfitting with validation and training loss differentiating by a factor of `10`. Accuracy on the test set still reaches `97.5%`.

## Remove the ReLU activation functions. Does the test accuracy decrease?

> Going from `ReLU` to `sigmoid` results in a slower training as the loss on validation keeps decreasing throughout all 10 epochs. The final accuracy on the test set is `97.7%`. Not a lot worse than the original architecture.

## Remove the image pre-processing step with dividing every pixel by 255. Does the accuracy decrease?

> Running the model on the full range of `0..255` values for each pixel starts the training process of with a `10x` higher initial loss than compared to the normalized data. This is expected as the absolute value ranges of the points are now a lot bigger which in turn means the misclassifications yield bigger absolute numbers and therefore bigger losses. After `10 epochs` the accuracy on the test set is a mere `37.98%` the worst so far.

## Try a different optimizer, such as stochastic gradient descent.

| Optimizer | Accuracy [%] | Training duration [s] |
|-----------|--------------|-----------------------|
| rmsprop   |      97.87   |           111         |
| sgd       |      98.37   |            95         |
| adagrad   |      98.38   |          114          |
| adam      |      98.22   |            131        |
| nadam     |      97.67   |              171      |

> SGD is faster and most accurate

## Increase (or decrease) the batch size.

| Batch Size | Accuracy [%] | Training duration [s] |
|-----------|--------------|-----------------------|
| 32        |    98.43     |        234            |
| 128       |    98.33     |         98            |
| 100       |    98.37     |        121            |
| 256       |    98.44     |         96            |
| 512       |    98.45     |         88            |

> Higher batch size ➡️ faster learning, slightly less accuracy
