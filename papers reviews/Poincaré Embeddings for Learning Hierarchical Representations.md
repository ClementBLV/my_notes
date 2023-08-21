
## Paper review 

TODO 

## Implementation of the code [here](https://github.com/facebookresearch/poincare-embeddings/tree/main) : 


for the data creation which is a csv containing the closure you can find it [here](https://github.com/facebookresearch/poincare-embeddings/blob/main/wordnet/transitive_closure.py) it is this .csv which is then fed to the model. They use **NLTK** in the whole implementation. 
Then if you lunch the file _train-nouns.sh_ and change the path with the custom closure, it might works, as the file preproduce the MAP result of the paper. But how do they reconstruct the WN to have the MAP result ? They obtain their results only working with nouns as we do. 
For their evaluation they take a set of positive relation and negative relations and they rank the score of the Poincaré embedding on the the given relation compared to the 10 negatives ones, in the code they call them. I think for each synset they have a set of n "close" synset according to the model, and they rank the index of the real "neighbor" as they called them compared to the "not" neighbor present in the set.
