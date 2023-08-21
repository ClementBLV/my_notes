
__name__ : [[Automatic Enrichment of WordNet with Common-Sense Knowledge]]
__tag__ : #WordNet #disambiguation 
__publication date__: 2016
__reading date__ : 20/04/23
__link__ : https://paperswithcode.com/paper/automatic-enrichment-of-wordnet-with-common 
__comments__ :  super outdated but can gives ideas on how to enrich [[WordNet]] and which problem can occurs 

---
>__abstract__ : WordNet represents a cornerstone in the Computational Linguistics field, linking words to meanings (or senses) through a taxonomical representation of synsets, i.e., clusters of words with an equivalent meaning in a specific context often described by few definitions (or glosses) and examples. Most of the approaches to the Word Sense Disambiguation task fully rely on these short texts as a source of contextual information to match with the input text to disambiguate. This paper presents the first attempt to enrich synsets data with common-sense definitions, automatically retrieved from [[ConceptNet]] 5, and disambiguated accordingly to WordNet. The aim was to exploit the shared- and immediate-thinking nature of common-sense knowledge to extend the short but incredibly useful contextual information of the synsets. A manual evaluation on a subset of the entire result (which counts a total of almost 600K synset enrichments) shows a very high precision with an estimated good recall.

## Highlights 

=> Automatic enrichment of [[WordNet]] synset with the disambiguated concepts of [[ConceptNet]]. 
enrichment of lexical dataset with conceptual dataset

got 88.19% of accuracy on 505 random human checked examples 

doesn't align Consepts from [[ConceptNet]] to [[WordNet]] synset simply by a similarity score. It is based on real overlapping word and direct relations. And they use heuristics for disambiguation 

## Representation of WordNet 

they represent Wordnet infos as followed : 
for an synset i of wordnet :
- S_i = < T_i , g_i , E_i > where T_i represent the set of synonym terms in the synset , g_i the gloss definition and E_i the examples 
- A set of semantic properties of and around S_i , P-word ( S_i ) ex *hypernym* (S_i) is the __direct__ hypernym synset of S_i , it can also be a set of synset like with the property _made_of_ : _metonymy_(S_i)
they represent conceptNet as followed : 
- NPi - rel_k - NPj   where NP is simple a non disambiguated group of noun or noun 








