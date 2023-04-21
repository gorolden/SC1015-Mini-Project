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
