For a ranking task the metrics are not simply, Recall and Precision as you have to evaluate the quality of the outputs items : is their order correct, are there intruder, is the element correct at the correct rank ... To resolve and evaluate such models different metric exist : 

## I- Recall@k , Precision@k

#### Recall and Precision reminder 

#### Recall@k 

#### Precision@k : 

The percentage of item which are correct in the topK. Concern if we are good at finding things. The fraction of the k recommendation that are good, can be use to evaluate the threshold of k. 

## II - MRR - *Mean Reciprocal Rank*

It goal is to measure where is the first relevant item (should be in 1 in the ideal case). For each ranking we get the index of the first relevant item and we sum the inverse of the position of this item. Ex for user 1, the first relevant item is in position 3 so in the sum it is 1/3 which appeared. The overall sum is then normalized by the total number of items.  

![[Pasted image 20230706104550.png]]

Pros : Relevant to measure the performance of the question : "What is the best blabla ?" 
Cons : Does not evaluate the quality of the rest of the list, a list such as - Good - Bad - Bad would have the same score as Good - Good - Good even is the second list has a highest quality. 


## III - MAP - *Mean Average Precision*

Measure the quality of the whole outputted information . Penalize greatly when the wrong output are located at the beginning of the list, and less if the wrong don't have a high score. A high quality list is a list were the most of good elements are located high in the list. 

![[Pasted image 20230706105401.png]]

A perfect list would be Good - Good - Good, hence (1/1 + 2/2 + 3/3)/3 = 1, and the farther the good element is the smaller is the precision = 1/ big-rank, and so the average of the precision is also small that correspond of the average precision AP for one prediction then average all those result to get the Mean of the Average Precision. More detail in this course : [here](https://www.youtube.com/watch?v=yjCMEjoc_ZI)  for the generation of the MAP curve 

Cons : It has to be a binary decision , the item is good or bad, does not handle a grade system for the quality of the answer for those pb use # Normalized Discounted Cumulative Gain


## Implementation 



Sources : 

https://medium.com/swlh/rank-aware-recsys-evaluation-metrics-5191bba16832
