The reset architecture which lead to the [[Transformer]] architecture is a powerful type of network which achieve huge deepness without any lost of information. 
introduced in 2015 ["Deep Residual Learning for Image Recognition"]()
*source* : [Youtube video](https://www.youtube.com/watch?v=Q1JCrG1bJ-A)
## Deepness and noise 

The problem of really big network is that each time you add a new layer you add noise at the initialization. Because you randomly initialized the  hidden layer. Hence imagine a NN of more than 100 hidden layer, at the end, the output is so noisy that all the info from the input layer is now lost. In the same was when you do the back propagation the difference between the output ant the truth is to big to correctly back-propagate info, an the info which come back to the input layer as nothing of the last layer anymore. 
In a nutshell the Big Networks struggle to handle all the layer and fit them correctly. This led to an extremely slow decrease of the loss during each steps. On the other end if a network is too shallow it struggles to achieve high performances. 


## The solution of ResNet 

ResNet achieve high performance on super deep networks and are an efficient solution against vanishing gradient. Its trick is to keep information from the previous layers by adding some "skip channels" were information from the input is add to information of the output. Hence the model has to learn the residual (output of the layers) and the input $$ y = F(x)+x $$
Those **skip connections** are preset throughout all the network. (Figure 1)

There are two building blocks (Figure 2) 
- **Convolutional Path** : (Main Path) series of convulutional layer with a small kernel = goal learn information 
- **Identity Path** : (Shortcut) add the infoation transformed by the convolutionnal layer to the original input data in ordoer to keep information

Back-propagation: the gradient decent is really effective due to the shortcuts 

The stacking of addition : As we don't wont the size of the hidden layer to be conditioned by the size of the the input layer the size of the output might be different to the one of the input. So how to add information ? Try to use consistent shapes to be able to add them. 
Concatenation causes an issue ass it increase the size of a vector and so the number of parameters. 



## Achievement : 
Get a better loss than the shallow notwork and get it way faster (less epochs) than the other shallow deep neural networks 





![[Pasted image 20230929171211.png]]![[Pasted image 20230929171300.png]]