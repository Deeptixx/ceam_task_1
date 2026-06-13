### CNN FOR OBJECT CLASSIFICATION
## WHAT I BUILT:
A custom convolutional neural network to classify 5 objects(book, phone,calculator,clock and headphones) from a dataset of 125 custom images. 
# Baseline Model
- Model Architecture - Custom CNN with:
  - 4 conv layers with ReLU activation
  - 3 MaxPooling2D layers
  - 1 GlobalAveragePooling Layer
  - Softmax output (5 classes)
- Optimizer: Adam
- Learning Rate: 0.001
- Batch Size: 8
- Epochs: 50
# Baseline Results:
- Train, Val, Test Accuracy were 82.76% , 78.95% , 78.95% respectively. 
- Overfitting gap was 3.8% which shows mild overfitting (small dataset)
## Experiments Performed
# Optimizers Tested:
- SGD Test Accuracy: 15.79%
- RMSprop Test Accuracy: 73.68%
- Adam Test Accuracy: 73.68% (78.95% in baseline model but because of random initialization the model trained with different initial weights so there is a little variance)
- AdaGrad Test Accuracy: 15.79%

**What changed and why?**
- Adaptive Optimizers adjust learnig rates for each parameter that is they are momentum based so Adam and RMSprop perform relatively well compared to non adaptive ones that update weights step wise.
 
# Learning Rate:
- Adam (lr=0.0001): Test Accuracy = 52.63%
- Adam (lr=0.0005): Test Accuracy = 68.42%
- Adam (lr=0.001): Test Accuracy = 84.21% (again variance because of random initialization - no fixed initial weights)
- Adam (lr=0.005): Test Accuracy = 57.89%
- Adam (lr=0.01): Test Accuracy = 15.79%

**What changed and why?**
- Best learning rate was 0.001 ( higher than baseline beacuse of luck but still performed better than the others)
- Plot was an inverted U curve which means that if the learning rate was too low then the model learned slowly and if it was too high there was instability

# Learn rate scheduling:
- Step Decay: 47.37%
- ReduceLROnPlateau: 57.89%
- Cosine Decay: 73.68%

**What changed and why?**
- All scheduling underperformed on this dataset. Scheduling is designed for long training (100 or more epochs). On 50 epoch with 125 images fixed LR works well.
( Need for lomger training, early drops, extra parameters that drop differently are some of the reasons this happens on small datasets)

# Batch Size:
- 8: 78.95% (Baseline)
- 16: 73.68%
- 32: 68.42% 
- 64: 63.16%

**What changed and why?**
- This demonstrates that smaller batches mean better accuracy. Smaller batches means more gradients per epoch which in turn means faster learning. 

# Regularization (Dropout):
- 0.3: 78.95%
- 0.5: 78.95%
- 0.7: 84.21%
 
 **What changed and why?**
 - Dropout rates of 0.3 and 0.5 were optimal but 0.7 won which is weird and interesting because a dropout rate of 0.7 means deactivation of 70% neurons.
 - Maybe model is overparameterized and more dropout means it forced the model to learn and generalize **better** instead of memorizing.


# L2 Regularization:
- 0.0001: 57.89%
- 0.001: 63.16%
- 0.01: 57.89%

**What changed and why?**
- L2 add penalty : loss=loss+L2_weight*sum(weight)^2
- L2 forces weights toward zero during training and it prevents weights from getting large
- L2 adds constraints on model capacity and train test gap in baseline was only 3.8% and L2 tackles overfitting.

## Key Insights:
- I learnt that optimizer choice is really important and adaptive optimizers for small datasets are good.
- I also learnt that learning rates are optimal and that batch sizes are important because on small datasets batch size noise acts like regularization
- I found out that scheduling works on large datasets only
- L2 tackles overfitting








