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



## References
1. https://web.stanford.edu/class/archive/cs/cs224n/cs224n.1194/slides/cs224n-2019-lecture06-rnnlm.pdf
2. https://www.fit.vut.cz/research/group/speech/public/publi/2010/mikolov_interspeech2010_IS100722.pdf
3. https://wiki.eecs.yorku.ca/course_archive/2016-17/F/6327/_media/rn_dallas.pdf
4. https://www.comp.hkbu.edu.hk/~markus/teaching/comp7650/tnn-94-gradient.pdf
