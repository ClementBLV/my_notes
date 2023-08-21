Relation Classification as Two-way Span-Prediction

---
__tag__ :  #RC 
__publication date__: 9 oct 2020
__reading date__ : 25/05/23
__link__ : https://paperswithcode.com/paper/relation-extraction-as-two-way-span
__comments__ :  use [[QA]] to predict the span of the [[RC]]. Curent state of the art methods on TACRED and SemEval task 8 datasets

---

>**abstract**: The current supervised relation classification (RC) task uses a single embedding to represent the relation between a pair of entities. We argue that a better approach is to treat the RC task as ***span-prediction*** (SP) problem, similar to Question answering (QA). We present a span-prediction based system for RC and evaluate its performance compared to the embedding based system. We demonstrate that the supervised SP objective works significantly better then the standard classification based objective. We achieve state-of-the-art results on the [[TACRED]] and [[SemEval]] task 8 datasets.


## Principle 

Instead of the classical approach of [[RC]] they proposed an approach based on span extraction like for [[QA]]. Because classical RC often get the relation work when this relation is induced by words situated elsewhere in the sentence (not between the entities). With span prediction they forced it to extract the exact span which induced the relation. Plus they use templates to infuse knowledge of the relation.  

![[Pasted image 20230425102131.png]]

inputs : f (c, q, ea)
- c : a contest on tokenized sentenced 
- q : a querry 
- ea : is the answer : a span of the context  + out-of-sequence-span when no relation 

## Method 

For each querry they predict a span , then score this span with a learn function then take the max of those spans :
>'*'The training objective is to maximize the score the correct spans above all other candidate spans.''*

q (“where was Sam born?”) 
a span eq (“Sam”) 
a predicate rq (“where was born”)

| --- | --- |--- |
| --- | --- |--- |
| classification | frc(c, e1, e2) → r | hre = embed(c, e1, e2) | 
| span | fqa(c, eq, rq) → e (e is a span) | hqa = embed(q, c) = embed(r, e1, c) |


Like that with the span prediction the embedding contains information on the relation. 
### Several relation 

Hence if a sentence has two relation, with the classification the embedding will either have to prioritize one relation or make an in-between between the two which can downgrade the performance. 
The span classification take the relation into argument of the embedding and so is insensible to this pb.  

### Knowledge in the template

The template encoding r and e add additional information to the model
- to generalize the relation to new cases unseen 
- to add semantic information between r and e 

ex : “Who was born in X?” “Who is the parent of X?”.  --> that X is a person thank to Who which is a precious additional information


### Bidirectional question 

The choice of e1 of e2 as the subject is arbitrary and can be changed to improve the result : When is born e! ? And Who is born in e2 ? for instance

## Conclusion 

This approach achieves state-of-the-art performance in supervised settings, with the moderate cost of supplying question templates that describe the relation