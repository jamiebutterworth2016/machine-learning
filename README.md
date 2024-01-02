# Machine learning (ML)
This guide is split into theory and practical. The theory is required to carry out the practical.\
If you already know enough theory, you can [skip to practical.](/practical/practical.md)


## About
ML is a subset of AI, a subset of data science, a subset of computer science.\
ML is self-learning - not explicitly programmed.\
It finds patterns in data. We have all this data. Let's make use of it!

## Semi-supervised learning
Algorithms are split into categories: unsupervised learning and supervised learning.\
Practially, unsupervised learning is required first before supervised learning can be applied.\
Tables don't usually start with a classification column, i.e. rows aren't usually classified.
1. First use an unsupervised learning model to categorise data into groups (ideally two groups for simplicity) and generate a classification column.
2. Then use a supervised learning model to:
    - Read the values of a new data row.
    - Compare the row with existing rows in each group.
    - Place the row into the group with the most similar values.

E.g. Is this animal more like a dog or a cat? It's more like a cat so place it in the cat group.

## The three self-learning categories
|                       | Known Input | Known Output |                                                                                                                                                                                                                                    |
| --------------------- | ----------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unsupervised learning | Y           |              | The model splits data into groups.<br/>[About unsupervised learning.](unsupervised-learning.md)                                                                                  |
| Supervised learning   | Y           | Y            | Feed existing input and output pairs into the model so it learns the patterns between the pairs.<br/>The model uses this learnt pattern to read new inputs and predict their corresponding outputs.<br/>[About supervised learning.](supervised-learning.md)                                                     |
| Reinforced learning   |             | Y            | The opposite of unsupervised learning as only outputs are known, not inputs. Random input (e.g. random chess moves) is fed into the model and graded until the known output is achieved (e.g. win a game of chess). desired output |

<br/><br/>

[The theory behind building a model](build-model-theory.md)


# 11. Accurate predictions

We test different algorithms and tweak their parameters until we find the one which produces the most accurate predictions.

![hyperparameters](/images/hyperparameters.png "hyperparameters")

<br/>

## Bias and variance
- Bias and variance contribute to error (inaccuracy).
- We want low bias - predictions near to the target.
- We want low variance - predictions which are close together.

![bias-and-variance](/images/bias-and-variance.png "bias and variance")

<br/>

## Balancing Bias and Variance
- Initially the model is simple and predictions are inaccurate (high bias) but close together (low variance).

![high-bias-low-variance](/images/high-bias-low-variance.png "high bias low variance")

- Bias and variance is a trade-off and we're looking for the perfect balance between the two.
- To increase accuracy (lower bias), we **increase the model's complexity**.
- Predictions are now slightly more scattered (mid variance) but also increasingly more accurate (mid bias). This is the perfect balance.

![mid-bias-mid-variance](/images/mid-bias-mid-variance.png "mid bias mid variance")

![model-complexity](/images/model-complexity.png "model complexity")


If we increase the complexity too much, this results in accurate predictions using training data but not test data (overfitting).

If we don't increase complexity at all, both training and test data results in inaccurate predictions (underfitting).

![model-complexity-2](/images/model-complexity-2.png "model complexity 2")


</br>

# 13. Neural Networks
[Neural networks](neural-networks.md)

# 14. Decision trees
[Decision trees](decision-trees.md)

# Practical
[Practical](practical.md)
