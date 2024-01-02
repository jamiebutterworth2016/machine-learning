## k-nearest neighbours (k-NN)
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
