Clarrify a text by correctly asigning the right sence to a word given a set of predefine sences. 
Possible approches : (see [[Sense Vocabulary Compression through the Semantic Knowledge of WordNet for Neural Word Sense Disambiguation]])

- with a KB 
- with a KG 
- Supervised : used annotated corpora to train a classifier (SVM, neural network ...) = most popular but pb not enough corporas 
- Unsupervised : used parallel corporas 

Ex: the goal of WSD would be to identify the corect sence of a word: 
mouse = computer mouse or animal ? 

## WSD based on language model 

RNN wich predict a word given its surrounding product a sense vector and the sense closest to word + the surrounding context of the word is assigned  

## WSD based on a Softmax Classifier

It directly assign a sense to each word thanks to the probability distribution of a softmax function.
Either : 
- one classifier for each words (4 output classifier for the 4 senses of mouse ) = useful when there are a small and precise set of word to disambiguate which have been clearly identified
- a big model with all the senses = can predict the same senses for two different words and can handle unseen words and misspellings  
- new way = compute attention between the _context_ of a target and its different _gloss_ => Incorpore [[WordNet]] into the work of WSD

## Sense clustering methods 

Create "*supersense*" tag buy grouping together different tags of WordNet senses, these tags correspond to brad domains like _food_ or _objects_ 
=> 41 categories = small and easy train models 

## Issues 

If one senses of a know word has never been seen the system can't know it. If it is trained on all of WordNet senses the vocab size is more than 20000 so the system is really slow 