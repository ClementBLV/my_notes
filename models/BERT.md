>For BERT, we used the model named “bert-largecased” of the PyTorch implementation3 , which consists of vectors of dimension 1024, trained on BooksCorpus and English Wikipedia. Due to the fact that BERT’s internal tokenizer sometimes split words in multiples tokens (i.e. [“rodent”] becomes [“rode”, “##nt”]), we trained our system to predict a sense tag on the first token only of a splitted annotated word. For the Transformer encoder layers, we used the same parameters as the “base” model of Vaswani et al. (2017), that is 6 layers with 8 attention heads, a hidden size of 2048, and a dropout of 0.1. Finally, because BERT already encodes the position of the words inside their vectors, we did not add any positional encoding.



----
## Model ID 
date of creation 
paper 
model type 
mother model : None 
number of parameters :

**Schema**

---
