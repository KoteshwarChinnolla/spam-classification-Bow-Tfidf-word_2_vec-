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

\documentclass{article}
\usepackage{amsmath}

\begin{document}

\section*{Term Frequency and Inverse Document Frequency}

\textbf{Term Frequency (TF):} The term frequency of a term t in a document d is given by:

\[
TF(t, d) = \frac{\text{Number of times term } t \text{ appears in document } d}{\text{Total number of terms in document } d}
\]

\textbf{Inverse Document Frequency (IDF):} The inverse document frequency of a term t is given by:

\[
IDF(t) = \log \left( \frac{N}{DF(t)} \right)
\]

where:
\begin{itemize}
    \item N is the total number of documents in the corpus.
    \item DF(t) is the number of documents that contain the term t.
\end{itemize}

\textbf{TF-IDF:} The TF-IDF score is computed as:

\[
TF\text{-}IDF(t, d) = TF(t, d) \times IDF(t)
\]

\end{document}



