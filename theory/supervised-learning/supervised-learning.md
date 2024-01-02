# Supervised learning
Supports both numeric predictions and classification.\
Classification appears to be the most useful.

Both inputs and output are known.

1. I take the output.
2. I take the inputs which created the output.
3. I discover the relationship between the inputs and the output.
4. I use this relationship to predict the output of future inputs.

| Algorithm                     | Used for                 |
| ----------------------------- | ------------------------ |
| [Linear regression](/theory/supervised-learning/linear-regression.md)             | Numeric predictions      |
| [Logistic regression](/theory/supervised-learning/logistic-regression.md)           | Classification           |
| [k-nearest neighbours (k-NN)](/theory/supervised-learning/k-nearest-neighbors.md)   | Classification           |
| [Support vector machines (SVM)](/theory/supervised-learning/support-vector-machines.md) | Classification           |
| [Decision trees](/theory/supervised-learning/decision-trees.md)                |                          |
| [Neural networks](/theory/supervised-learning/neural-networks.md)               |                          |

<br/>



## 4. Support Vector Machines (SVM)
- Classification technique.
- Similar to logistic regression - both techniques use a line to separate the points but positions the line differently.
- Logistic regression **minimises** the distance between all points and the line.
- SVM **maximises** the distance (margin) between all points and the line.

![svm-vs-logistic](/images/svm.PNG "svm vs logistic")
