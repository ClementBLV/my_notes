Automatically constructing Wordnet synsets

---

__tag__ : #WordNet #Translation 
__publication date__:  8 Aug 2022
__reading date__ : 24/04/2023
__link__ : https://arxiv.org/abs/2208.03870
__comments__ : Automatically construct [[WordNet]] and automatically generate synset for poor language WordNet using public WordNets, Translation and a bilingual dictionary: Translate the synset into the target language and rank the best translation.
They  <u>multiply by 10</u>  the synset coverage achieve by the direct translation method

---

> **abstract** . Manually constructing a Wordnet is a difficult task, needing years of experts' time. As a first step to automatically construct full Wordnets, we propose approaches to generate Wordnet synsets for languages both resource-rich and resource-poor, using publicly available Wordnets, a machine translator and/or a single bilingual dictionary. Our algorithms translate synsets of existing Wordnets to a target language T, then apply a ranking method on the translation candidates to find best translations in T. Our approaches are applicable to any language which has at least one existing bilingual dictionary translating from English to it.

## Goal 

Generate high quality synset (set of synonyms) in a target language generally low and poor resources target languages. Plus the method need to be able to reduce de noise. 
They have used the Microsoft Translator (free access for research)

## Method
+
Needs : 
- English [[WordNet]]
- Other rich sources Finnish , Japanese and French 
- Existing wordnet in the target language (can be small)
- A Machine translation tool 
- A bilingual dictionary
Output :
- WordNet in target T 

They take a Id af a word:
1. in all wordnet they translate the word with the same ID
2. They see which translation occurs the most in the different WordNet (simplification they use a more complicated and efficient way to rank canditates based on the num of WN the occurrences etc  )
3. That the correct translation (if all the same rank no translation is taken into account)
They also use a different method were instead of translating every thing to the target language they firstly traduce every thing to english and use an english - target dictionary to get the the synset candidates in the target language and then they rank those translations 


![[Pasted image 20230425223108.png]]

vs naive direct translation 
![[Pasted image 20230425224044.png]]

## Result 

They  <u>multiply by 10</u>  the synset coverage achieve by the direct translation method.
