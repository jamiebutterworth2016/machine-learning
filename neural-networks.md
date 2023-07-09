# Neural networks
- ML technique.
- Network-based model.
- Network of decision layers - *decision trees?*

<br/>

# Network makeup
- Node = decision function
- Edge = gateway to next node
- Nodes are separated into layers, starting with a wide base.
- First layer = input data - numbers, strings, image pixels, sound etc.

![neural network layers](/images/ann-layers.png "neural network layers")

- Each node forwards data to the next layer of nodes via an edge.

![neural network](/images/ann-network.png "neural network")

## Edges
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
## Layers
- A network is divided into an input layer, hidden layer and output layer.
- Hidden layer - Analyses and processes the inputs. Hidden from humans. More hidden layers = network can analyse more complex patterns. Deep number of layers = *deep learning*.
- Output layer - Shows the prediction.

![network layers](/images/network-layers.png "network layers")

## Perceptron - a feed-forward network
- *Feed-forward network* is the simplest method to assemble the nodes of the network. Data flows from input to output in one direction - no loops.
- Perceptron is the most basic feed-forward network.
- Receive inputs -> binary output.
- Output can be 0 or 1.
- 1 = trigger activation function -> forward output to next layer.
- 0 = do not trigger, do not forward.

![perceptron](/images/perceptron.png "perceptron")

### Perceptron in supervised learning
1. Feed inputs into processor.
```
Input 1: x1 = 24
Input 2: x2 = 16
```

2. Apply weights to estimate value of inputs.
```
Input 1: 0.5
Input 2: -1
```

![perceptron supervised learning](/images/networks/perceptron-supervised-learning.png "perceptron supervised learning")

3. Calculate cost (different between estimate and actual values). Multiply input with weight.

```
Input 1: 24 * 0.5 = 12
Input 2: 16 * -1 = -16
```

4. Adjust weights to reduce cost.
5. Repeat until model is accurate.


