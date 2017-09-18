# Cats vs Dogs

- Ensembled
- Data augmentation
- Not using pseudolabeling

# BatchNorm on a Pretrained Model

- Added to VGG (didn't exist before) 
- Remember BatchNorm is faster and reduces overfitting
- You could also get higher learning rates
- Remember: two new weights added for stability
- Now finetune = See an improvement
- Could also add this to the convolutional layers

# Collaborative Filtering

- Each row is a single user reviewing a single movie
- Turned into a crosstab
- Can add on bias
- In collaborative filtering, the embeddings are known as "Latent Factors"
- Increasing regularization was very effective (takes longer to train, though)

## Analyzing Results

- Grab the top 2000 movies based on biases
- You can see the "best" and "worst" movies

-What's going on in the latent factors
- Do a PCA on the latent factors
- First factor: overall rating
- 2nd: Budget
- 3rd Violence/Scariness

More latent factors = more accurate model

latent factors are not necessarily instructable
Visualizations are very important

# Keras Functional API

- What is you can't express as a sequence?
- Use the function layer
- Looks like currying?
- Then use `merge` (not the same as `Merge`)
- Pass in an array in the functional fit method

# NLP

- Example: IMDb sentiment analysis (Stanford)
- He imports it directly
- 25000 reviews
- Every word is an integer (ordered by use)
- Also provide sentiment

- Truncate only the top 5000 words
- Need to truncate review length as well
- Pad the sort reviews
- Can do both at the same time with `sequence.pad_sequence`
- It's padded at the front

# Single Hidden Layer Model

- Simplest possible model
- Start with an embedding
- Using sigmoid activation (single dimension)
- Embedding returns a vector from an ID (one hot encoding followed by a matrix product)
- This is not bag of words

# CNN Model

- CNNs are great for ordered data
- 1D convolution
- Accuracy improved over benchmark
- Embeddings are not words. They are vectors
- We are "learning" these vectors
- They start randomly
- Can dropout embeddings

# Pre-Trained Word Embedding

- Can pass around embeddings (word vectors) instead of networks
- Glove (Global Vectors for Word Representation)
- word2vec (from Google) (Good tensorflow info)
- Sometimes things are cased, sometimes not
- These embeddings are unsupervised
	- Try to determine if a sentence with a replaced word is real or not
- Find the nearest word vector in a different language to translate

- TSNE dimensionality reduction
- The 2D is a big simplification
- Exploring the Limits of Language Modeling
- CNNS with pre-trained word embeddings are state of the art

# Using Glove for Sentiment Analysis

- Always you pre-trained word embeddings
- Convert IMDb index into glove index
- Another improvement

# Multi-size CNNs

- Quid uses deep learning with small data
- Identify marketing phrases
- **Merge multiple size of convolutions**
- ANOTHER improvement

# Recurrent Neural Networks

Why we Need RNNs
  - variable length sequence
  - long-term dependency
  - stateful representation
  - memory

Multiple Object Recognition with Visual Attention
- Where do I look next?

SwiftKey uses RNNs

Add Word 2 into the second layer etc.
RNN is aware of state
Can we do a layer operation on itself? Yes
All hidden-to-hidden matrices are the same

# RNN Example