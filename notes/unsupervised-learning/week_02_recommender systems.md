# Week 02 - Collaborative Filtering - Recommender System
An introduction to **Unsupervised Learning** via the **Collaborative Filtering** algorithm.


## Introduction
As the name suggests, Recommender Systems make recommendations to users based on their preferences (ratings, purchases, likes, etc.). Collaborative Filtering is a technique to predict user's preferences by analzying the behaviour of similar users.

Recommender systems use datasets made up of:
- **Users' behaviours**: likes, ratings, clicks, etc.
- **Items' features**



## Algorithm
* **LINEAR REGRESSION**
$$
\begin{matrix} &\textbf{min}& \\w^{1}, & ... & w^{(n_u)}\\b^{1}, & ... & b^{(n_u)}\\x^{1}, & ... & x^{(n_m)} \end{matrix} \frac{1}{2}\sum_{(i, j):r(i, j) = 1}(w^{(j)}\cdot x^{(i)}+b^{(j)}-y^{(i, j)})^2 + \frac{\lambda}{2}\sum_{j=1}^{n_u}\sum_{k=1}^{n}(w_{j}^{(i)})^2+\frac{\lambda}{2}\sum_{i=1}^{n_m}\sum_{k=1}^{n}(x_{k}^{(i)})^2
$$

Where:
- $\( n_u \)$ : number of users
- $\( n_m \)$ : number of items
- $\( \vec{w} \)$ : ($\n_u\$, n) vector of *n* weights for each user
- $\( \vec{b} \)$ : (1, $\n_u\$) vector of *n* weights for each user
- $\( \vec{x} \)$ : ($\n_m\$, m) vector of *m* features for each item
- $\( y^{(i, j)} \)$: true label for item *i* and user *j*
- $\( r^{(i, j)} \)$: presence of value for item *i* and user *j*: 1 is user has performed that operation, 0 if not


* **BINARY CLASSIFICATION**

For a classification problem we will need to use the Binary Crossentropy. Having a function:
$$y^{(i, j)} = f_{(w, b, x)} (x) = g(w^{(j)} \cdot x^{(i)} + b^{(i, j)})$$
And a Loss function:
$$L(f_{w,b,x}(x), y^{(i, j)}) = -y^{(i, j)}log(f_{w,b,x}(x)) - (1 - y^{(i,j)})log(1 - f_{w,b,x}(x))$$

The Cost function is:
$$J = \sum_{(i, j):r(i, j) = 1}L(f_{w,b,x}(x), y^{(i, j)})$$

### Mean Normalization
When there are users who have not voted anything yet or new items that haven't received any ratings, if we were to apply those algorithms as is they would receive a rating value equal to 0 (zero).
To avoid that, we need to normalize our data:
1. Calculate **mean** $(\mu)\$ for each item
2. Subtract the mean $(\mu)\$ from EACH user's rating related to that item. **Note** if a user hasn't rated the item yet, the value will be (0-$\mu\$ = -$\mu\$) negative mean
3. Apply our algorithms
4. **Sum** each mean $(\mu)\$ back again to avoid negative ratings

## Finding Related Items
Once you trained your model to show what items my interest a user or not we can apply one of a few technique:
* Cosine Similarity
* Nearest Neighbors
* Pearson/Spearman correlation

**COSINE SIMILARITY**

Compute cosine similarity between the item vectors in the learned latent space. This gives a measure of how similar two items are in terms of their latent features.
$$\cos(\theta) = \frac{v_i\cdot v_j}{\|v_i\|\|v_j\|}$$

Where:

$v_i$, $v_j$ = latent vectors of items *i* and *j*

**NEAREST NEIGHBORS**
Find the nearest neighboring items related to another one.
1. Find the square distance between the item we are trying to find values for and the other items
$$\sum_{l = 1}^{n}(x_{l}^{(k)} - x_{l}^{(i)})^2$$
2. Find the minimum distance in that vector

## Limitations
- **Cold Start Problem**: the algorithm is not very accurate when we have new items that not many users have rated or when we have new users that haven't rated many items yet
- **Information usage**: the algorithm does not have a good way to use useful user's information such as demographics


```python

```
