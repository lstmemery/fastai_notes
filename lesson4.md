# Lesson 4

## CNN Review

- It's just an element-wise multiply
- "It's hard to believe that's all there is!"
- Max pooling helps with translational invariance

## SGD
- happens for all layers at once
- everything we learn about fitting a line also applies to CNNs
- Finite differencing: Add a small amount each parameter
- Multiply the derivative by the learning rate
- ReLU needs subgradients
- Your learning rate is too high, things will actually get worse
- This similar to exploding gradient
- The majority of space in a neural net is a saddle point
- The loss tends to bounce around but in a constant direction, we can use momentum to push it down further.
- Back propagation work because of the chain rule

## Momentum
- Add the average of the next few steps
- Momentum rate is a hyperparameter

## Dynamic Learning Rates
- Different parameters learn at different speeds
- Adagrad, for example
- We care about the difference between the gradient and the previous gradient
- Square of the gradient
41:19

## RMSProp
- Jeff Hinton in Coursera
- Weighted running average of the squared gradients
- Otherwise the same as Adagrad
- Doesn't explode!
- **If you see your validation score flatline with RMSprop, divide your learning rate by 10**
- Learning rate annealing (learning rate gets smaller over time)

## ADAM
- RMSprop + momentum
- Seems to do really well
- He makes a version with automatic annealing that looks very nice

## Eve
- Automatic learning rate annealing + ADAM
- Ratio of the loss function and the previous loss function
- Exponential moving average of kiss functions ratios
- Not many citations (too new?)
- Can both increase and decrease the learning rate
- Not sure if this is ready for prime time

## Early Stopping (Aside)
- It's really hard to find the optimal stopping point

## State Farm Distracted Driver Detection
- Can do batch normalization on the first layer!
- Many people training just got the same class over and over again (Learning rate too high)
- First epoch should have a low learning rate
- Samples good for checking learning rates
- Tried every data augmentation (seperately)
- To figure out regularization, we need to the full dataset, though
- Don't forget clipping
- Rule of thumb 0.5 Dropout on the dense layers
- pre-computed features from ImageNet
- could save the augmented images

## Pseudo-labelling & Knowledge Distillation
- Use the structure of the test set to inform your training
- Train on the predicted features of a weaker model
- Mentions spearmint: Bayesian hyperparameter optimization
- WE ARE NOT USING THE VALIDATION LABELS
- Pseudo-labeling is an iterative process
- A quarter to a third of the minibatches should be pseudolabels
- Errors could propagate through
- Takes advantage of large amounts of unlabeled data

## Collaborative Filtering
- Who is going to like what?
- Netflix, Amazon
- Find out what people like you like
- MovieLens competition
- Using pandas crosstab
- Using gradient descent in Excel (called solver)
- We also need biases for popular movies and people who rate highly
- We are calculating "latent factors"
- How do you look up a user's latent factors from their latent factors
- Set the missing value losses to 0

## Embedding
- A type of layer in keras
- We are no longer using sequential
- you can do collaborative filtering in Keras!
- Concatenate the feature embedding
- Simple neural net architecture beats the state-of-the-art!
