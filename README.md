# Neural_Network_Charity_Analysis
M19

## Overview of the analysis
The purpose of this analysis is to establish neural networks that is capable of predicting weather applicants will be successful if funded by Alphabet Soup. The data used for training and testing the model contains more than 34,000 organizations that applied and were approved.

## Results
### Data Preprocessing
- _Q1: What variable(s) are considered the target(s) for your model?_

A1: Column `IS_SUCCESSFUL` is considered the target for the model.

- _Q2: What variable(s) are considered to be the features for your model?_

A2: `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, `ASK_AMT` are considered to be the features.

- _Q3: What variable(s) are neither targets nor features, and should be removed from the input data?_

A3: `EIN` and `NAME` are neither targets nor features. They should be removed from the input data.

### Compiling, Training, and Evaluating the Model
- _Q4: How many neurons, layers, and activation functions did you select for your neural network model, and why?_

A4: Initially, the model used 100 neurons on the first hidden layer and 50 on the second hidden layer. The activation function was “relu”. 

The selection of number of neurons on the first hidden layer is based on recommendation of 
> “A good rule of thumb for a basic neural network is to have two to three times the amount of neurons in the hidden layer as the number of inputs.”

Used “relu” because it is the most used activation function, which is worth to be examined first.

![deliverable_2_nn_summary](https://user-images.githubusercontent.com/78275082/125199780-d800b080-e235-11eb-94e8-fddf6fb64ef7.png)

(_figure 2.1: Initial Neural Networks Summary_)

![deliverable_2_nn_result](https://user-images.githubusercontent.com/78275082/125199852-231ac380-e236-11eb-8a5f-d51270572632.png)

(_figure 2.2: Initial Model Performance_)

- _Q5: Were you able to achieve the target model performance?_

A5: After the initial model run, two more attempts were made to improve the accuracy of the model to be higher than 0.75. The target accuracy is achieved after the second attempt.

- _Q6: What steps did you take to try and increase model performance?_

A6: In the first attempt, `Keras Tuner` module was used to test more activation functions, neurons and layers. Activation functions tested are: 'relu','tanh','sigmoid','selu','softmax','softplus','softsign','selu','elu','exponential'. The result was not satisfying, the best accuracy found by the `keras_tuner` only achieve 0.727. This is slightly better than the initial neural network.

![deliverable_3 1_nn_summary](https://user-images.githubusercontent.com/78275082/125199934-7db41f80-e236-11eb-8028-9951589ce50a.png)

(_figure 3.1.1: First Attempt Model Summary_)

![deliverable_3 1_nn_result](https://user-images.githubusercontent.com/78275082/125199937-80167980-e236-11eb-9bb4-2db17a4bbc75.png)

(_figure 3.1.2: First Attempt Model Performance_)

In the second attempt, outliers in `ASK_AMT` column were removed. The upper boundary is set at 75 percentile + 1.5 x IQR. After the outliers being removed, `keras_tuner` was used again to find neural networks that provide highest accuracy. The result shows that the best accuracy is higher than the 0.75 target.

![deliverable_3 2_nn_summary](https://user-images.githubusercontent.com/78275082/125199998-d5eb2180-e236-11eb-8eb7-4c2990fd8f8e.png)

(_figure 3.2.1: Second Attempt Model Summary_)

![deliverable_3 2_nn_result](https://user-images.githubusercontent.com/78275082/125200000-d84d7b80-e236-11eb-8fd7-c998d50cda6b.png)

(_figure 3.2.2: Second Attempt Model Performance_)

## Summary
The analysis shows that after removing the outliers in the `ASK_AMT column`, which are values higher than 11,855, neural networks can achieve accuracy of 0.7543 and loss of 0.5299. The recommended neural networks for this analysis is summarized in the _figure 3.2.1_ above.

Other than using neural networks model, random forest classifiers are worth to be tried on the analysis. The analysis of using a random forest classifier shows accuracy of model at 0.7528. Even though it is less accurate than the neural networks recommended above, this random forest classifier is faster to be trained, which makes it more convenient to be used for a quick and brief analysis.

![deliverable_4_rf_result](https://user-images.githubusercontent.com/78275082/125200070-39754f00-e237-11eb-8bb5-ae35e5b6608f.png)

(_figure 4: Random Forest Classifiers Performance_)

