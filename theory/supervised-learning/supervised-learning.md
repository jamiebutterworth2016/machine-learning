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
| [k-nearest neighbours (k-NN)](/theory/supervised-learning/k-nearest-neighbors.md))   | Classification           |
| [Support vector machines (SVM)](/theory/supervised-learning/support-vector-machines.md)) | Classification           |
| [Decision trees](/theory/supervised-learning/decision-trees.md)                |                          |
| [Neural networks](/theory/supervised-learning/neural-networks.md)               |                          |

<br/>

## 3. k-nearest neighbours (k-NN)
- Classification technique.
- Classifies new points relative to how near they are to existing points.
- k is the number of existing points we use to determine which class a new point belongs to.
- k must be an uneven number.
  
1. I set k to 3.
2. A new point is placed on the graph.
3. I find the new point's 3 nearest neighbouring points.
4. I note the class of each neighbouring point.
5. The new point belongs to the class with the most neighbouring points. E.g. 1 neighbouring point belongs to class A. 2 neighbouring points belong to class B. The new point belongs to class B.

![k-nearest neighbours](/images/k-nearest%20neighbours.PNG "k-nearest neighbours")

- Test different k combinations to find the best fit.
- Setting k too low results in misclassification.
- Setting k is too high is computationally expensive - calculating the distance between a new point and all existing points is expensive.
- Setting k to an uneven number eliminates the possibility of a stalemate.
- 5 is the default when using Scikit-learn.
- k-NN is not recommended for large datasets.

<br/>

## 4. Support Vector Machines (SVM)
- Classification technique.
- Similar to logistic regression - both techniques use a line to separate the points but positions the line differently.
- Logistic regression **minimises** the distance between all points and the line.
- SVM **maximises** the distance (margin) between all points and the line.

![svm-vs-logistic](/images/svm.PNG "svm vs logistic")
