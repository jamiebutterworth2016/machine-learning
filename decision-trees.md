# Decision trees

- Decision trees are an alternative to networks.
- Networks require a lot of data, processing and their decisions are untraceable (black-box dilemma).
- Trees require less data, processing and their decisions are traceable so easier to explain.

## Class and regression trees
- There are two types of trees:
  - Class trees
  - Regression trees
- Both trees take numeric and categoric inputs.
- Class trees predict categoric outputs.
- Regression trees predict numeric outputs.

## Example of class tree
![class tree](/images/trees/class-tree.png "class tree")

## Example of regression tree
![regression tree](/images/trees/regression-tree.png "regression tree")

## Tree structure
- Keep the tree as small as possible.
- Start with a root node - the entry point.
- Leaves are decision points.
- The last leaf is the terminal node.
- Each layer splits the data into increasingly homogenous groups.
  
![tree nodes](/images/trees/tree-nodes.png "tree nodes")

### Choosing the root node
- Find the input which best splits data into the two homogenous groups.

![split data](/images/trees/input-a.png "split data")