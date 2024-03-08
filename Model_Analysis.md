## Neural Network Model Analysis

# Overview

The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. Using machine learning and neural networks, I used the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

The dataset provided cotained records for more than 34,000 organizations thathave received funding from the foundation,

# Results

Data Preprocessing

The data was first processed to prepare it for use in a neural netweork binary classifier model. The target feature was "IF_SUCCESSFUL" which shows if the awardee used the funding reeived effectively

The large dataset contains a number of features that may be used in any model. They are summarized in the list below;

EIN and NAME—Identification columns
APPLICATION_TYPE—Alphabet Soup application type
AFFILIATION—Affiliated sector of industry
CLASSIFICATION—Government organization classification
USE_CASE—Use case for funding
ORGANIZATION—Organization type
STATUS—Active status
INCOME_AMT—Income classification
SPECIAL_CONSIDERATIONS—Special considerations for application
ASK_AMT—Funding amount requested

I removed the EIN and NAME columns from the analysis.

Compiling, Training, and Evaluating the Model

For the initial running of the TensorFlow neural network model, I used a two hidden layer model with 80 and 30 neurons respectively. This model achieved an accuracy of 0.7242 which was slightly below the target accuracy of 0.75. 

To examine if the target accuracy could be achieved, three attempts were made to optimize the model. Theres are summarized in the table below

| Attempt # | Epochs | Hidden Layers | Neurons (per Layer)  | Accuracy | Features                    |
| --------- | ------ | ------------- | -------------------  | -------- | --------------------------- |
| 1         | 100    | 2             | (1) 80 (2) 30        | 0.6638   | Removed four more features  |
| 2         | 300    | 2             | (1) 80 (2) 30        | 0.7251   | Original features           |
| 3         | 300    | 3             | (1) 60 (2) 20 (3) 20 | 0.7263   | Original features           |

In addition, a Keras Autotuner was applied to the data, which cycled through a wide variety of hidden layers, numbers of nodes and activation functions. None of the these resulted in an accuracy above the target accuracy of 0.75.


# Summary

In summary, the most accurate model found here (0.7263) consisted of three hidden layters with 60, 20 and 20 neurons repspectively, run over 300 epochs.

I would recommend investigating if the features in the collected data are true predictors of success. For example, it might be useful to collect data on how well each organization used funding from other sources.

I would also recommend considering a Logistic Regression model as an alternative to the TensorFlow neural network used here. I ran a Logistic Regression on the same data (see file AlphabetSoupCharity_Logistic_Regression.ipynb). This model achieved an accuracy (0.7195) similar to that of the neural network model (0.7263) but took less time to run with no need for tuning of hyperparameters. Logistic Regression models are also generally considered to be more interpretable theat neural networks which would make the model operation easier to explain to various stakeholders.  

