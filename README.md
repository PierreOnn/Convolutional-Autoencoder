# ACML-Assignment-2
The project entailed the development of an AutoEncoder architecture for image reconstruction. Therefore, the implementation was built upon the library TensorFlow / Keras as it has excellent support to run with the traditional Google engine of Colaboratory. The latter IDE was chosen over Pycharm as the notebook provides a connection with a single NVIDIA GPU to perform parallel computations with CUDA. This is necessary as some basic Tensorflow operations benefit from the provided speedup capability, especially when operating in a deep learning environment.

The results from different runs where tracked using Weights and Biases, a tool for experiment tracking. Herewith, hyperparameters are defined to tune upfront and run the experiments on multiple machines simultaneously. The upshift of this approach was a reduced coordination and experiment tracking overhead while everything was assembled in comprehensive graphs. On the other hand, a well-defined configuration with the tool was needed so that the data being tracked had a clear documentation.

## Exercise 1
Evaluation of the proposed AutoEncoder architecture.

Notice that 'accuracy' is used as an additional metric in Keras. During training, the *loss* goes down and the *accuracy* up which implies a working model.
However, Keras documentation describes the working of the accuracy metric as follows: *"Calculates how often predictions equal labels"*(https://keras.io/api/metrics/accuracy_metrics/#accuracy-class).

Therefore, as this assignment involves image reconstruction and not image classification, the **loss** is a more appropriate metric to evaluate and enhance the model.
The test error is interpreted as the validation loss.

## Exercise 2
In order to tune the hyperparameters, Weights and Biases is used as a platform to retain and display insights about the initial AE architecture.
In regard to the configuration values, sweeps are executed at random which chooses a random set of values on each iteration. This search method is surprisingly effective to reach and identify good parameters for the architecture.

The following API key could be used as a login to W&B: 3baf9835f7643ccdd5a2df4c3d89245c61479e0f

Now, when logged in and the agent has started, it should be able to run the code in regard to the predefined sweep configuration files and collect the outcomes on the platform. Unfortunately because of the deep integration for hyperparameter tuning, it is not possible to run that code without Weights and Biases.

## Exercise 3
The YIQ color space is used to capture the lumincance and chrominance of an image (https://en.wikipedia.org/wiki/YIQ).

The Y or gray-scale component represents the luminance or sharpness of the image, the AE has to learn the two remaining I and Q channels for colorization. This reduces the size of the network and stimulates a faster convergence.
