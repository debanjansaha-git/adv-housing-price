## Ames-Iowa-Housing-Data-Set
![](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)

![Python](https://img.shields.io/badge/Python-3.9-blue)
![License](https://img.shields.io/github/license/mashape/apistatus.svg)

### Domain

The Ames Housing dataset, which describes the sale of individual residential property in Ames, Iowa from 2006 to 2010, was compiled by Dean De Cock for use in data science education. It was designed based after the Boston Housing dataset and is now considered a more modernized and expanded version of it. More details of this dataset are described in [*Ames, Iowa: Alternative to the Boston Housing Data as an End of Semester Regression Project*](https://ww2.amstat.org/publications/jse/v19n3/decock.pdf).

### Problem Statement

The objective of this data set is to predict the final sale price of each home based on 79 other explanatory variables.

### Data Description

The original data set can be found [here](https://ww2.amstat.org/publications/jse/v19n3/decock/AmesHousing.txt).

### Solution Statement

This dataset can be solved by applying regression techniques, like linear regression, random forest, or gradient boosting.
We have used simple linear regression here. One is be advised to try out various models and check which one works for the best.

### Exploratory Data Analysis (EDA)

Various EDA techniques have been applied to this dataset including:
<ol>
    <li>If percentage of null records exceed 5% -> Remove the feature</li>
    <li>For text columns drop rows where there are missing values</li>
    <li>If nulls are less than 5%, we will fill them with most appropriate values</li>
    <li>Convert the text columns into categorical features</li>
    <li>If the features are not of much use, drop them</li>
    <li>Try creating new features if possible</li>
</ol>

For categorical feature handling, the following methods were tried
<ol>
    <li>Create a list of categorical column names</li>
    <li>Convert numerical features that should be categorical</li>
    <li>Drop categorical columns with more than 10 unique values</li>
    <li>Drop categorical columns with unique values under 2 and a very skewed distribution</li>
    <li>Create dummies for remaining categorical columns</li>
</ol>
    

### Feature Engineering
    
Various feature engineering has been tried on this dataset, to create new meaningful features.

The below features have been combined into two single features
<ul>
    <li>Bsmt Full Bath: Basement full bathrooms</li>
    <li>Bsmt Half Bath: Basement half bathrooms</li>
    <li>Full Bath: Full bathrooms above grade</li>
    <li>Half Bath: Half baths above grade</li>
</ul>

The below features were dropped as there was no requirement for what type of sale has been processed
<ul>
    <li>Mo Sold: Month Sold (MM)</li>
    <li>Yr Sold: Year Sold (YYYY)</li>
    <li>Sale Type: Type of sale</li>
    <li>Sale Condition: Condition of sale</li>
</ul>

The below features were re-engineered to a more relevant feature, which is the age of the house.
<ul>
    <li>Year Built: Original construction date</li>
    <li> Year Remod/Add: Remodel date (same as construction date if no remodeling or additions)</li>
    
</ul>

### Feature Selection
After performing all the above steps, a correlation is drawn between the target (`Sale Price`) and all the features.
The features which have more than 30% correlation with the target were kept and the rest were discarded.

### Performance Metric

Performance is evaluated on Root-Mean-Squared-Error (RMSE) between the predicted value and the observed sale prices.

### Validation Testing

We perform three types of validation

#### Holdout Testing
The training is performed on 1460 datapoints and the rest of the dataset is used for validation.\
The model is able to attain a RMSE value of 36632.403066029794

#### Cross Validation Testing
Simple cross validation testing is performed with k = 1.\
The model is able to attain a RMSE value of 33782.16373371206

#### K-fold Testing
Multiple values of k are tried until the model attains minimum RMSE error.\
The model is able to attain a RMSE value of 30495.773468817508 at k = 98.