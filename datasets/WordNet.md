date : 20/04/2023
tags : #WordNet 
related topics : [[hyponym]], [[hypernym]] , [[BabelNet]] , [[Global FrameNet]] , 

---

## Original 
Developped by Princton University and was make with teh help expert lexicographer, WordNet is a lexical Knowlage Base.
It can be used for : sentiment analysis , natural languae generation, textual entailement.
!! only one update since 2006 (date of its release) !!


## 2019 version
Hence new version propose in [[English WordNet 2019 – An Open-Source WordNet for English]]. This one is entirely open source, the goal was like for Linux project, to have enought people involve to earase safely the need of experts (even if they were still involved). 
They haven´t change the stucture and the definitions of the original wordnet, they have corrected the minors spelling errors, they also change the examples which didn t use any lemmas of the synset, and they add new lemmas. In the future realese they plan to add relations and synset. 

![[Pasted image 20230420100940.png]]
## 2020 version 

see [here](https://aclanthology.org/2020.mmw-1.3.pdf)

## WordNet elements 
synsets : express a concept, it is a set of synonims that are interchangables. A synset is a set of synonims. If one word has several ñeaning, each meaning has its own synset. Each synset have a gloss and an example. They have a id caled synset tag 

>A synset is technically a group of one or more word-senses that have the same definition and consequently the same meaning. For instance, the first senses of “eye”, “optic” and “oculus” all refer to a common synset which definition is “the organ of sight”.

gloss : small definition of a synset 

lemmas :  wordnet's version of an entry in a dictionary: A word in canonical form, with a single meaning

senses : is a discrete representation of one aspect of the meaning of a word ex bank (river) and bank (office) have two senses (not 100 sure)
average number of senses per word is 3 (compared to the 207272 senses in total)

synset relations : 
	- most frequent : "is a " , aka hyponymy  large synset -> specific synset  ( type for objects and instances for persons , Obama is a instance of president )
		- hypernym is a generalization of a term 
		- hyponym is a specification 
	- meronomy : "part of" between synsets 
	- antonymy : between adjectives means they are opposites wet / dry 
	- troponyms : link between verbs to describe the gain of precision communicate -> talk -> whisper 
	Hypernym is a generalization of motor vehicle is a hypernym of car

| Relation | Description |
| ----------- | ------------- |
| Hyponym |  is a kind of car is a hyponym of motor vehicle |
| Meronym | is a part of lock is a meronym of door | 
| Holonym | contains part door is a holonym of lock |
| Troponym | is a way to ﬂy is a troponym of travel |
| Antonym | opposite of stay in place is an antonym of travel |
| Attribute | attribute of fast is an attribute of speed |
| Entailment | entails calling on the phone entails dialing |
| Cause | cause to to hurt causes to suﬀer |
| Also | See related verb to lodge is related to reside |
| Similar to | similar to evil is similar to bad |
| Participle of | is participle of stored is the participle of to store |
| Pertainym | pertains to radial pertains to radius |




## WordNet Gloss Corpus

??

## WordNet library 

To use WN we can either use the NLTK library of [wn](https://pypi.org/project/wn/) library. We prefer to use the second one to avoid NLTK. The documentation of wn can be found [here](https://wn.readthedocs.io/en/latest/?badge=latest).
This library is an interface for using wordnet in the [WN-LMF](https://globalwordnet.github.io/schemas/) 

### Storage of the wn 

The library will search in the .wn_data file for existing wordnet on the device in the download file for download LMF files from the web (Their filename is a hash of the URL to avoid double download) or the wn.db

\``` wn.config.data_directory = '~/Projects/wn_data'```

```wn.config``` is an object 

### WordNet object

In the library there are 4 objects ```Sense, Word``` , ```Synsets``` and ```Lemmas```. Usually senses are simple seen as an edge and the link between word and synset. But here they give metadata to senses so it is more like an edge. 

**Word** bank is present in two different synsets , but we can disciminate by the sense , 14 sense of bank is in one synset while the other is in another 
![[Pasted image 20230508122242.png]]




### Modify and save 

wn library can't modify the wn it's only a reading tool. 

#### Editor Benchmark 

##### StarNet: A WordNet Editor Interface

Cited 0 

##### VisDic – Wordnet Browsing and Editing Tool

Cited 56 
Date 2004
link : https://citeseerx.ist.psu.edu/viewdoc/download;jsessionid=0A7D123609BFEF54E48D5CCC1CBAB8BB?doi=10.1.1.1.2146&rep=rep1&type=pdf
> **abstract** : This paper deals with wordnet development tools. It presents a designed and developed system for lexical database editing, which is currently employed in many national wordnet building projects. We discuss basic features of the tool as well as more elaborate functions that facilitate linguistic work in multilingual environment.

The one used in many national WN projects, it give you full control on the editing process

##### WordnetLoom – a Multilingual Wordnet Editing System Focused on Graph-based Presentation

Cited 15
Date 2018

##### WN-editor

No documentation 
