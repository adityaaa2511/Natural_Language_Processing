# Natural_Language_Processing
This repository contains NLP projects that I have created using data science and deep learning.
## The Markov Model
* The **Markov Model** is used to model sequences. In NLP, the sequences can be of **Categorical Symbols** which are referred to as **States**. So, the Markov Model is all about modeling sequences where each state depends on the previous state we came from (Markov Property). For that, we create the **State Transition Matrix(A)** and the **Initial State Vector(pie)**.<br/>
* Using the Markov model(A and pie) we can answer interesting questions like:-<br/>1) What is the probability of a particular sequence? <br/>2) Given the dataset, can we determine A and pie(**Training**)<br/> 
* We use **Bayes Theorem** and **Maximum Likelihood** to answer these questions respectively. However, slight modifications are required. We work with **Log-Probabilities**, as these numbers are often quite small, and multiplying many small numbers makes the product tend to 0. Also, we **Add One/Epsilon Smoothing** while calculating Maximum Likelihood in order to have some arbitrary probability of a particular transition instead of 0.<br/>
### Text Classifier using Markov Model
* In order to convert the **Unsupervised** Markov Models to **Supervised** Text Classifier, we will make use of **Bayes Rule** to create a **Bayes Classifier**. We will train 2 separate Markov Models for each of the classes. Then, we will calculate the probability of a sequence. In my case, I will be using poems by 2 authors as my sequences. So, this probability is **P(poem|authoer=k)**. However, what I want to know is **P(author|poem)**.<br/>
* If I have the distribution of P(author|poem), then I will simply take the **ArgMax** of the highest probability to make the decision. We can get the required distribution using the **Bayes Rule**.
So, the denominator of the resulting expression **P(poem)** is not dependent on any author, therefore there is no need for its consideration.<br/>
* The numerator **P(poem|author=k)P(author=k)** is now of importance. If the **Prior P(author)** is uniform i.e there is no reason as to why any particular answer will be more likely, given no information then, P(author=k) is also a **constant** and can be removed. This reduces the expression to the likelihood once again.<br/>
### Language Model using Markov Model
