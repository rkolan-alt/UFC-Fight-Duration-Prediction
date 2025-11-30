
# 🥋 UFC Fight Duration Prediction

This project predicts the amount of time a UFC fight lasts. This will be done using machine learning techniques.  

---

## 🔍 Problem Overview

On betting apps such as Draftkings, fans can predict on specific details of a UFC fight including how long it would last. This model would aim to assist them in the prediction of the amount of time a fight would last. 

The goal: To create a model that predicts the amount of time a UFC fight lasts to assist fans with betting. 

---

## 🧠 Thought Process

When thinking about what kind of machine learning task to pursue upon looking at the dataset, I knew I wanted to predict something which isn't obvious, predicting the winner of each fight, and is a useful feature to predict on as it can assist tasks such as sports betting. Hence I determined the fight duration to be the target of the dataset. I wanted to precict the duration in seconds as it would give a precise prediction and help the user truly understand how long into a round the fight could end. 

---
## 📊 Data Preprocessing and Feature Engineering

After loading the dataset, I immediately converted the duration of the fight into seconds in order to obtain the target variable. Before exploring the dataset, I wanted to know if the career stats of each fighter in each fight were accurate at the time of their fight. When I explored that, it turned out that the career stats of each fighter were the same across all their fights which wasn't accurate at all. 
<img width="1299" height="612" alt="image" src="https://github.com/user-attachments/assets/77039a50-7c8d-452e-aca1-37df42e98d9c" />

Hence, I came up with a method that corrected these stats and made them accurate to the fight. The main downside of this method unfortunately was its huge runtime due to the size of the dataset. 
<img width="1003" height="736" alt="image" src="https://github.com/user-attachments/assets/b4e59f5c-2dfe-44da-b577-5922c28b9156" />

Through this method, I was able to also perform feature engineering and come up with other new features using my domain knowledge as it took the averages of the stats in each fight for each fighter respectively. I didn't really find any of the categorical features such as the referee or the stance of the fighter to be a contributing factor to the duration of the fight due to which I couldn't implement one hot encoding which I would've been interested in. 

---
## 🤖 Machine Learning 

Finally, after obtaining the data which I needed, I was ready to perform machine learning tasks. I split the main dataset into a dataset with 3 round fights and a dataset with 5 round fights. These are the 2 types of fights in the UFC and it wouldn't make sense to use data from 5 round fights to predict the duration of a 3 round fight. After using ChatGPT for assistance on which models to use, I settled upon performing a regression task through LightGBM. LightGBM was a suitable model as it is mainly used for tabular data like the dataset I am working with. 

When I used the model however, my predictions were quite inaccurate. 
<img width="668" height="664" alt="image" src="https://github.com/user-attachments/assets/298104fa-c7af-44e5-92ee-c46c888f97b1" />

The root mean squared error was over 300, which is basically a whole round off. Predictions being inaccurate by a whole round are not helpful for sports betting whatsoever. I tried to improve the performance of the model through further feature engineering through based on the features with the most gain. 
<img width="1096" height="623" alt="image" src="https://github.com/user-attachments/assets/c60f3a0c-301b-4e3a-98ac-74a7b829314e" />

In this case, I took the average fight time of both the fighters and averaged them out to obtain the combined average time.
<img width="1091" height="611" alt="image" src="https://github.com/user-attachments/assets/6698443a-eea5-4df9-af0b-674caca6a826" />

However, this only resulted in an improvement of 10 which doesn't make much of a difference in the quality of the predictions. After assessing the distrubution of the target values, I realized that the poor performance could've been attributed to the heavily skewed dataset, as there are many fights that went to decision due to which there are a ten of 900 second fights. This is what led to inaccurate predictions. 
<img width="674" height="533" alt="image" src="https://github.com/user-attachments/assets/39c4888f-b6e4-4a4d-861f-c482de44c934" />

I could've implemented hyperparameter tuning to improve the model but I didn't know how to implement it in order to avoid adsurdly long runtimes. Also, my knowledge of the parameters in the algorithm was weak. Hence I decided to pause the project here and take the Machine Learning Specialization from coursera to imrpove my understanding of the models and machine learning in general. 

Upon finishing 2 courses in the specialization, I was able to gain a good understanding on the basic fundamentals of machine learning, such as supervised vs unsupervised learning, overfitting, underfitting, etc. I was also able to gain an in-dept understanding of the models. I really liked Neural Networks and I wanted to find a way to implement it in this project. Hence I decided to switch to a classification task where I predicted the number of rounds as the measurement for the duration of the fight rather than the seconds. Through implementing neural networks, I have seen an improvement in the predictions as I was able to get a 60 percent accuracy on the test data upon my first attempt. 
<img width="862" height="258" alt="image" src="https://github.com/user-attachments/assets/244014e3-5772-4be0-8524-b029e9313d3b" />
<img width="450" height="406" alt="image" src="https://github.com/user-attachments/assets/b7d606d1-c62f-4920-aeec-f75740ebe4ab" />

However, I realized there was slight underfitting because the accuracy on the training data was only 62 percent. Hence, I decided to implement a bigger neural network through which I say a 1 percent increase in training accuracy, but a 1 percent decrease in test accuracy. Through the specialization, I also learnt about data augmentation where generating samples of training data which are less present, can improve model performance and help with overfitting. I wondered how this impact the performance of the model given that it was starting to overfit. Once I implemented it however, the model performance become much worse leadning to drastic overfitting. There was a 10 percent improvement in training accuracy, but a 10 percent decrease in testing accuracy.
<img width="608" height="294" alt="image" src="https://github.com/user-attachments/assets/d57c6e78-4048-44dc-b6fd-5cc2f4cc067c" />

I was genuinely caught off-guard by this and was really confused as to why this happened. I expected some improvement in the model performance only to see this. This also means that there is so much more for me to learn in the field of machine learning. I like that I am seeing things I am not expecting as this would only help me become more knowledgeable in this field. 

Overall, I think it would be quite challenging to obtain accurate predictions in the UFC because of the unpredictable nature of the sport. Regardless, I am glad that I was able learn a lot through this project. 
