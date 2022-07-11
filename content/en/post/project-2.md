---
date: 11 jul 2022
description: "build chatBot with NLP "
featured_image: "/images/pj2.png"

title: "Project 2: ChatBot Tunisien"
---

1-pipeline:

•tokenize lines (split lines into words in the same list)

•eliminate duplicated words and word have same sense  with lemmatizer

•Preparing data by transforming words in the list into numerical values, create the bag of words (exemple :
Our list after tokenize ->[hi, bye, I, will, go, eat, play, too, football, see, u, watch, champions, league] ->length=13
Line 1-> hi, I will go to eat 
	   [1,0,1,1,1,0,1,0,0,0,0,0,0]->same length: refer to eat tag
       
Line 2 ->I watch champions league
        [0,0,1,0,0,0,0,0,0,0,1,1,1]: refer to football tag
)

•initialize a training set with features are bag of words, and labels are tags (classes)  (word embedding  is  bag of words+ ref labels)

•Build the  recurrent  neural network:  
dense_layer(128)->activation function: relu ->dropout (0.5) -->dense_layer(64)->activation function: relu ->dropout (0.5)
-->Dense layer (len (labels or y)) ->activation function softmax 

2-training and evaluation : 

•Loss function categorical cross entropy 
Optimazer: stochastic gradient descent with low learning rate
Metrics accuracy for evaluation ==>accuracy=97% for 200 epochs 

•Predict class of the message, but first we must clean up the line that we would predict 
 With same 3 first instructions in the pipeline to make it comprehensible for the model (normalize data to predict)

3-deploy  in one function i called predict in view.py  with django 


{{< figure src="/images/pj2.png">}} {{< figure src="/images/pj22.png">}} {{< figure src="/images/pj23.png">}}


[Link To GitHub Repository](https://github.com/AliSaidiPortfolio/ChatBotTunisien)

