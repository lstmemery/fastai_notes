# Lesson 3

## Notes on Notebooks
- Check the notebooks (actually write them)
- Type in the solutions from scratch
- You can put the completed notebooks side-by-side
- Visualizing and Understanding Convolutional Networks
- Deep Visualization Toolbox is also really cool
- Deeper layers are more concept level

## Convolutions
- matrix multiply small kernels over image
- shows edge detector
- What's the optimal way to design filters?
- Deep learning answers that question (with SGD)
- Going to talk about filter sizes
- http://neuralnetworksanddeeplearning.com/chap4.html
- Convulations are particularly good at finding patterns in images
- Flatten removes the dimensions
- VGG says: increasing number of convolutions
- `model.summary()` to see parameters
- Increase number of convolutions to compensate for the lost information in max pooling
- convolutions are position invariant
- sidenote: It would be difficult to identidy cartoons from imagenet (not in the training set)
- correlate and convolve are essentially the same
- smaller filters with more layers is better
- no standard on the number of layers
- resample down (RNNs have attentional models)
- the later on we get in the network, the more complicated the "functions" 

## Max Pooling
- Simplifies pixels
- Gradually simplifies
- Reduces resolution
- as max pooling increases, the convolutions deal with more general position (i.e. are eyes on a face side by side?)

## Activations
- ReLU
$$\max(0,x)$$
- Softmax (Final activation for one hot encoding)
$$\frac{\exp(x_i)}{\sum{\exp(x)}}$$
- One high number and one low number
- any network can learn. Some are fast than others
- A network could learn the same filters but that wouldn't be optimal

## Finetuning
- Original Imagenet architecture was close to cats and dogs
- Is not going to work with statefarm
- Throw out more layers
- He retrained the dense layers
- Do not set the weights randomly when retraining

## Training a Better Model
- your current model is either underfitting or overfitting
- Underfitting is when your model is too simple (training lower than validation)
- Overfitting is when your model is too complex (just learns the data)
- VGG underfitting because of dropout
- Dropout is when you random set some fraction of the activations to 0
- Dropout prevents underfitting
- Allows use to train complex models over a long time without overfitting
- He then removes the last dropout layer by making a new model
- Dense layers are very fast to train but take up lots of memory
- You can perform dropout after convolutional layers
- **Suggests increasing dropout strength over time**
- Don't apply dropout to the input layer

## Reducing Overfitting
1. Add more data
2. Use data augmentation
3. Use architectures that generalize well
4. Add regularization
	- Such as dropout (creates large ensembles)
	- also L1, L2 norm
5. Reduce architecture complexity

## Data Augmentation
 - Rotate
 - flip
 - zoom in and out
 - Add in the ImageDataGenerator in `get_batches`
 - validation set has no data augmentation
 - experiment! (these are hyperparameters)
 - We can't precompute convolutional features, so it will take long to train
 - Always do some form of data augmentation
 - color channel data augmentation
 
## Batch Norm
 - Always do this
 - subtract the mean from input
 - Naively subtracting the mean in activation will just cause SGD to try the same thing again
 - 10X Speedup
 - Reduces overfitting
 - Adds two trainable parameters, a multiply and add 
 - BatchNorm changes all of the weights!
 - Add axis=1 to Convolutional BatchNorm
 
## MNIST
- don't forget to expand dims
- onehot encoder numbers
- start learning rate small (to initialize), then high, then small to learn
- Ensembling (make multiple models and average their outputs)
- start by overfitting