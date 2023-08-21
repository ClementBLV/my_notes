
Read Me 

This project is composed of two part : 
*Part one* : Downgrading of a wordnet 
*Part two* : reconstruction of a wordnet 

## Part one : 
This task of downgrading a wordnet is handle buy two files , the synset_candidates.py which generates the candidate synset to remove and the xml_parser.py which handle the ask of removing the synset from the database.
Both code works from the command shell and have a list of arguments the user can choose : 
here an example : were we are generating a weak wordnet of a downgrading ratio of 50% related to a rich wordnet named rich_10: 

python synset_candidates.py -d '0.5' -f 'weak_50_v3' -r 'rich_10'
python xml_parser.py -w 'oewn' -n 'weak_50_v3' -s 'weak_50_10_v3.xml'

##### synset_candidate : 
The three main arguments are the downgrading ration -d , which is a float corresponding to the percentage of synset removed (-d 0.1 implies that 10% of the synset have been removed ) , the name of file under which the outputs are going to be save (-f) and the name of a reference file (-r) , this file is used to indicate a list of already removed files in another wordnet. It is important to avoid a lost of information between the donor and the receiver. You can also precise the mode, the default mode is snipper, where only a synset is removed and all its synset located further on the branch are kept. It can also be set to the cut mode where the all branch is removed.
The output is formed of two files : the first one is a txt file containing the list of all the synset to remove, the second one which is optional and is only generated when the snipper mode is used is a json file containing all the relation and how to replace them. With the snipper mode when a synset is removed the relation are replaced, the hypernyms of the removed synset become the hypernyms of its hyponyms (as if the removed synset has never existed).

##### xml_parser : 
wn library, the library to read wordnet can only read a wordnet file which consist of a xml file. To modify a xml you have to directly modify this .xml. That's the goal of the xml_parcer, it parse modify and save a new wordnet. 
The arguments are -w the source file of the original Open English Wordnet, this argument take a path toward the origin wordnet to path, if the argument is "oewn" it points directly toward the Open English Wordnet 2022. The argument -n points toward the files containing the synset list and the relations, no extensions should be added. Finally the -s indicated the name to save the file, with an extension. 

Firstly run the synset_candidate to generate the candidates, and then the xml_parser. 

## Part two : 

### Utils (get_best_path.py): 

To be easily used the wn architecture is converted in a matrix structure. All the utils methods to convert the wn architecture into more machine readable one are present in the **get_best_path.py**. 
We use np.arrays to represent the three, the first column is the origin synset (all the element of this column are the same), then the matrix got as much rows as it got children. 
For example, synset A has 3 hyponyms then the matrix representing them gonna be : [ [ A - h1] , [A - h2] , [A - h3] ]. Then this matrix can be extend to add the hyponyms of A's hyponyms, in that way you can construct all the path starting from A. For example, if h3 don't have any hyponyms the row is padding by None, eg [ [ A - h1 - h1'] , [A - h2 - h2'] , [A - h3 - None] ]
Synset object and CustomSynset are used inside the matrix

**Similarity** class, is the children class of the Utils class. All the methods using the similarity and the scoring are present in the Similarity class. The methods to rank the branches are also present in this class. 

### Find the most suitable branch : reconstruction.py

The find_best_root_v2 method in the reconstruction.py is the method to find the best branch starting from the ancestor. The common ancestor given in the output has to be a CustomSynset as those synsets have integrated methods used into the find_best_root_v2 code. 
*top_k* : is the number of branches outputted (number of rows in the matrix )
*deepness* : the length of the branch (number of column in the matrix), be careful with this parameter as it also controls the number of synset watch at each step, hence a deepness to big could cause speed problem and the deepest you go the ore synset you have to look for. 
*heuristic* : this Boolean argument decides weather or not you are using the heuristics methods of the "sure" branch for the scoring. The "leaf" and "discard" synset always gonna be used. 

The output is the top_k best branches in the form of a numpy array with the synsets inside.

### Find the position of the candidate inside the branch : recontruction_entailment.py 

This file as the goal to position the synset inside the branch. It receives the output of the reconstruction.py and position the candidate synset inside the branch. For each branch it search for the index where the candidate should be and it takes the most common position. 
cathegorized_synset : to find the relation between two synsets, either HYPERNYM, HYPONYM or None 
cathegorize_branch : replace each synset of a branch by its relation with the candidate 
cathegorize_output : find the most common position of the shifting between Hyponym and hypernym. If the relation is None the index is 10000 arbitrarily 

### Metrics 

Implementation of the MAP and MRR, the MAP is sklearn implementation and MRR is a stackover flow. It takes into input a binary input 1 if the path is correctly predict and 0 else, eg : [1, 1, 0] if the last element of the prediction is false. 

### Evaluation 

The evaluation file have two parts one to evaluate the branch prediction and the other to evaluate the entailment 

branch prediction : we predict the top_k branch from the last common ancestor to the candidate and then we use he full English wordnet to predict all the path from the common ancestor, we then check that all the predicted paths are in the golden, if one path as been wrongly predicted we assign a 0 else its a 1. 

entailment evaluation : we artificially create branches from the original wordnet and then remove a synset from this branch. Then we try to insert back this synset using the model. 


## Dependences 

- wn to read the wn
- Python 3 with NumPy
- 