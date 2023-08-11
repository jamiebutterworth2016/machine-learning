# Neural networks
- ML technique.
- Node = decision function
- A network of nodes is divided into an input layer, hidden layer (can be multiple) and an output layer.
- Input layer - receives input data - numbers, strings, image pixels, sound etc.
- Hidden layer - Analyses and processes the inputs. Hidden from humans. More hidden layers = network can analyse more complex patterns. Deep number of layers = *deep learning*.
- Output layer - Shows the prediction.
- Each node forwards data to the next layer of nodes via an edge.

![network layers](/images/network-layers.png "network layers")

## Edges
- An edge is a gateway to next the node.
- Each edge has a unique numeric weight.
- The weight can change with experience.

### The sum of the connected edges is calculated.
- If the sum satisfies a set threshold, the activation function forwards the data to the next node.
- If the sum does fails to satisfy the threshold, the activation fails. *Does this mean the network does not forward the data to the next node?*

# ANN in Supervised learning
- Train the model by tweaking the weights.
- Find the **cost** by comparing the difference between the predicted output and expected output.
- We want the cost to be as near to zero as possible.
- This training technique is called *back-propagation*.
- Back-propagation navigates from right to left - from the output layer to the input layer.

# Blackbox dilemma
- The network model is unable to specify the relationship between inputs and output.
- Decision trees and linear regression are better algorithms in showing the relationship between inputs and output.
- *More info needed - maybe an image?*
- Networks aren't good at showing their workings.
- Neural networks are good for when you need a fast prediction without caring too much about how they came to their prediction.

<br/>

# Building a network


## Perceptron
- A basic *feed-forward network*.
- Simplest way to assemble the nodes of the network.
- Data flows from input to output in one direction - no loops.
- Receive inputs -> binary output of 1 or 0.
- 1 triggers the activation function -> forwards output to next layer.
- 0 does not trigger the function.

![perceptron](/images/perceptron.png "perceptron")

### Perceptron in supervised learning
1. Feed inputs into processor.
2. Apply weights to estimate value of inputs.
    Multiply input with weight.
```
x1: 24
x2: 16

x1 weight: 0.5
x2 weight: -1

x1: 24 * 0.5 = 12
x2: 16 * -1 = -16
```

![perceptron supervised learning](/images/networks/perceptron-supervised-learning.png "perceptron supervised learning")

- The activation function can be configured.
- Can set the function to >= 0.
- If the sum is >= 0, the output is 1, else 0.
  
  ![activation function](/images/networks/activation-function.png "activation function")

  ```
  Input 1: 24 * 0.5 = 12
  Input 2: 16 * -1 = -16
  Sum (∑): 12 + -16 = -4
  Output: 0
  ```

- As the result is 0, the function is not triggered.
- If the function is not triggered, we need to adjust the weight or the function.
- Adjusting the weight:
  ```
  Input 1: 24 * 0.5 = 12
  Input 2: 16 * -0.5 = -8 <--
  Sum (∑): 12 + -8 = 4
  Output: 1
  ```

- Adjusting the function:
  ```
  if x > 3 then y = 1
  if x <= 3 then y = 0
  ```

- As the result is now 1, the function is triggered and the output is forwarded to the next layer.


  ![activation function 2](/images/networks/activation-function-2.png "activation function 2")


### Sigmoid neuron
- More flexible than perceptron.
- Outputs a value between 0 and 1, e.g. 0.5.
- Weight changes have less of an undesired knock on effect on outputs.
- Hyperbolic tangent functions are even more flexible because they output a value between -1 and 1, e.g. -0.5. 

## Multilayer perceptrons (MLP)

  ## Deep learning