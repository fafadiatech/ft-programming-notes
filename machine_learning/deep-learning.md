
# Notes on Deep Learning

## Basics
1. [Building Neural Network from Scratch](https://thecodacus.com/neural-network-scratch-python-no-libraries/)
1. [Learning AI if you suck at Math](https://hackernoon.com/learning-ai-if-you-suck-at-math-p4-tensors-illustrated-with-cats-27f0002c9b32)
1. [Exploring Linear Algebra with Python](https://mubaris.com/2017-09-25/exploring-linear-algebra-with-python)
1. [Linear Programming with Pulp](http://benalexkeen.com/linear-programming-with-python-and-pulp/)
1. [deeplearn.js Tutorial](https://deeplearnjs.org/docs/tutorials/intro.html)
1. [Github: Teachable Machine Learning](https://github.com/googlecreativelab/teachable-machine)
1. [pyTorch Zero to All](https://github.com/hunkim/PyTorchZeroToAll)



## [DeepLearning.tv](https://www.youtube.com/watch?v=b99UVkWzYTQ)

- GEOFF HILTON {Father of DNN}
- MLP {Multi Layered Perceptron} -> Vanialla Neural Network
- Problem of Vanishing Gradient {This is what RBM Solves}

### Unsupervised

#### RBM {Extract features and reconstruct inputs}

- Forward/Backward Phase

#### Autoencoders {Family of algo to which RBM belongs to}

- Idenfity patterns in dataset
- Denoising
- Contractive
- Unlabelled Input -> Try to Reconstruct Input as Possible
- Feature Extraction Engine
- Shallow
- Backprogation with Lost
- Deep Auto-Encoder [28 x 28] -> 30
- Better than PCA

### Supervised

#### DBN {Feed Forward}

- Combine multiple RBMs
- Hidden Layer of one RBM is Visible Layer of another RBM
- Useful in scenarios where we have small sample of Trained Data
- Training process get completed in reasonable amount of time

#### CNN {Feed Forward}

- Machine Vision is where CNN is used
- ImageNet competition
- [Andrej Karpathy's Note](http://cs231n.github.io/)
- Layers:
    - Convolution Layer
        - Technical Operation {Convolution} to search for pattern
    - Relu {Rectified Linear Unit}
        - Used for reducing training time for early layers
    - Pooling
        - Used for dimensionality reduction
    - Fully Connected Layer
        - Allows network to classify data from samples based on patterns discovered by Polling layer
- Since this is supervised method, take large sample of labeled data

#### RNN

- If patterns change over time is where RNN is useful
- Application {Speech Recognization, Driverless Car}
- Output of layer is fed back to the same layer along with inputs
- Applications
    - Sequences of Input to Produce Sequences of Output
    - Image Captioning {Singel Input, Multiple Output}
    - Document Classification {Single Input, Single Output}
    - Video Classification {Multiple Input, Multiple Output}
    - Forecasting {with time Delays}
- Stacking
- Difficult to train because of Vanishing Gradients
- Solution:
    - Gating {Method of deciding for network when to forget current input or consider current input}
        - LSTM
        - GRU
    - Gradient Clipping
    - Better Optimizers
    - Steeper Gates
- GPUs prefered methods of training
- RNN suited for timeseries data
- Feedforward: Classification/Regression
- Recurrent Neural Network: Forecaster

#### RNTN {Recursive Neural Tensor Nets}

- For applications like Parsing
- 3 Basic Component
    - Root {Fires out Class and Score}
    - Child Nodes {Leafs}
- Collection of Recursive Binary Tress
- Score repesent quality
- Text
    - Parsing
    - Sentiement Analysis
- Image Parsing {Break Image into many different components}

## Fast.ai

[Fast.ai](http://course.fast.ai/index.html) is an online free course for deep learning. Following is quote from their official website

>>Welcome to fast.ai's 7 week course, Practical Deep Learning For Coders, Part 1, taught by Jeremy Howard (Kaggle's #1 competitor 2 years running, and founder of Enlitic). Learn how to build state of the art models without needing graduate-level math—but also without dumbing anything down. Oh and one other thing... it's totally free!

Note: [DeepSchool.io](https://github.com/sachinruk/deepschool.io) has also opensource its course.

## Frameworks

1. [Microsoft CNTK](https://www.youtube.com/watch?v=pl-kbFJ1KzU)
1. [Amazon Dsstne](https://github.com/amzn/amazon-dsstne)
1. [Microsoft's ELL](https://github.com/Microsoft/ELL)

## Blog Posts

1. [AlphaGo Zero](https://deepmind.com/blog/alphago-zero-learning-scratch/)