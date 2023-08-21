__tag__ : #BabalNet #word_sense_disambiguation #disambiguation 
__publication date__: 2022
journal : Colin
__reading date__ : 
__link__ : https://paperswithcode.com/paper/multilingual-word-sense-disambiguation-with-1
__comments__ : Transfer from a rich database in one language to another one smaller in another language. They use [[BabelNet]]. Significant results with  SemEval-13 and SemEval-15 datasets.

>**abstract** : As a key natural language processing (NLP) task, word sense disambiguation (WSD) evaluates how well NLP models can understand the lexical semantics of words under specific contexts. Benefited from the large-scale annotation, current WSD systems have achieved impressive performances in English by combining supervised learning with lexical knowledge. However, such success is hard to be replicated in other languages, where we only have limited annotations. In this paper, based on the multilingual lexicon BabelNet describing the same set of concepts across languages, we propose building knowledge and supervised-based Multilingual Word Sense Disambiguation (MWSD) systems. We build unified sense representations for multiple languages and address the annotation scarcity problem for MWSD by transferring annotations from rich-sourced languages to poorer ones. With the unified sense representations, annotations from multiple languages can be jointly trained to benefit the MWSD tasks. Evaluations of SemEval-13 and SemEval-15 datasets demonstrate the effectiveness of our methodology

## Goal 
To infuse a scarce source language kb using a rich source
**=> MULTILINGUAL WORD SENSE DESAMBIGUATION**

## Method 
They use the rich language to infuse a supervised multilingual [[Word Sense Disambiguation]] MSWD for the multilingual part they use a translation and alignment tool and used it as a weak supervision.
In the paper the construct a MWSD with a [[BERT]] as bone model.
They achieve a benchmark on [[SemEval]] 13 and 15

They applied their method to Eng, Fr , Sp , De , It 

## Architecture 
![[Pasted image 20230421213436.png]]
The model is vastly based on a m-BERT-UNI
- a biencoder for the English WSD task !!!! THEY USE mBERT (multilingual Bert trained on 104 languages)
	- one to encode the multilingual context 
	- one to encode the gloss

[[SemCor]] for senses 

## Results : 

Able to infuse knowledge from rich source language into scarce ones  for a Multilingual [[Word Sense Disambiguation]] 
Outperform the current methods for MWSD up to 17 points on SemEval task for certain languages. 