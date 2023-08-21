## Principle

The goal of RC is to read a text and only keep the pair of entities e1 and e2 between which the relation holds. 
Inputs : *(s, e1, e2, r)*
- a sentence 
- two entities span 
- (know all the possible relations types)
Output: 
- classify between all the relation and no_relation possibilities

Common Dataset : [[TRACE]]

## Training 

The goal is to embed the sentence and the sentence into vectors and then classify those vectors: 
The goal of this training is to learn to embed vectors in spacer spaces where the relation or disjoin.

Hence it is a multiclass classifier between all the relation plus the empty relation 

The embedding used pretrained masked language model like [[BERT]] or [[RoBerta]]

PB it often classified the sentence without looking at the entities 