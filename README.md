# CEAM-Neural-Network-Assignment

## 1. Objective

The objective of this project was to build a complete image classification pipeline using a custom dataset and to experimentally investigate how neural networks learn during training.
A Convolutional Neural Network was developed using PyTorch to classify three object categories: Bottle, Watch and Scissors. The project involved dataset collection, preprocessing, model design, training and evaluation.

Through this project, I aimed to develop practical intuition regarding ERM, Forward Propagation and Backpropagation, Optimization and Gradient Descent, Learning Rate Selection, Batch Size Effects, Regularization Techniques, Dropout, Overfitting vs Generalization, Training Stability. Instead of focusing just on achieving high accuracy, the purpose of the project was to understand why neural networks behave the way they do.


## 2. Dataset Creation

A custom image dataset was created consisting of three object classes: Bottle, Watch, Scissors.
Approximately 30 images were collected for each class, resulting in a dataset of around 90 images. To improve diversity, images were captured from different viewing angles, distances and lighting conditions. 
The dataset was split into: 70% Training Set, 15% Validation Set, 15% Test Set

## 3. Model Architecture

A lightweight Convolutional Neural Network (CNN) was implemented using PyTorch.

The architecture consists of: 
* Two convolutional layers for feature extraction
* ReLU activation functions for non-linearity
* Max pooling layers for spatial downsampling
* Fully connected dense layers for classification
* Optional dropout layers for regularization experiments

The final output layer contains three neurons corresponding to the three target classes. Cross Entropy Loss was used as the loss function, while the Adam optimizer was used for weight updates during training.

## 4. Experimental Setup

A baseline CNN configuration was first established before performing controlled experiments.

Baseline Configuration:
* Learning Rate = 0.001
* Batch Size = 16
* Dropout Rate = 0.0
* Optimizer = Adam
* Epochs = 20

After obtaining baseline results, experiments were performed by modifying one parameter at a time while keeping all other settings unchanged.

The experiments included:
* Learning Rate Analysis
* Batch Size Analysis
* Dropout Regularization Analysis
* Failed Training Run Analysis

For every experiment, training loss, validation loss, training accuracy and validation accuracy were recorded and compared. This experiment helped observe how individual hyperparameters influence neural network training behaviour.

## 5. Learning Rate Experiments

* Learning Rates Tested: 0.0001, 0.001 (Baseline), 0.01, 0.5 (Failed Run).
* Converging rate: 0.0001-Slowest, 0.001-Fastest, 0.01-initially reduced training loss extremely, its optimization behaviour was less stable and produced poorer validation performance.
This experiment answered a lot of questions and confusions i had. Some are:
* Most stable learning rate? 0.001. Optimizer was able to make meaningful progress toward lower loss values, avoiding excessively large updates.
* Which learning rate was unstable and why? 0.5. Because, Instead of gradually moving toward a minimum in the loss landscape, the optimizer repeatedly overshoots the optimal region. Hence, loss values fluctuate. This is often referred to as overshooting during gradient descent.
* Why did higher learning rates appear to learn faster initially? Larger learning rates move weights more. This can produce rapid decreases in loss during the early stages of training. However, excessively large updates may prevent the optimizer from accurately locating the minima, reducing stability and potentially harming generalization.

## 6. Batch Size Experiments

Batch Sizes Tested: 8, 16 (Baseline), 32
Batch size is the number of training samples processed before the optimizer updates the model weights. Instead of updating the network after every individual image, multiple images are grouped into a batch. The loss and gradients are computed using the entire batch before a weight update is performed.

Some doubts: 
* Why are larger batch sizes faster? Larger batch sizes process more images simultaneously during each training step.
* Why do smaller batches often generalize better? Smaller batches produce noisier gradient estimates. Computed gradient is slightly different every time. This noise can help the optimizer avoid memorizing the training dataset.
* Why does batch size affect optimization? Gradient descent relies on gradients calculated from training data. When batch size changes, the quality of the gradient estimate changes.

## 7. Dropout Experiments

Dropout Rates Tested: 0.0 (Baseline), 0.4
Dropout is a regularization technique used to reduce overfitting in neural networks.

Some doubts: 
* Why does training accuracy often decrease when dropout is used? Dropout intentionally makes the learning problem more difficult. Since a fraction of neurons are randomly disabled during training, the network cannot rely on the same ways every time.
* Did dropout completely solve overfitting in this project? Apparently No. Because dropout can reduce memorization, but it cannot fully compensate for insufficient training data.

## 8. Optimizer Experiments

Optimizers Studied: Adam (Adaptive Moment Estimation), Stochastic Gradient Descent (SGD)
An optimizer is the component responsible for updating the neural network's weights during training. After forward propagation computes predictions and the loss function measures error, backpropagation calculates gradients for each weight. The optimizer then uses these gradients to determine how the weights should be updated in order to reduce loss. Without an optimizer, a neural network would not be able to learn from its mistakes.

Some questions: 
* Why does Adam usually converge faster? Adam combines two important ideas: Momentum, Adaptive Learning Rates. Instead of reacting only to the current gradient, Adam accumulates information from past updates.
* Does faster convergence always mean a better model? No. An optimizer that reaches low training loss quickly does not automatically produce the best generalization performance.
* What are the tradeoffs between Adam and SGD?
Adam:
Advantages:
  * Faster convergence
  * More stable training
  * Less manual tuning
Disadvantages:
  * Higher memory usage
  * May sometimes generalize worse

SGD:
Advantages:
  * Simpler algorithm
  * Lower memory requirements
  * Strong generalization in some tasks
Disadvantages:
  * Slower convergence
  * More sensitive to learning rate selection

## 9. Failed Experiment

Failed Configuration: Learning Rate = 0.5, Batch Size = 16, Dropout = 0.0, Optimizer = Adam

Some doubts: 
* Why did the experiment fail? When the learning rate becomes too large, the optimizer takes excessively large steps through the loss landscape. Rather than gradually approaching a minimum, the optimizer repeatedly overshoots good solutions. Hence, the model cannot settle into a stable region of low loss.

## 10. Learnings 
These are some concepts I was able to cover so far: 

ERM, Learning Rate, Overfitting, RAG and it's pipeline, Vector databases, Embeddings (This was my favorite cause it made the most sense of how AI is trained), Transformers and their working pipeline (Attention confused me initially), Inference engine (Like llama.cpp), ROS, Autoencoders, Segmentation, Forward Propagation, Loss Functions, Backpropagation, Gradient Descent, Optimizers, Overfitting, Underfitting, Validation Set, Regularization, Dropout, Batch Normalization, Feature Extraction


## Dataset Access

The dataset used for this project consists of custom images collected (by me) for three classes: Bottle, Watch, Scissors. 
Due to GitHub file size limitations, the complete dataset has been hosted separately.

Dataset Link:
[https://drive.google.com/drive/folders/1_VnlwvR9OmPkxskU58LuUc6yul-sk31I?usp=sharing]

