# Notes on mini-project modifications

> Base performance of the model is `98.21%` in `10 epochs` with `669,706` parameters.

## Increase (or decrease) the number of nodes in each of the hidden layers. Do you notice evidence of overfitting (or underfitting)?

> By reducing the complexity of the model by `~ 1/7` (going from 512x512 to 128x64) the accuracy dropped from `98.2% to 97.8%` within the existing 10 epochs. This could be classified as minor underfitting.

> Reducing the complexity even further to just `25,818` parameters (64x32 nodes) in the hidden layer yields an accuracy of `95.4%`. The reduced complexity allows for higher epoch count to train in the same time. Which is not beneficial to the overall accuracy as the best accuracy is reached within the first 10 epochs.

## Increase (or decrease) the number of hidden layers.  Do you notice evidence of overfitting (or underfitting)?

## Remove the dropout layers in the network.  Do you notice evidence of overfitting?

## Remove the ReLU activation functions.  Does the test accuracy decrease?

## Remove the image pre-processing step with dividing every pixel by 255.  Does the accuracy decrease?

## Try a different optimizer, such as stochastic gradient descent.

## Increase (or decrease) the batch size.