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

## Max Pooling
- Simplifies pixels
- Gradually simplifies
- Reduces resolution
- as max pooling increases, the convolutions deal with more general position (i.e. are eyes on a face side by side?)

## Activations
- ReLU
$$\max(0,x)$$
- Softmax (Final activation for one hot encoding)
$$\frac{\exp{x_i}}{\sum{exp{x}}}$$
- One high number and one low number
- any network can learn. Some are fast than others
- A network could learn the same filters but that wouldn't be optimal

## Finetuning
- Original Imagenet architecture was close to cats and dogs
- Is not going to work with statefarm
- Throw out more layers

1:06:15
