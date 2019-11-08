back to [main page](main.md)

# Probability & Statistics

![](images/probability_header.jpg?raw=true)

## Definitions

### Sample Space
The sample space *S* of an experiment is the set of all possible outcomes of the experiment. The sample space of an experiment can be finite, countably infinite, or uncountably infinite.

### Event
An event *A* is a subset of the sample space *S*, an we say that *A* occurred if the actual outcome is in A.

![](images/sample_space.png?raw=true)

Set theory is very useful in probability. 

![](images/sets.png?raw=true)

### Naive Definition of Probability

Let A be an event for an experiment with a finite sample space S. The naive probability of A is:

![](images/probability_1.png?raw=true)

**note:** we use |A| to denote de size of A.

The naive definition is very restrictive in that it requires S to be finite, and with equally likely outcomes.

### How to count
Calculating the naive probability of an event A involves counting the size of A and the size of the sample space S. Often the sets we need to count are extremely large. This section introduces some fundamental methods for counting.

1) **Multiplication rule:** Consider a compound experiment consisting
of two sub-experiments, Experiment A and Experiment B. Suppose that Experiment A has a possible outcomes, and for each of those outcomes Experiment B has b possible outcomes. Then the compound experiment has ab possible outcomes.
2) **Sampling with replacement:** Consider **n** objects and making **k**
choices from them, one at a time with replacement (i.e., choosing a certain object does not preclude it from being chosen again). Then there are **n<sup>k</sup>** possible outcomes.
3) **Sampling without replacement:** Consider **n** objects and making
**k** choices from them, one at a time without replacement (i.e., choosing a certain object precludes it from being chosen again). Then there are **n x(n-1) x ... x (n-k+1)** possible outcomes, for k <= n.
This result also follows directly from the multiplication rule: each sampled ball is again a sub-experiment, and the number of possible outcomes decreases by 1 each time.
4) The **binomial coefficient:** counts the number of subsets of a certain size for a set, such as the number of ways to choose a committee of size k from a set of n people. Sets and subsets are by definition unordered, e.g., {3, 1, 4} = {4, 1, 3}, so we are counting
the number of ways to choose k objects out of n, without replacement <u>and without distinguishing between the different orders in which they could be chosen.</u> 

![](images/binomial_coef.png?raw=true)

### Non-Naive Definition of Probability
Probability has the following properties, for any events A and B:

![](images/probability_2.png?raw=true)

![](images/probability_3.png?raw=true)

### Conditional Probability
If A and B are events with P(B) > 0, then the conditional probability of A given B, denoted by P(A|B), is defined as:

![](images/conditional_prob.png?raw=true)

**Intuition:** From left to right: (a) Events A and B are subsets
of the sample space. (b) Because we know B occurred, get rid of the outcomes in B<sup>c</sup>. (c) In the restricted sample space, renormalize so the total mass is still 1.

![](images/intuition.png?raw=true)

### Bayes Rule


## Correlation
Correlation is a statistical measure that describes the association between random variables. The correlation measures the linear association between continuous variables. In other words, this coefficient quantifies the degree to which a relationship between two variables can be described by a line. Correlation values range between -1 and 1.  

![](images/correlation.png?raw=true)