
# Notes on Deep Learning

## Basics
1. [Building Neural Network from Scratch](https://thecodacus.com/neural-network-scratch-python-no-libraries/)
1. [Learning AI if you suck at Math](https://hackernoon.com/learning-ai-if-you-suck-at-math-p4-tensors-illustrated-with-cats-27f0002c9b32)
1. [Exploring Linear Algebra with Python](https://mubaris.com/2017-09-25/exploring-linear-algebra-with-python)
1. [Linear Programming with Pulp](http://benalexkeen.com/linear-programming-with-python-and-pulp/)
1. [deeplearn.js Tutorial](https://deeplearnjs.org/docs/tutorials/intro.html)
1. [Github: Teachable Machine Learning](https://github.com/googlecreativelab/teachable-machine)
1. [pyTorch Zero to All](https://github.com/hunkim/PyTorchZeroToAll)
1. [Integrating Keras & TensorFlow: The Keras workflow, expanded](https://www.youtube.com/watch?v=UeheTiBJ0Io)
1. [Deep Learning: Keras Short Tutorial](https://www.youtube.com/wavenet-generative-model-raw-audioch?v=Tp3SaRbql4k)


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
1. [Neural Network in Python 15 lines](https://iamtrask.github.io/2015/07/12/basic-python-network/)
1. [Hey Siri: An On-device DNN-powered Voice Trigger for Apple’s Personal Assistant](https://machinelearning.apple.com/2017/10/01/hey-siri.html)
1. [What does AI code look like?](https://www.quora.com/What-does-AI-code-look-like/answer/Mikkel-Duif?srid=a9)
1. [WaveNet: A Generative Model for Raw Audio](https://deepmind.com/blog/wavenet-generative-model-raw-audio/)
1. [Using neural networks to detect car crashes in dashcam footage](https://blog.insightdatascience.com/crash-catcher-detecting-car-crashes-in-video-9c0522b04558)
1. [Creating a Modern OCR Pipeline Using Computer Vision and Deep Learning](https://blogs.dropbox.com/tech/2017/04/creating-a-modern-ocr-pipeline-using-computer-vision-and-deep-learning/)
1. [What is the state of art in scanned document text detection, Optical Character recognition (OCR) pipeline from a computer vision perspective ?](https://www.quora.com/What-is-the-state-of-art-in-scanned-document-text-detection-Optical-Character-recognition-OCR-pipeline-from-a-computer-vision-perspective)
1. [Nordic.js 2017 • Amir Hossein Rahnama - Lightning talk: Machine Learning Intuitions for DeepLearn.js](https://www.youtube.com/watch?v=5bwlH0j5rQk)
1. [An Overview of the Tesseract OCR Engine](http://citeseerx.ist.psu.edu/viewdoc/download;jsessionid=E6122958EB8D16F13E0EEC460D6207E5?doi=10.1.1.308.445&rep=rep1&type=pdf)
1. [Tesseract.js](https://github.com/naptha/tesseract.js#tesseractjs)
1. [ConvNetJS – Deep Learning in your browser](https://www.youtube.com/watch?v=nAHcrz5hxc4)
1. [OCR AND MEDIEVAL MANUSCRIPTS: ESTABLISHING A BASELINE](https://brandonwhawk.net/2015/04/20/ocr-and-medieval-manuscripts-establishing-a-baseline/)
1. [Hacker's guide to Neural Networks](http://karpathy.github.io/neuralnets/)
1. [200 universities just launched 600 free online courses](https://qz.com/1120344/200-universities-just-launched-600-free-online-courses-heres-the-full-list/)