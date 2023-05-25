# deep-learning-challenge Report

Overview

The goal of this project is to create a model for the foundation Alphabet Soup that can help select the applicants most likely to have success. Data for creating models was provided by Alphabet Soup as a csv file located in the Resources file under charity_data.csv. For a successful model it must be more than 75% accurate.

Before a model could be created, the data need to be cleaned and fitted using a StandardScaler.
•	EIN and NAME need to be dropped
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/6554fd95-159f-4757-a704-cebe29fe5b2c)

•	All APPLICATION_TYPE that where under 500 were placed into a new value called Other to simplify the data. The same was done for CLASSIFICATION values that where under 1000.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/8acb53cc-9d69-4681-8ab1-87ca184029bc)
![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/fe1036f1-31de-4490-91a1-4e428165d2c3)
 
•	Catergorical data is converted using get_dummies
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/926f2242-bd9f-491c-8ccf-7a29328d6014)

Now that the data is cleaned and fitted a model is ready to be made.
•	X and y are split on IS_SUCCESSFUL and training and testing dataset is created and scaled.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/1c8aa472-5f9e-4c75-952d-34b3161c845a)

•	The first model is created using two hidden layers. The first layer uses 80 units. The second layer uses 30 units and both use relu as the activation. Output layer is made with 1 units and sigmoid is the activation. The model is compiled and the model is trained and run with 100 epochs.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/19f15054-9d73-4496-a82d-b9e89b513e44)

•	Model is tested for accuracy and the model is saved as file named AlphabetSoupCharity.h5. The model is only 72.86% accurate so changes need to be made to the model.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/9dcc5469-d03f-406c-827e-36e4ce6c191e)

Three attempts where made by the creator to try and achieve a model that is better then 75%
•	Attempt one added another hidden layer the same as the second layer in the previous model with 30 units and relu as the activation. Attempt one model is still only 72.9% accurate.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/fcb978f8-2815-4caf-8f49-4fd2727976f8)
![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/d99ae396-900a-4e18-ba10-272bf3df549d)
 
•	Attempt two added two more hidden layers the same as the second in the original model. Attempt two model is a massive failure at 45.94% accurate.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/1b2f02d0-a290-431a-b46d-8f0d9c0e1584)
![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/235e9614-dd12-4b5f-b277-a2165e9abf41)
 
•	Attempt three model has massive changes after the large drop of from model two. Model three is the same as model one with tanh replacing relu as the activation. Attempt three model is 72.93% accurate.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/0dc0590d-759d-4f0e-8f8f-0f6be0e9242d)
![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/2220799c-cc44-4abd-98f6-4eab1e770447)
 
All models fail to reach the minimum threshold of 75% accuracy, so a better model needs to be made. For that reason a neural network model needs to be created.
•	Kerastuner is installed into the model. neural network model is made with activation choices being relu, tanh, and sigmoid. Kerastuner is added to the model with min value set at 1 and max value set at 90 for neurons for the first hidden layer. All other hidden layers are set at range of one to five hidden layers with units ranging from 1 to 30. Output layer is set at one units and activation equal to sigmoid.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/8817bb72-03f0-454b-b929-3b225a378dd1)

•	Kerastuner model is run to find the best model to use to get an accuracy of over 75%. Kerastuner returns best model only returning 73.39% not achieving the goal of 75%. best model is saved as AlphabetSoupCharity_Optimization.h5.
 ![image](https://github.com/Tsmoore002900/deep-learning-challenge/assets/119066378/11bd111b-bddc-4ed6-90b0-beb242b0deb6)

Summary

The summary of the project is that no models where created the where better than 75% accurate. The best model attempt three only reaching 72.93%, and a Failed Kerastuner model only reaching 73.39%. The conclusion I reach is that the data needs to be recleaned and scaled to make a better model. When get_dummies is run on column INCOME_AMT it breaks this columns into to many pieces of data. This should be switched to if the value is equal to 0 it should equal true if not false. Creating all values equal to 0 being marked as 1 and any other value equaling 0. This should simplify the INCOME_AMT data down to one column allowing for a better model to be made. 

