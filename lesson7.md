# Lesson 7

 - only CNNs right now
 - include_top=False (no need for popping off top layer)
 - Precomputing everything
 - All shapes are activations
 - Arrows are layer operations

## Resnet
- Won 2015 Competition
- Includes local average pooling layer
- Very accurate
- Adds information in (through identity)
- That's a resnet block


Why is this so good?
1. Allows for deeper networks
2. It's optimizing the residual (difference between model and actual)

This is like boosting
Dimensionality remains constant
Hasn't been well studied for transfer learning
Activations can't really be visualized 

## Global average pooling
- Across each filter, what is the average?
- ResNet was training wuth GlobalAveragePooling, so it's learned the best results
- Does not need as much Dropout because of no dense layer

## Fisheries Competition
- A dozen boats (day and night)
- One or more fish (small in the image)
- Tried VGG
- added a few dense layers

## Data Leakage
KDD best paper: [https://www.cs.umb.edu/~ding/history/470_670_fall_2011/papers/cs670_Tran_PreferredPaper_LeakingInDataMining.pdf](Leakage in Data Mining)
(Might be worth submitting) 
Different boats = different oceans = a very good feature
Different resolutions = different boats
It's legal in Kaggle
Merge in image size (one hot encoded) Then dense
The multiinput is not better
This means that leakage was not actually helpful
Kaggle tries to prevent this through stratified sampling etc.

### Different sized images

- resizing to 224x224
- resnet resizes to 400x400

## Multioutput and Bounding Boxes
- Someone has annotated the fisheries dataset
- Made a little function to see the bounding box
- We don't have bounding boxes for the test set
- Make a network that finds the bounding boxes
- 4 linear outputs (bounding box)
- Have to scale the loss
- Network has to find the bounding box AND label the fish at the same time
- We get a much better accuracy (We gave the network a hint where to look)
- You could do this sequentially (Right Whale Competition)
- Tenacity is very important for winning Kaggle competitions
- Try an hour a day

Didn't cover more data augmentation

## Fully Convolutional Networks (FCNs)
- Would allow for multiple sizes (convolutional layer doesn't care about dimensions)
- Don't include the fully connected blocks
- REMEMBER: matrices are rows by columns, images are columns by rows
- Conv-BatchNorm-MaxPool blocks then Dropout-> GlobalAveragePooling
- last conv layer has 8 filters (for the 8 fish)
- 22nd place with no psuedolabeling or data augmentation
- Why?
1. It works well
2. Generalizes well
3. Nice to visualize
Very cool heatmap option
This is not an attention model
Could check attention vs bounding box
How to align the head and tail (hand annotation)
Hand labeling brings errors

## InceptionNet
- Inception + ResNet won last year's Imagenet
- Use multiple filter sizes and concatenate them together
- Keras has Inception (has not been well studied)
- Inception uses concat instead of add merges

# RNNs Revisited
- Speech translation
- time series of click events etc.
- Attentional models

## Pure Python RNNs
- he clips the cross entropies
- Scan gets the next element of the sequence plus the result of the current
- Do the forward pass (just a scan with the matrix multiplication)
- Then do the derivatives in the opposite direction
- derivative of softmax
- derivative of matrix multiplication is the matrix and transpose
- "undo" the activation function
- Create the weight matrices (Glorot initialization)

## Gated Recurrent Units (GRUs)
- Simpler and better
- Prevents exploding gradients
- hidden state with gates (mini-neural network)
- reset gate causes forgetting (it can learn when to forget)
- update gate determines whether to take the hidden state or the new hidden state
- Gates use sigmoid activation (one layer neural net)
- learns when to throw away and forget states