__*name*__   : [PseudoReasoner: Leveraging Pseudo Labels for Commonsense Knowledge Base Population](obsidian://open?vault=my_notes&file=papers%20reviews%2FLeveraging%20Pseudo%20Labels%20for%20Commonsense%20Knowledge%20Base%20Population)
__tag__ : #KB_Population , #Pytorch 
__*publication date*__ : 14 oct 22
__*reading date*__ : 
__*link*__ : https://paperswithcode.com/paper/pseudoreasoner-leveraging-pseudo-labels-for
__*comments*__ : propose un systheme de teacher student where a KB is used as a teacher and (eg the model has beem trained on other CSKB) and the teacher propose labels on an unseen dataset for the student to learn 

>__abstract__ : Commonsense Knowledge Base (CSKB) Population aims at reasoning over unseen entities and assertions on CSKBs, and is an important yet hard commonsense reasoning task. One challenge is that it requires out-of-domain generalization ability as the source CSKB for training is of a relatively smaller scale (1M) while the whole candidate space for population is way larger (200M). We propose PseudoReasoner, a semi-supervised learning framework for CSKB population that uses a teacher model pre-trained on CSKBs to provide pseudo labels on the unlabeled candidate dataset for a student model to learn from. The teacher can be a generative model rather than restricted to discriminative models as previous works. In addition, we design a new filtering procedure for pseudo labels based on influence function and the student model’s prediction to further improve the performance. The framework can improve the backbone model KG-BERT (RoBERTa-large) by 3.3 points on the overall performance and especially, 5.3 points on the out-of-domain performance, and achieves the state-of-the-art. Codes and data are available at https://github.com/HKUST-KnowComp/PseudoReasoner 

Common Sence knowledge Base (CSKB) store knowledge, like [[ConceptNet]] , [[ATOMIC]], [[GLUCOSE]] those KB are not lexical, they reference properties of object, causes and consequences of actions, emotions of humans ... 

__CSKB Completion__ : add new edges/assertions from INSIDE the CSKB (close world )
__CSKB Population__ : add new edges/assertions from OUTSIDE the CSKB

In the paper they use the 3 CSKB of before (which have been aligned) to populate the [[ASER]] dataset.

They use a teacher and a student, the teacher which has been trained on the source data and this model is used to proposed "pseudo labels" to the student for the unlabeled candidates. The student is then fine tune to only keep relevant labels from the pseudo label proposed by the teacher (only the one with a probability score high enough) . 
**teacher** : [[KB-BERT]] or [[GPT-2]] (COMET)
**student** : KB-BERT
Pseudo label : used in semi supervised system, limit human annotation 
![[Pasted image 20230503110249.png]]

---
__task__ : given a labelled KB D_l and an unlabeled KB D_u use D_l to label D_u. Use D_l to predict the plausible triplet (head, relation, tail )

---
backbone model : KG-BERT

	1. they use the pattern <CLS> tokenized head,  <SEP> r <SEP>,  tokenized tail
	2. Feed this pattern to a BERT based and keep the <CLS> as the representation of the triplet
	3. cross entropie loss to differentiate positive of negtive triplet 

__results__ : They improve the benchmark by 5 to 6 points, in averall KB-Bert performs better but GPT2 adapts better to the new knowledge 