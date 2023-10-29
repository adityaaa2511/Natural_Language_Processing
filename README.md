# Natural_Language_Processing
This repository contains NLP projects that I have created using data science and deep learning.
## Text Classifier using Markov Model
* The **Markov Model** is used to model sequences. In NLP, the sequences can be of **Categorical Symbols** which are referred to as **States.**So, the Markov Model is all about modeling sequences where each state depends on the previous state we came from (Markov Property). For that, we create the **State Transition Matrix(A)** and the **Initial State Vector(pie)**.<br/>
* Using the Markov model(A and pie) we can answer interesting questions like:-<br/>1) What is the probability of a particular sequence? <br/>2) Given the dataset, can we determine A and pie(**Training**)<br/> 
* We use **Bayes Theorem** and **Maximum Likelihood** to answer these questions respectively. However, slight modifications are required. We work with **Log-Probabilities**, as these numbers are often quite small and multiplying many small numbers makes the product tend to 0. Also, we **Add One/Epsilon Smoothing** while calculating Maximum Likelihood to in order to have some arbitrary probability of a particular transition instead of 0.<br/>
