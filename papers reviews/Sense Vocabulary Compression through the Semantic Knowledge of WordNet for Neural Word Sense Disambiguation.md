
__tag__ : #disambiguation #word_sense_disambiguation #WordNet 
__publication date__: 2019
__reading date__ : 21/04/23
__link__ : https://paperswithcode.com/paper/sense-vocabulary-compression-through-the
__comments__ : il a gagné 9 point par rapport au 3 eme et 6 point par rapport au 2 eme en therme de F1 score sur [[SemEval]] Task 12 le rank 1 pour l' instant: Interessant parceque il se focus sur les relation de wordnet de type [hypernym] , [hyponym] , synonim  

---

>__abstract__: In this article, we tackle the issue of the limited quantity of manually sense annotated corpora for the task of word sense disambiguation, by exploiting the semantic relationships between senses such as synonymy, hypernymy and hyponymy, in order to compress the sense vocabulary of Princeton WordNet, and thus reduce the number of different sense tags that must be observed to disambiguate all words of the lexical database. We propose two different methods that greatly reduce the size of neural WSD models, with the benefit of improving their coverage without additional training data, and without impacting their precision. In addition to our methods, we present a WSD system which relies on pre-trained BERT word vectors in order to achieve results that significantly outperforms the state of the art on all WSD evaluation tasks

The goal is to disambiguate word of wordnet. 

## [[Word Sense Disambiguation]]: 
For this task they use a pre-trained BERT, and they manage to significantly outperformed the baselines.
They deal with disambiguation of words which have never been seen in the training data.
In this work they used the related concept of a word (hypernym, hyponym) to disambiguate it as those concepts are closely related to this work. 

## [[WordNet]]:

Here they use only a subset of wordnet to disembuate all senses = core concepts sences. 
Protocole :
1. They take  a full wordnet
2. Generate a subset =  extract the core concepts ~ the essence, this subset will be used for disambiguation 
	- 2 methods to do create the subset : called sense vocabulary compression methods
	- With this subset they can deal with the disambiguating of unseen word in the training data 
!!!! If it is trained on all of WordNet senses the vocab size is more than 200000 so the system is really slow => That is why they proposed a way to group MULTIPLE sense tag which refer to the SAME CONCEPT
__=> They group senses of a same synset cause 117000 synset but 207000 senses
=> they group synset with the same _hypernymy___ 
They also use SemCor for evaluation and other senses ? 


## Hypernym methods 

for one synset they try to find the highest ancestor = ! should be discriminative of all the different senses of the TARGET WORD 
preserve the hypernyms that are indispensable to discriminate the senses of the other words in the dictionary
example with the word mouse to discriminate between the computer and the rotten we would get rid of the hypernym animal and just link it to the hypernym living_thing bit we need the hypernym animal to distinguish between the two senses of ''prey'' (person who is the aim of an attack or animal hunted or caught for food)

## Implemetation 

Due to the fact that [[BERT]]’s internal tokenizer sometimes split words in multiples tokens (i.e. [“rodent”] becomes [“rode”, “##nt”]), we trained our system to predict a sense tag on the first token only of a splitted annotated word


Permet de donner un sens a un mot en utilisant une version symplifé de wordnet 

Keep only the nesessary info to efficiently differentiate the senses of words in the database
=> you can use only 6% of the original size while doubling the coverage of the same corpus

## Evaluation 

They use [[SemEval]] for the evaluation 
SemCore 
Texts semantically annotated with WordNet 1.6 senses (created at Princeton University), and automatically mapped to WordNet 1.7, WordNet 1.7.1, WordNet 2.0, WordNet 2.1, WordNet 3.0

## How can it be used 

You have an word and you need to know the sence of this word in order to retrieve the proper definition. 