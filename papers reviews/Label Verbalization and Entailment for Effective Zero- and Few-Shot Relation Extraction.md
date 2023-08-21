**tag** : #Not_review  #RE  #Entailement  #Zero-shot 
**publication date** : 8 sep 21
**reading date** : 22/05/23
**link** : https://arxiv.org/abs/2109.03659
**comments** : From the Basque HiTZ institute, transform the relation extraction task as an entailment task 

---

>**abstract:** Relation extraction systems require large amounts of labeled examples which are costly to annotate. In this work we reformulate relation extraction as an entailment task, with simple, hand-made, verbalizations of relations produced in less than 15 min per relation. The system relies on a pretrained textual entailment engine which is run as-is (no training examples, zero-shot) or further fine-tuned on labeled examples (few-shot or fully trained). In our experiments on TACRED we attain 63% F1 zero-shot, 69% with 16 examples per relation (17% points better than the best supervised system on the same conditions), and only 4 points short to the state-of-the-art (which uses 20 times more training data). We also show that the performance can be improved significantly with larger entailment models, up to 12 points in zero-shot, allowing to report the best results to date on TACRED when fully trained. The analysis shows that our few-shot systems are specially effective when discriminating between relations, and that the performance difference in low data regimes comes mainly from identifying no-relation cases.

They took the [[TRACED]] dataset and convert it into an entailment task. They reformulate the relation to use a pre-build entailment model to check if the relation holds. 
They obtain "excellent" results using zero-shots or few-shots on traced

![[Pasted image 20230522121658.png]]


The get the premise that entail the hypothesis, where the premise is the relation and the hypothesis is the text, the output is an entail probability 

### Verbalization : 

They use template for each relation : 
PER:DATE_OF_BIRTH => {subj}’s birthday is on {obj}

#### NLI for inferring relations: 

The relation return is the one with the **highest** probability between all the entailment probabilities of all pairs of premises (input text) and hypothesis (template).

##### Case of the No_relation:
Two options :
- Template , {subj} and {obj} are not related 
- Threshold on the probability of all the outputs (minimal probability for a relation to hold) -> works better according to their results 

#### Data generation 

For each positive relation example they generate a neutral and negative one using random pickup templates. 
