tag : #WordNet  #KB_Population  
publication date : 20 Jun 2017
reading date : 19/09/2023
link : https://arxiv.org/pdf/1706.05674.pdf
comments : Wordnet population with GNN - out of the bow population

---

>**abstract** :  Knowledge base completion (KBC) aims to predict missing information in a knowledge base. In this paper, we address the out-of-knowledge-base (OOKB) entity problem in KBC: how to answer queries concerning test entities not observed at training time. Existing embedding-based KBC models assume that all test entities are available at training time, making it unclear how to obtain embeddings for new entities without costly retraining. To solve the OOKB entity problem without retraining, we use graph neural networks (GraphNNs) to compute the embeddings of OOKB entities, exploiting the limited auxiliary knowledge provided at test time. The experimental results show the effectiveness of our proposed model in the OOKB setting. Additionally, in the standard KBC setting in which OOKB entities are not involved, our model achieves state-of-the-art performance on the WordNet dataset. The code and dataset are available at https://github.com/takuo-h/ GNN-for-OOKB.

The OOKB deals with the insertion of an out of the box node at the right position. The idea of using a GNN is to avoid to retrain the all graph when new entities are added. 
The train the model to predict the link in a form (h , r , t)
