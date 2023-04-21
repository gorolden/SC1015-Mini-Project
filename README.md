# SC1015-Mini-Project


Gaming is a major industry globally, and researchers have been trying to figure out the best strategies for certain games. In our case, these strategies needed to be learned and regressed into a machine learning model. This was our problem.
The game, Age of Empires II is one of the most popular online real-time strategy games of all time. 

It features an online ranked ladder where players build and manage their own empires and engage in battle with other players trying to do the same. Amidst an extremely competitive online scene and a wide variety of civilisations and maps to pick from, let us see if machine learning models can help us predict the conditions that would result in a win!
The dataset for the matches of the game was imported from Kaggle. Since the set was very large initially, it had to cleaned and modified to only include the most useful contributions.

We begin by importing essential libraries for data analysis and learning models.

- ‘numpy’ is an array format that uses less memory and more convenient to use than lists. 
- 'pandas’ is the main Python library for data analysis. 
- ‘seaborn’ allows the construction of graphs and charts to represent our data.

The remaining code gives us the leverage of creating machine learning models for analysis.

There are 11 columns and over 3 million entries in this dataset. Our response variable is likely winning_team. The predictor variables can range from the match durations to even their environments. Anything else can be a predictor.
In the game, long drawn games can result in messy "trash wars". The "trash wars" may negatively affect our models. Therefore, we should consider removing these from our data.

In the 1st stage of the cleaning process, the duration variable was identified as a potential outlier that needed to be removed. It was observed that its range was high - from a second to as long as 60 days. The outliers were identified and removed.

A 2nd dataset was imported, containing individual player information - such as ELO, color, civilisation, etc. This was merged with the initial dataset based on token column. Further outliers such as NULL spaces in this new dataframe was also removed.

Analysis of the data was conducted using multiple bar plots and graphs. We moved on to machine learning process, starting with the classification tree.



This was used because our response variable is winner, which is of type bool. 6 predictors were listed as factors that may influence this response.
- color
- civ
- rating
- ladder
- map
- duration_seconds

A decisionTreeClassifier was used for these variables. Respective confusion matrices and accuracies were determined using them.
Train data:
- accuracy: 0.5
- TPR: 0.12
- TNR: 0.89
- FPR: 0.10
- FNR: 0.87

Test data:
- accuracy: 0.5
- TPR: 0.12
- TNR: 0.89
- FPR: 0.1
- FNR: 0.87

Analysis. At a low depth of 4, it is clear that our model is ineffective because the  acccuracies are about 0.50 for both train and test data. This means half the time it is making the wrong prediction. Furthermore, despite the ratio of actual wins to losses to be about 50:50, this model is predicting a huge majority of games to be 'Loss' compared to 'Win'.

- The following attempt at this model was to increase depth. It resulted in a better outcome. Accuracies went up, and the confusion matrices came out less skewed. It can be improved however.
- Attempt 3 went about by reducing the sample size during to the long compilation procedure. 2 of the 6 predictors were also removed. Any fluctuations that these variables created were therefore, eliminated. Model performed better on train, but worse on test datas. Overfitting (overcomplicating) was still an issue.
- Attempt 4: RandomForestClassifier was used now. This could change the model since it uses multiple trees. 
- > Exp 1: @n=100, & depth=4, model became underfitted
- > Exp 2: @n=1000, & depth=4, model performed better on test - but underfitted
- > Exp 3: @n=100, & depth=16, model accuracies improved, but overfitting happens
- > Exp 4: @n=1000, & depth=16, model performed the best, conclude that increasing both parameters obtains better model
- Attempt 5: GridSearchCV using to cross validate for optimum values at 'n' and 'depth'. Testing done at intervals.
- > Run 1: Accuracy. Parameter values checked by incrementing at regular intervals. 
- > Run 2: F1. Same process conducted.

Analysis:
- The GridSearchCV gave good accuracies. Run 1 resulted in an optimal depth value of 12, Run 2 resulted in depth value of 16. The ideal value may lie in between, but hardware constraints make it difficult to test for every circumstance. Accuracies for test/train data in this new method were close, which is quite optimal.

Conclusion:
- The data set is very large to work with. Therefore, we have utilised random classifying, grid searching, etc. to find some kind of a model. Determining the perfect model with no over/underfitting is impossible. Grid searching could be left running for a longer period, but this is not practical. 

Contributions:
- Ethan
- > Presentation slides, datasets, initial/fundamental data analysis, primary EDA, machine learning techniques, outcomes and experiments
- Ivan
- > Slide sorting, layouts, initial presentation of findings, secondary data analysis, secondary EDA, supplemental information, overall descriptions of works conducted

References:
- Jupyter Notebook/Anaconda
- Slidesgo
- Random Tree Classifiers
- > https://www.analyticsvidhya.com/blog/2020/05/decision-tree-vs-random-forest-algorithm/
- GridSearchCV
- > https://www.mygreatlearning.com/blog/gridsearchcv/
