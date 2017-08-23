# Lesson 2

## Lecture

Covering homework
- `kg download`
- Create a todo list directly in the Jupyter Notebook
- `predict_generator` is a great keras method
- `from IPython.display import FileLink` Download your files!
- In Keras logloss is binary entropy

### Categorical Cross Entropy
- Use a spreadsheet
- Harshly punishes confidence
- To solve this `np.clip` (Smart!)
- Maybe match your clipping to your validation?
- Drop down learning rate

### Visualizing
- Take a look at the Jupyter Notebook with this
- Show what you got right, wrong and in are not sure about
- Probabilities that coming out of the network are not real probabilities
- The more epochs, the more confident the neural network will be
- `tree -d`
- Watch lecture 0


### Convolutional Networks
- Visualizing and Understanding Convolutional Networks by Matthew Zeiler (https://www.cs.nyu.edu/~fergus/papers/zeilerECCV2014.pdf)
- Gabor Filters are a natural analog
- Finetuning means taking all the complicated filters and combining them on your problem
- At least kernel layers will be useful
1:02:40
- Made a deep network in excel
- The number of columns only matters for the last layer
- You wants weight to be very similar
- Xavier initialization $\frac{2}{n_in * n_out}$
- Huge improvement

### Linear Model
- Need a loss function
- Sum of squared errors works
- Find the derivative
- multiply it by the learning rate
- this is gradient descent (calls it stochastic gradient descent!)
- Not really a local minimum!
- What if you don't know the derivative? Use symbolic differentiation
- Make a linear model whose input is the imagenet 1000 nodes
`bcolz` is a library for saving numpy arrays (https://www.youtube.com/watch?v=-lKV4zC1gss)
- onehot encoding needed by Keras (needed for matrix multiplication)
- RMSprop is tweak on SGD

### Finetuning
- Activation function
- The example was just linear
- With ReLU, you can approximate any function
- Pop off the last layer