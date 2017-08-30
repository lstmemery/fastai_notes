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
48:03
