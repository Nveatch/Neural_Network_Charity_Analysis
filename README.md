# Neural_Network_Charity_Analysis

## Overview of Project

### Purpose
The purpose of this analysis was to use a deep neural network to analyze a charity dataset, and create a binary classifier that is able to predict if applicants will be successful if funded by Alphabet Soup


## Results

### Data Preprocessing

**What variable(s) are considered the target(s) for your model?**

* IS_SUCCESSFUL, the binary classifier that says if the funding was successful or not


**What variable(s) are considered to be the features for your model?**

* APPLICATION_TYPE

* AFFILIATION

* CLASSIFICATION

* USE_CASE

* ORGANIZATION

* STATUS

* INCOME_AMT

* SPECIAL_CONSIDERATIONS

* ASK_AMT


**What variable(s) are neither targets nor features, and should be removed from the input data?**

* EIN

* Name


### Compiling, Training, and Evaluating the Model

**How many neurons, layers, and activation functions did you select for your neural network model, and why?**
I used the Keras hypertuner to determine the optimal configuration, and ended up will 11 layers using the relu activation function, with the neurons per layer being 36,51,76,31,96,56,66,31,36,11, and 96.

![Model Summary](https://github.com/Nveatch/Neural_Network_Charity_Analysis/blob/main/Resources/summary.png)


**Were you able to achieve the target model performance?**
No, I was unable to get hit the target accuracy of 75%. Using the hypertuner, I was able to obtain a theoretical accuracy of 74.45%, and running the model again with those hyperparameters, 74.00%. 

![Hypertuning](https://github.com/Nveatch/Neural_Network_Charity_Analysis/blob/main/Resources/hyper_tuning.png)

![Final Result](https://github.com/Nveatch/Neural_Network_Charity_Analysis/blob/main/Resources/accuracy.png)


**What steps did you take to try and increase model performance?**
From my baseline accuracy of 72.86%, I tried:

* Dropping the application types and classifications with less than 500 and 150 counts respectively, rather than using binning (72.82% accuracy)

* Dropping the status and special consideration columns (72.82% accuracy)

* Dropping the use case column, and the 50M+ income amount group (74.2% accuracy)

I also tried several other modifications of the income amount column, to try and address the model confusion caused by 71% of the rows having an income of 0 (which I'm assuming means that they left it blank):

* Dropping the income amount column entirely didn't improve the model accuracy

* Dropping the rows that did not have an income amount of 0 didn't improve model accuracy

* Dropping the rows that had an income amount of 0 actually allowed me to get a model accuracy over the target 75%, but at the cost of tossing out 71% of the data (a tradeoff I didn't think was worth it)


## Summary
Using the charity dataset and Keras deep learning API, I was able to achieve a model with almost 75% accuracy. I think an even higher accuracy could be achieved if the income amount field was not allowed to be zero, as this significantly confused the model. My recommendation for a different model to try would be a support vector machine (SVM). SVMs can handle multiple data types, which this data set has, and unlike deep neural networks, are less prone to overfitting, as well as missing an overall trend due to focusing on a single specific one.
