# Week 01 - Anomaly Detection
## Introduction
- **Anomaly Detection**: an unsupervised learning algorithm that learns from a set of *normal* events and raises an alarm when an anomaly is detected
- **Density Estimation**: a technique used in *Anomaly Detection* that estimates the probability density of our data in a region and in its sub-regions
- **Gaussian Distribution** (*Normal Distribution*): a probability distribution that takes a common *bell* shape. The center of the bell is its **mean** $(\mu)\$ and the spread of data around the mean (its width) is its **variance** $(\sigma^2)\$
## Algorithm
Knowing that the *Normal Distribution* is:

$$
p(x_i) = \frac{1}{\sqrt{2\pi\sigma^2}}*e^\frac{-(x_i-\mu)^2}{2\sigma^2}
$$

Where:
- $\mu\$ = **Mean** = $\frac{1}{m} \sum_{j = 1}^{m} x_j \$
- $\sigma^2\$ = **Variance** = $\frac{1}{m} \sum_{i = 1}^{m}(x^{(i)}-\mu)^2 \$

And so if $\vec{x}$ is a vector, then:

$$
p(\vec{x}) = p(x_1; \mu_1, \sigma_1^{2})*p(x_2; \mu_2, \sigma_2^{2})*p(x_3; \mu_3, \sigma_3^{2})*...*p(x_n; \mu_n, \sigma_n^{2})
$$

Or also:

$$
\prod_{j = 1}^{n}p(x_j; \mu_j, \sigma_j^{2})
$$

Having $\epsilon\$ as a **small** threshold.

So if:
$$p(\vec{x})< \epsilon$$

Then:
**ANOMALY DETECTED**

Else if:
$$p(\vec{x})\geq \epsilon$$

Then:
**NOT ANOMALY**
## Real Number Evaluation
Technique to **evaluate** our Anomaly Detection algorithm:
1. Assume there are a **small** amount of *anomalies* out of a **large** amount of *normal* examples. E.g. 10000 good examples, 20 anomalies
2. Divide the data set into:
  - **Training Set/Cross Validation/Test set**: if number of anomalies is **high** enough. Anomalies will be split **only** among **CV** and **Test set**. E.g. 6000 good in training, 2000 good + 10 anomalous in CV, 2000 good + 10 anomalous in Test set
  - **Training Set/Cross Validation**: if  number of anomalies is **low** (e.g. 2). All anomalies will be in **CV set**. E.g. 6000 good in training, 4000 good + 2 anomalous in CV.
3. Compute **Precision, Recall, and F1 Score**

**IMPORTANT**: splitting data only into training and cv set is *dangerous* but sometimes it can't be avoided if we only have a **small** amount of anomalous data
## Improvements
Check if features are **Gaussian**. If features are **not Gaussian** and data is **skewed** then:
1. Apply **transformations** such as:
   - $\log(x)\$
   - $\log(x+c)\$
   - $\sqrt{x}\$,
   - etc.
2. Check if transformed feature becomes Gaussian
## Anomaly Detection vs Supervised Learning

**Anomaly Detection**

- Used when you have a very small number of positive (y = 1, anomalous) examples / you have a large number of negatives (y = 0, normal)
- If there are many types of anomalies and often new ones

**Supervised learning**:

  - Use when classes (labels) are balanced - large number of positives and negatives
  - If there are enough positive examples for the algorithm to get a sense of what positives look like

## Uses
- Fraud Detection
- Manufacturing -> finding *unseen* defects
- Monitor machines in data centers
