Are a Type of [[Transformer]] 

*source* : 
*videos*: [theorie](https://www.youtube.com/watch?v=tRQ0EaqeJAI&t=1s) [theroie and implementation](https://www.youtube.com/watch?v=j3VNqtJUoz0)
*paper* : [An Image is Worth 16x16 Words : Transformer for image recognition at scale]

Vision Transformer are an extension of transformer for visual data. They only use the encoding part as the decoding part is mostly use for sequence prediction. 

## Embedding : 

The goal is to project similar information into similar area of the hyperspace.
But transformer only take sequence into input, so : How to transform an image into a sequence ? 
With images the trick is to use patching techniques to cut the image according to a grid. Then each element of the grid is taken one by one and transformed in an embedding. Usually it done by taking each pixels as vectors and pass them through a CNN. Then the embedding is fed to the transformer. Or take each channel (RGB) and process each one independently 

To know the position of the patch image inside the original image you use positional encoder. Its important because the attention part is position independent, so you need to add the position to have it took into consideration. 


(usually you use einops to process the image)

## CLS : 

represented in blue on the figure 
Randomly initialized, it's a feature vector which represent the whole image 

![[Pasted image 20230929185940.png]]![[Pasted image 20230929191713.png]]

## CNN vs ViT 

![[Pasted image 20230929192010.png]]

Can generate an attention map were important inforamtion is hold insde an image![[Pasted image 20230929192131.png]] 

## Extension 

Swin transformer, which use windows instead of padding 