**Introduction**

This study uses the Chicago Crimes dataset to conduct an exploratory data analysis on the factors affecting crime rate and find correlations in the elements that can be used for crime prediction. To do this, several machine learning algorithms have been used to answer research questions like 
- Rate of change in crime rate over time
- Types of crimes which have the highest occurrence 

Specifically, carrying out performance comparison of a multi class – classifiers. The Naïve Bayes classifier gave 75 per cent accuracy, while on the other hand the classifier built using Random Forest gave our model an accuracy which was greater than 95 per cent.

**Step**

  •	 Conduct data cleaning <br/>
  
  ![A test image](../images/imputation.png)
  
  •	 Visualize initial trends in crime data <br/>
  •	 Conduct exploratory data analysis (EDA) to find the most important variables for predicting type crime <br/>
  •	 Confirm that such a prediction is possible to make using machine learning techniques <br/>
  •	 Compare different approaches for classification and identify the most efficient method <br/>


**Dataset** 
https://www.kaggle.com/currie32/crimes-in-chicago/downloads/Chicago_Crimes_2012_to_2017.csv/1.h

**Results**

Classifier | Accuracy
--- | ---
Naïve Bayes (Arrests) |	84 %
Radom Forrest (Arrests)|	86 %
Random Forest (1 tree) |	93 %
Random Forest (2 tree)|	91 %
Random Forest (15 trees)|	97%
Random Forest (15 trees) without FBI|	38 %
Random Forest w/o FBI w/ (with cluster targets)|	73 % (15 trees)




