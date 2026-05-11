## Language Models
For a Language Model(LM) to successfully capture the semantic meaning of some text, it is essential that it can capture the <b>context</b> of the words that came before.
The idea of modeling the probability of the next word in a sequence based on the words that came before is one of the most popular ideas in modern NLP. For instance, the word <b>rock</b> in 
the two sentences, "The man found a <b>rock</b>." and "The boy was listening to <b>rock</b> music." has two clearly, distinct meanings because of the surrounding context.  
In the following sections, various LM architectures are discussed.  

### n-Gram
Early attempts at modeling context came in the form of n-gram models. An n-Gram, is a sequence of text of length n. For example, in the sentence a, "The man found a <b>rock</b>.", 
possible bigrams(n=2) could be "The man", "man found", etc. Likewise a trigram(n=3) and 4-gram would have sequences of length 3 and 4 respectively. 

The approach for an n-Gram model is to process the entire corpus of text and calculate the conditional probability of each n-Gram. 
In the example of a bigram model, one would process the entire corpus in bigram(n=2) sized chunks and count the frequency of each bigram to estimate conditional probabilities. 
After processing the corpus, generating text is as simple as starting with a sequence of length <i>n-1</i> (can be randomly sampled) and using that as input to the n-Gram model. 
Then, one can generate the next word in the sequence by calculating the probability of some word in the vocabulary given the <i>n-1</i> words in the current n-Gram or <b>P</b>(next word | n-1 words in n-Gram). 
The word that returns the highest probability is chosen to be the next word in the sequence. 
This process can be recursively ran until a desired text-length.

### RNN
The approach that an RNN takes is to capture the context of text using recurrent connections. In other words, an RNN maintains a time-varying hidden state(s(t)) such that the input to an RNN is both the word embedding(x(t)) and the hidden state at the previous time step(s(t - 1)). Using this architecture, an RNN is able to store the context of previous words in its hidden state and represent semantic meaning across time. 

Input to an RNN LM consists of a sequence of text; the output is a sequence of words that contains the predicted next word for each word in the input. The benefit of using an RNN
is that this "sequence" can be of any length. As a result, there is no fixed window size that an RNN has to adhere to. For each sequence of text the RNN recieves, two actions are performed: predict the next word for each word in the sequence and calculate the new hidden state. For example, suppose an RNN LM that takes a sequence of length 4 as input 
and the sentence, "The man found a <b>rock</b>" is provided. Then, the RNN would iterate over the sequence and predict the next word after "The" and "man" and "found", and so on. 

For each prediction, the pipeline is as follows: 1. the current word is passed through an embedding layer to produce a word embedding, which is then linearly projected and added to a linear projection of the previous hidden state 2. An activation function, typically tanh or sigmoid, is applied to this result to produce the new hidden state 3. The new hidden state is passed through an output layer and softmax is applied to generate a distribution over all words in the vocabulary. During training, this distribution is compared against the true next word using cross entropy loss. During inference, the next word is chosen by either randomly sampling from the distribution or taking the argmax 4. Process the next word in the sequence and repeat until the entire sequence is processed. The key insight is that the input to the hidden layer relies on both the input word as well as the hidden state at the previous time step. However, in practice, the vanishing gradient problem means that older context tends to fade from the hidden state over long sequences, limiting the RNN's ability to capture long-range dependencies.


## References
1. https://web.stanford.edu/class/archive/cs/cs224n/cs224n.1194/slides/cs224n-2019-lecture06-rnnlm.pdf
2. https://www.fit.vut.cz/research/group/speech/public/publi/2010/mikolov_interspeech2010_IS100722.pdf
3. https://wiki.eecs.yorku.ca/course_archive/2016-17/F/6327/_media/rn_dallas.pdf
4. https://www.comp.hkbu.edu.hk/~markus/teaching/comp7650/tnn-94-gradient.pdf
