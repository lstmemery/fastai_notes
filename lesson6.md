# Pseudo Labeling: MixIterator
- Mix in unlabeled data (add in pseudobatches)
- Can use the validation set as well (right at the end)

# Embeddings

- It's just a lookup
- Take the product of the two vectors (user and movie)
- Word embeddings work exactly the same way
- The size of embeddings will affect accuracy (related to the complexity of the corpus)
- Read the [word2vec paper](https://arxiv.org/abs/1301.3781)
- Read: [Designing Great Data Products](https://www.oreilly.com/ideas/drivetrain-approach-data-products)


# RNNs

- Needs Stateful Representation
- Recall all hidden-to-hidden transitions use the same matrix
- Same for input-to-hidden

## 3 Char Model
- Convert characters into IDs
- Predict the fourth character from the first 3
- Create a character-wise embedding (Not normally done)
- Chose 256
- Dense layers used
- Merge the layers together with the functional API
- This model can only look 3 characters behind
- Unrolled form

## Nth Char Model

- Tensorflow automatically unrolls RNNs
- Jeremy hasn't seen any architectures that mix activation functions (except for at the output)
- Init="identity" hidden-to-hidden transistion
- Hinton suggests this
[A Simple Way to Initialize Recurrent Recurrent Networks of Rectified Linear Units](https://arxiv.org/abs/1504.00941)
- What if the output is also recurrent? Then we could make a sequence of any length
- We want to learn on every character
- Long term dependecies are like context

## Sequential RNN

- character_out is shifted input by one
- Initialize hidden state with 0ss
- Append the output for each step
- Now we have multiple losses
- The first character loss will always be bad (how to predict when there's no information)
- *Does the RNN learn what the most probable first character is?*

### In Keras

`return_sequences=True`

## Stateful RNN

- How do we handle long term dependencies?
- First, we need to stop shuffling the input?
- Keep the Hidden state as it was before
in Keras: `stateful=True, shuffle=False`
- Harder to train (the hidden matrix is being used hundred of thousands of times)
- Any imbalance in the matrix will destroy the model
- This is the exploding gradients problem
- Originally thought to be impossible to train before LSTMs
- Much harder to parallelize
- Better loss though

## Stateful RNN Example

- RNN feeds into an RNN
- Stacked RNN (Operates consequentively)
- Makes a more flexible function
- Dropout is great in an RNN
- `TimeDistributed` because a normal dense layer is only one dimension
- When you have `return_sequences`=True, try TimeDistributed
1:19:16
## RNN in Theano

