# Week 01 - K-Means
An introduction to **Unsupervised Learning** via the **K-Means** algorithm.

## Introduction
- **Clustering** = a technique in unsupervised learning that groups up similar data examples together into **clusters**. Each cluster will have a cluster **Centroid** that will correspond to its geometric center.
- **K-Means** = an algorithm used for clustering. It will group up our unlabeled data into `K` clusters each with its own centroid. The process of clustering is made up of the following steps:
    - Randomly set `K` centroids
    - Loop through the data and compute the `Euclidian norm` (L2 Norm) to find the distance between that data point and each centroid.
    - The centroid that will hold the minimum distance between itself and the data point will become the centroid for that specific data point. We then created K different clusters.
    - Find the centers of the newly created clusters and set them as the new centroids.
    - Repeat the steps above until convergence -> centroids not changing anymore.

## Algorithm
$$
J = \sum_{i=1}^{k} \sum_{x \in C_i} \| x - \mu_i \|^2
$$
Where:
- \( k \): number of clusters
- \( C_i \): set of data points assigned to cluster *i*
- \( mu_i \): centroid (mean) of cluster *i*
- \( \| x - \mu_i \|^2 \): squared Euclidean distance between point *x* and its centroid

### Steps
1. **Initialize Centroids**: Choose randomly \( k \) initial centroids \( \mu_1, \mu_2, \dots, \mu_k \)
2. **Assign Points to Centroids**: For each data point \( x_j \) assign it to its closest centroid:
   $$
   c_j = \arg\min_i \| x_j - \mu_i \|^2
   $$
3. **Update Centroids**:
   Calculate each centroid again as the mean of its assigned points within each cluster.
   $$
   \mu_i = \frac{1}{|C_i|} \sum_{x_j \in C_i} x_j
   $$
4. **Repeat Steps 2-3 until Convergence**: Convergence happens when Centroids **don't update** anymore or if their improvement is **minimal**

### Notes:
- K-Means also work if groups aren't well defined
- Oftentime there is no right answer on what value of K to pick. However we need to consider that choosing a value over another can have inpacts on the final scope of the application. E.g. time vs cost

## Improvements
- **Initializing Centroids**: for the beginning centroids we can pick them by randomly choosing K examples and setting each \( mu_i \) as one of the training examples. But since they are picked randomly among our training data we might face an edge case:
    - **Local Minimum**: All centroid end up close to each other so the algorithm gets stuck to a local minimum.
- **SOLUTION**: run the algorithm between *50 - 1000* times to find the best **starting** centroids.

## Uses
- **Image Compression**: reduction of the number of colors, reducing the whole image's size
- **Reccomendation Systems**: group users by preferences or items by similarity
- **Customer Segmentation**: group users by their behaviours
- etc.


