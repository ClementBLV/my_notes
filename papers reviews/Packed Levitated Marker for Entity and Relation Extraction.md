__tag__ : #RE 
__publication date__: 21 Apr 2022
__reading date__ : 
__link__ : https://paperswithcode.com/paper/pack-together-entity-and-relation-extraction
__comments__ : Top 1 in many benchmark for [[RE]] and [[NER]] they use a new span representation approach. 

---

>__abstract__:  Recent entity and relation extraction works focus on investigating how to obtain a better span representation from the pre-trained encoder. However, a major limitation of existing works is that they ignore the interrelation between spans (pairs). In this work, we propose a novel span representation approach, named Packed Levitated Markers (PL-Marker), to consider the interrelation between the spans (pairs) by strategically packing the markers in the encoder. In particular, we propose a neighborhood-oriented packing strategy, which considers the neighbor spans integrally to better model the entity boundary information. Furthermore, for those more complicated span pair classification tasks, we design a subject-oriented packing strategy, which packs each subject and all its objects to model the interrelation between the same-subject span pairs. The experimental results show that, with the enhanced marker feature, our model advances baselines on six NER benchmarks, and obtains a 4.1%-4.3% strict relation F1 improvement with higher speed over previous state-of-the-art models on ACE04 and ACE05. Our code and models are publicly available at https://github.com/thunlp/PL-Marker.



- __solid marker__ : Insert two marks before and after the token with a subject and object marker => cannot handle multiples pairs at the same time
- __levitated marker__ : decrease the model performance but gain in computational efficiency. The markers in a pair are set to be visible in the attention mask => Ignore interrelations between spans 
- __Packed Levitated Marker__ : like that it can handle interrelations between spans : like the relation "_attack_" between David and the restaurant workers.

Here the example below with the relation "_located_in_"

![[Pasted image 20230424114536.png]]

## Packed Levitated Marker 

They pack levitated markers in the encoding sentence but put several markers in the sentence increase the complexity. So they pack all the span with the same start together 


## Strategies 

The pack all the candidate **object** span with levitating markers and the **subject** with solid markers 


Packed Levitated Marker based on neighborhoods packing significantly improve NER task compared to random packing, and gain of 4.7 in F1 score 

