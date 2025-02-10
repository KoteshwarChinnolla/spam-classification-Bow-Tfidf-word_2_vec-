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

> In Bag of Words representation we consider entire text as a corpus. finding out unique words out of corpus. the unique words basically known to be vocabulary.

> Considering all vocabulary( let say size of vocabulary is 1000) of the entire text and then we assign index to each word (token) alphabetically.

> Now when we are creating a vector for each individual sentence. we consider the vector of size Vocabulary. then we traverse the entire sentence left to right. each word( token) is already assigned with a index from previous step. we are taking that index and incrimening the count at that index position.

 example -- "I have a pen, I use this pen for writing" let say this is the text. now we are creating vector to it !!
 At index position 'I' it is initially 0 then we make it 2 . then 'have' to 1, 'a' to 1,'pen' to 2 etc... this index positions are related to corpus of text.
 
