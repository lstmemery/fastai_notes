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

50:55
## Sequential RNN

## Stateful RNN

## Stateful RNN Example

## RNN in Theano

