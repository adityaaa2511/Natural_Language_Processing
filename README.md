# Natural_Language_Processing
This repository contains NLP projects that I have created using data science.
## 1) The Markov Model
* The **Markov Model** is used to model sequences. In NLP, the sequences can be of **Categorical Symbols** which are referred to as **States**. So, the Markov Model is all about modeling sequences where each state depends on the previous state we came from (Markov Property). For that, we create the **State Transition Matrix(A)** and the **Initial State Vector(pie)**.<br/>
* Using the Markov model(A and pie) we can answer interesting questions like:-<br/>1) What is the probability of a particular sequence? <br/>2) Given the dataset, can we determine A and pie(**Training**)<br/> 
* We use **Bayes Theorem** and **Maximum Likelihood** to answer these questions respectively. However, slight modifications are required. We work with **Log-Probabilities**, as these numbers are often quite small, and multiplying many small numbers makes the product tend to 0. Also, we **Add One/Epsilon Smoothing** while calculating Maximum Likelihood in order to have some arbitrary probability of a particular transition instead of 0.<br/>
### 1) Text Classifier using Markov Model
* In order to convert the **Unsupervised** Markov Models to **Supervised** Text Classifier, we will make use of **Bayes Rule** to create a **Bayes Classifier**. We will train 2 separate Markov Models for each of the classes. Then, we will calculate the probability of a sequence. In my case, I will be using poems by 2 authors as my sequences. So, this probability is **P(poem|authoer=k)**. However, what I want to know is **P(author|poem)**.<br/>
* If I have the distribution of P(author|poem), then I will simply take the **ArgMax** of the highest probability to make the decision. We can get the required distribution using the **Bayes Rule**.
So, the denominator of the resulting expression **P(poem)** is not dependent on any author, therefore there is no need for its consideration.<br/>
* The numerator **P(poem|author=k)P(author=k)** is now of importance. If the **Prior P(author)** is uniform i.e there is no reason as to why any particular answer will be more likely, given no information then, P(author=k) is also a **constant** and can be removed. This reduces the expression to the likelihood once again.<br/>
### 2) Language Model using Markov Model
* In order to generate poems using Markov Models, we will use 2nd order Markov Models i.e the state at time t will depend on the state at time t-1 and t-2. The **State Transition Tensor** is now of 3 dimensions. The A matrix will be used to generate the 2nd word in the sequence, the pie vector will be used to generate the first word and the rest of the words will be generated(Sampled) from the State Transition Tensor.
#### Code Discussion for the Language Model
* First of all we will **remove punctuations** and **tokenize** the words in the dataset with the intention of eventually making a **dictionary** of words and corresponding probabilities. We will sample(generate) our words from this dictionary.
* Next we create helper functions to maintain the words and their frequencies. We will include seperate conditions for the first word and the final word in one line of the poem.
* Then we normalize the frequencies into probabilities for each of the dictionaries containing the samples for the next word.
* Lastly, we employ a similar function to the **np.random.choice** to sample a word based on sampling a number between 0 and 1 and using a cummulative score.
* Voila, we now have our personal Robert Frost like Poem Generator!!
### 3) Cypher Decryption
* We will create a **Probabilistic Model** of the English language and then use it to train a **Bi-gram Markov Model**.
* Sentences are made up of words and so, we will compute the probability of the occurrence of real words. Actual words will have higher probabilities and others will have a lesser probability. Here, also we will use **Add One-Smoothing** and **Log probabilities**.
* Then we will utilize **Genetic Evolutionary Algorithms** to determine which encryption mapping(substitution mapping in this case) is the best suited for decryption(These are used when we cant differentiate the model objective with respect to the model parameters i.e cant apply gradient descent). Basically, we will have a pool of mapping(which will be mutated via swaping) and initially we take the best 5 suited mappings and then create offsprings(3 per each parent, so total remains at 20). We will again calculate the 5 best suited mappings(via log-likelihood) and repeat this process for a fixed amount of iterations.
* 2 advantages of employing this algorithm being that we will not be stuck at a local maxima nor do we need to check for all possible mappings(26!) to determine the best one which requires a huge chuck of time.
### 4) Article Spinner
* I will use a **Trigram Markov Model** in order to replace the ith word conditioned on the **(i-1)th** and **(i+1)th** word using the Probabilistic Language Model.
* Also, it is not necessary to replace every word so i'll take the replacement probability to be 0.3.
