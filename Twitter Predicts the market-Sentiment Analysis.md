
Date: 2024-09-10

Tags: [[Quant Resources]]

## Summary

A basic form of sentiment analysis. Relevant twitter messages are analyzed in either Opinion Finder(OF) or Google-Profile Of Mood States (GPOMS). The messages are assigned a mood category. Some sort of mood index time series is created and compared with the DJIA closing values. Can use multiple regression or a Self-Organizing Fuzzy Neural Network (SOFNN).

OF assigns either positive or negative emotion whereas GPOMS has 6 category values (derived from Profile of Mood States, POMS-bi).

The conclusion is that GPOMS is useful in predicting the closing value to some degree. The most statistically significant correlation is with calm values and coming close is the combination of calm and happy values.

Try to keep DJIA in the form of change in closing prices. i.e. :

$D(t) = DJIA(t) - DJIA(t-1)$

## Schematic

Schematic representation of the system.

![[Screenshot 2024-09-10 234235.png]]


## Steps to implement study

1. Obtain data that can serve as a proxy for public mood, such as twitter opinions. 
2. Filter the input data by keeping only relevant tweets (sanitize the input).
3. Feed the data into mood analyzer such as OF or GPOMS.
4. Normalize values of OF/GPOMS with z-score in a sliding window to enable comparison between the two (DONT normalize the values going into the NN). 
5. Cross-validate the accuracy of the mood analyzers by seeing how well the data does on an obvious expected emotional response. For example, both should accurately show a temporary spike in happiness around Diwali. Can perform a multiple regression of GPOMS on OF and see which values are statistically significant.
6. Obtain data on closing value of relevant market index, such as DJIA (lagged values of X will exhibit a statistically significant correlation with Y).
7. Perform a Granger Causality test (multiple regression) to relate D(t) and GPOMS/OF. Once on just the lagged values D(t-i) and once add GPOMS variables to the first version. "i" can go from 1 to n where, the paper says past 3 diminishing returns to significance.
8. Deploy SOFNN to test hypothesis and predictive power. Parameters need to be tuned (try delta= 0.04, = 0.01, krmse = 0.05, kd(i), (i = 1, ..., r) = 0.1 where r is the dimension of input variables and krmse is the expected training root mean squared error which is a predefined value.)
9. Test linear effect of chosen categories on DJIA (for fun i guess?) with a nested F-Test.

## Models and Equations

![[Screenshot 2024-09-11 003354.png]]
Normalization formula for mood scores comparison.

![[Screenshot 2024-09-11 003528.png]]
Cross validation; Multiple regression of GPOMS on OF

![[Screenshot 2024-09-11 003615.png]]
Granger Causality Model

![[Screenshot 2024-09-11 003648.png]]
Input combinations to SOFNN


![[Screenshot 2024-09-11 003725.png]]
F-test Models

## Further Suggestions

1. Try implementing other neural networks. Compared with some notable fuzzy neural network models, such as the adaptive-network-based fuzzy inference systems (ANFIS) [22], self-organizing dynamic fuzzy neural network (DFNN)[11] and GDFNN [49], SOFNN provides amore efficient algorithm for online learning due to its simple and effective parameter and structure learning algorithm [28]. In our previous work, SOFNN has proven its value in electrical load forecasting [32], exchange rate forecasting [28] and other applications [29].

## References
https://www.sciencedirect.com/science/article/pii/S187775031100007X