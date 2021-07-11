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
