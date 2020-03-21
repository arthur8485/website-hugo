---
title: LSTM Day1
date: 2020-03-21T19:39:42+08:00
lastmod: 2020-03-21T19:39:42+08:00
author: Author Name
categories: ["category1"]
tags: ["tag1", "tag2"]
# showcase: true
draft: false
---

#### Before introducing Long short-term memory(LSTM), here, Recurrent Neural Networks(RNN) should be known !

## Recurrent Neural Networks

#### The original neural networks can't act like human. Instead of start thinking from scratch , you can surely    understand
####  the meaning of essay from every single word or patterns rather than forgetting all thoughts and restart 
####  your thinking from scratch ------ persistence. 


<!--more-->

## LSTM networks

#### Long shot-term memory is based on RNN model, which can learn long-term of dependencyies. LSTMs are explicitly 
#### designed to avoid the long-term dependency problem. Remembering information for long periods of time is practically 
#### their default behavior, not something they struggle to learn!

#### All recurrent neural networks have the form of a chain of repeating modules of neural network. In standard RNNs, 
#### this repeating module will have a very simple structure, such as a single tanh layer.


### To be continue.....

```python
import pandas as pd
import numpy as np
from sklearn.preprocessing import StandardScaler, OneHotEncoder, LabelEncoder
from keras.models import Sequential
from keras.layers import LSTM, Dense,Dropout, CuDNNLSTM
import numpy as np



df = pd.read_csv("D:\\python\\Lottery\\winning_number\\combined\\combined.csv")
data = df.iloc[:,1:21]

scaler = StandardScaler().fit(data.values)
transformed_dataset = scaler.transform(data.values)
transformed_df = pd.DataFrame(data=transformed_dataset, index=data.index)



number_of_rows= data.values.shape[0] #all our games
window_length = 10 #amount of past games we need to take in consideration for prediction
number_of_features = data.values.shape[1] #balls count
train = np.empty([number_of_rows-window_length, window_length, number_of_features], dtype=float)

label = np.empty([number_of_rows-window_length, number_of_features], dtype=float)
for i in range(0, number_of_rows-window_length):
    train[i]=transformed_df.iloc[i:i+window_length, 0: number_of_features]
    label[i]=transformed_df.iloc[i+window_length: i+window_length+1, 0: number_of_features]


batch_size = 25
model = Sequential()
model.add(LSTM(128,      
           input_shape=(window_length, number_of_features),
           return_sequences=True))
model.add(Dropout(0.2))
model.add(LSTM(128,           
           return_sequences=False))
model.add(Dropout(0.2))
model.add(Dense(number_of_features))
model.compile(loss='mse', optimizer='rmsprop', metrics=['accuracy'])

model.fit(train, label,
          batch_size=64, epochs=10000, validation_split=0.1)
model.save("C:\\Users\\arthu\\Desktop\\train2\\RNN.model")

```



Reference: 

##### [[1] 理解LSTM网络 Kavin_Liang](https://blog.csdn.net/shinanhualiu/article/details/49864219)
##### [[2] Understanding LSTM Networks](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)