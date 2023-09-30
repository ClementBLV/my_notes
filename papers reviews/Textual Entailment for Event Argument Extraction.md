tag : #Entailement #RE #Zero-shot 
publication date : 3 May 2022
reading date : 30/09/2023
link : https://arxiv.org/abs/2205.01376
comments : Event extraction using entailment in a zero and few shot way. Good presentation of the entailment and the verbalization task

----

>**abstract** : Recent work has shown that NLP tasks such as Relation Extraction (RE) can be recasted as Textual Entailment tasks using verbalizations, with strong performance in zero-shot and fewshot settings thanks to pre-trained entailment models. The fact that relations in current RE datasets are easily verbalized casts doubts on whether entailment would be effective in more complex tasks. In this work we show that entailment is also effective in Event Argument Extraction (EAE), reducing the need of manual annotation to 50% and 20% in ACE and WikiEvents respectively, while achieving the same performance as with full training. More importantly, we show that recasting EAE as entailment alleviates the dependency on schemas, which has been a roadblock for transferring annotations between domains. Thanks to the entailment, the multi-source transfer between ACE and WikiEvents further reduces annotation down to 10% and 5% (respectively) of the full training without transfer. Our analysis shows that the key to good results is the use of several entailment datasets to pre-train the entailment model. Similar to previous approaches, our method requires a small amount of effort for manual verbalization: only less than 15 minutes per event argument type is needed, and comparable results can be achieved with users with different level of expertise.
## Main idea 

In their previous paper [[Label Verbalization and Entailment for Effective Zero- and Few-Shot Relation Extraction]] they have proven that the entailment was an effective way to achieve high performances on RE using a few shot and zero shot approach. The achieve those result buy converting the RE task into an entailment task trough a verbalization of the relations. But the RE dataset used : TRACED is easy to verbalized and the relation are easily visible in the context. Hence they wanted to check in this paper that the entailment appraoch still holds in a more chalenging task : Event Argument Extraction. 

## Process 

They use to dataset WikiEnvent and ACE, the goal is to learn from different sources. Their approach which is schema agnostic is easy to generalize though datasets. Then they generate positive example using their template and the known label and false argument using a random template. 

## Metric : 

They use the F1 score and the area under the curve 

## Model  
they use a ROBERTa Large with a training of 0% , 1% , 5% , 10% and 20% and 100%

## Results : 

They outperformed the exising methods by 10 points for few shots and 4 point for trining > 20 % => significative improvement (the result were hard to interprete I am not sure of the 10 and 4 points )
Time gain on the template and they shot that the template written buy a linguis achieve similar results than common templates. No more tidious annotation.  
