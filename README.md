## Data set [Got it from here](https://www.kaggle.com/datasets/purusinghvi/email-spam-classification-dataset) 

The objective of this repo is not to get state-of-the-art results. It is mainly focused on improving training accuracy and understanding how.

This project was implemented parallelly through my learning process. to get a deeper understanding of how actually the field of NLP became accurate and outperformed the human brain.

Looking at the evaluation of NLP. I just want to have a deeper understanding of every architecture. starting from RNNs to BERT.


The project is all about implementing all the NLP techniques.
> 1. Bag of words
> 2. Term frequency and Inverse document frequency
> 3. word to vec
> 4. Bi-directional LSTM
> 5. BERT

I mainly focused on how actually these techniques work and their internal mechanisms

### the accuracy of the test data is gradually increasing from Bag of words to BIRT

The goal is to understand the reason and know in depth theory behand every technique

## this are some of my observations Regarding accuracy


### BAG OF WORDS

> 1. In Bag of Words representation we consider entire text as a corpus. finding out unique words out of corpus. the unique words basically known to be vocabulary.
> 2. Considering all vocabulary( let say size of vocabulary is 1000) of the entire text and then we assign index to each word (token) alphabetically.
> 3. Now when we are creating a vector for each individual sentence. we consider the vector of size Vocabulary. then we traverse the entire sentence left to right. each word( token) is already assigned with a index from previous step. we are taking that index and incrimening the count at that index position.

 example -- "I have a pen, I use this pen for writing" let say this is the text. now we are creating vector to it !!
 At index position 'I' it is initially 0 then we make it 2 . then 'have' to 1, 'a' to 1,'pen' to 2 etc... this index positions are related to corpus of text.

 Major disadvantages of using Bag Of words is that 
 > Sparsity in terms of huge vocabulary ( think of a case where you have 10000 unique words , now every sentence has to be represented in 10000 dimensions)

 > Can't handle words wich are out of the Vocabulary (OOV)

 > Symantic meaning not captured ( Importance of word in the sentence)

Ways of making it more efficient 

>[!TIP]
>**using N-grams**
> N grams is basically considering n words togather and assigning it a separate index. in this way it can understand the importance of words occurring togather but disadvantages will remain same.


### Term frequency Inverse Document Frequency 

TFIDF Majorly solves the case of giving important to cirtain words. in the case of nlp the words that are uniquely identified makes more impact then that of continuously repeating. In such a case it is always efficient to be prioritising uniquely identified words 

example:- Let say we have 3 sentences 

"Boy looks good"

"Girl looks good"

"This dreas looks good"

Looking at 3 sentences it is pretty clear that good and looks doesn't create that impact as "Boy,Girl,And Dress". so " Boy , Girl and Dreess" given more importance while forming a vector.

In TFIDF importance is captured in two ways **term frequency** and **Inverse Document Frequency**

#### Term Frequency 

Term frequency focus on reputation of that perticular word in that sentence.

so Term frequency of a word t in a sentence s is given by

$$
TF(t, d) = \frac{\text{Number of times term } t \text{ appears in sentence } s}{\text{Total number of terms in sentence } s}
$$

term frequency of a word is callculated for every sentence. it is not dependent on the Corpus. it discribes the importance of the word in the sentence. 

#### Inverse Document Frequency (IDF)

Inverse document frequency focusses on the entire corpus, it calculate in number of sentences word t appeared. imagine if lesser the time the word appears the more unique it is and more importance is given to that word.


The **Inverse Document Frequency (IDF)** of a term t is given by:

$$
IDF(t) = \log \left( \frac{N}{DF(t)} \right)
$$

where:
- N is the total number of documents in the corpus.
- DF(t) is the number of documents that contain the term t.

IDF of a word is calculated by considering the whole corpus.so we take a word from vocabulary and chaeck for number of sentences had that word. we calculate the IDF value and assign it for that perticular word. this Vslue will be usefull when we reach out that word in a sentence. as it is constant for entire document for a vocabulary.

if we are appearing a sentence such as "Boy looks good" in such a case we take the idf score of Boy wich is already calculated and TF of boy is 1/3 (Frequency of Boy in the sentence is 1 and total words in the sentence is 3) multiplie both.


The **TF-IDF** score is calculated as:

$$
TF\text{-}IDF(t, d) = TF(t, d) \times IDF(t)
$$

vectors are generated in a way we consider entire vocabulary, in a sentence for each word we calculate tfidf and the value will be then placed at the index of word in the entire vocablery. it that way the words wich are present in the sentence eil have a value atvthe index in the vocabulary and remaining values will be 0. the vector of size vocablery is genrated.

TF-IDF is widely used in **text mining** and **information retrieval** to measure the importance of a term in a document relative to a collection of documents.

**Disadvantages of TF-IDF**
> 1. Symatic meaning is still not captured ( contextual meaning)
> 2. sparcity (length of each vector will be large for large carpus)

## Word to Vec




