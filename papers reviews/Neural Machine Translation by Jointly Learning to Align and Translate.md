Neural Machine Translation by Jointly Learning to Align and Translate

---
__tag__ : #Translation 
__publication date__: 19 May 2016 
__journal__: ICLR
__reading date__ : 27/04/2023
__link__ : https://paperswithcode.com/paper/neural-machine-translation-by-jointly
__comments__ : Use encoder decoder technique it is a different approach than Statistical Machine Translation [[SMT]] 

---
>__abstract__: Neural machine translation is a recently proposed approach to machine translation. Unlike the traditional statistical machine translation, the neural machine translation aims at building a single neural network that can be jointly tuned to maximize the translation performance. The models proposed recently for neural machine translation often belong to a family of encoder-decoders and consists of an encoder that encodes a source sentence into a fixed-length vector from which a decoder generates a translation. In this paper, we conjecture that the use of a fixed-length vector is a bottleneck in improving the performance of this basic encoder-decoder architecture, and propose to extend this by allowing a model to automatically (soft-)search for parts of a source sentence that are relevant to predicting a target word, without having to form these parts as a hard segment explicitly. With this new approach, we achieve a translation performance comparable to the existing state-of-the-art phrase-based system on the task of English-to-French translation. Furthermore, qualitative analysis reveals that the (soft-)alignments found by the model agree well with our intuition.


## Encoder Decoder method 

The other method apart from SMT is buy using an encoder-decoder system. In this case they are two possibilities to use it. 
*First method :* encoder-decoder couple for each language 
*Second method :* encoder specific to a language applied to each sentence and the outputs are compared
A decoder take the encoded vector and output a translation 

---> jointly trained to maximized the performances 

input sentence > ENCODER > **fixed length vector** > DECODER > output  

The pb is that the encoded vector need to encode the input in a fixed length vector : no matter the size of the input sentence :
=> works better for short sentences (. Cho et al. (2014b))

## Method 

They add a module which align and translate jointly. 
When a word is predict, the model search into the input sentence to find the area with the most relevant info and use this context to propose a candidate. 
Hence it doesn't encode the whole sentence into a fixed length vector ! It encode it into a set of vectors >> The information is not compressed. 

Two [[RNN]] for encoding and decoding 

## [[Translation]]

**Old Architecture**

The goal of MT is to maximize the joint probability : p(y|x) with y the translated sentence and x the input sentence. 

***Encoder:*** each step ht = f (xt, ht−1)   ( xt input and ht-1 previous hidden state, f and q non linear functions   ) 
=> *output* : c = q ({h1, · · · , hTx })

***Decoder :*** trained to predict p(yt | {y1, · · · , yt−1} , c) = g(yt−1, st, c) with yt predicted word and st the hidden state of the decoder 

**Proposed Architecture**

Here they use the following formula p(yt |y1, . . . , yt−1, x) = g(yt−1, st , ct ) 
We can see that ct changes at each step/target word yt st = f(yt−1, st−1,  ct).
ct = SUM( alpha * hidden states )  ( where alpha are obtain by combining the previous states s and h ) and it corresponds to the **alignment** part ( ~ feed forward neural network )

![[Pasted image 20230427115306.png]] 
(here they use a biRNN)

= A mechanism of attention in the decoder which decides on which part of the source it should take attention.

## Result 

They  use the parallel corpora of [[ACL WMT ’14]] and [[BLEU]] as an evaluation metric. 
There method strongly outperform simple enc-dec for long sentences and have the same performances 