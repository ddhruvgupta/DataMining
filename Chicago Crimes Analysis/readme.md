For a detailed report please refer to: https://github.com/ddhruvgupta/DataMining/blob/master/Chicago%20Crimes%20Analysis/DataMining_FinalProject.pdf

**Introduction**

This study uses the Chicago Crimes dataset to conduct an exploratory data analysis on the factors affecting crime rate and find correlations in the elements that can be used for crime prediction. To do this, several machine learning algorithms have been used to answer research questions like 
- Rate of change in crime rate over time
- Types of crimes which have the highest occurrence 

Specifically, carrying out performance comparison of a multi class – classifiers. The Naïve Bayes classifier gave 75 per cent accuracy, while on the other hand the classifier built using Random Forest gave our model an accuracy which was greater than 95 per cent.

**Step**

  •	 Conduct data cleaning <br/>
  •	 Visualize initial trends in crime data <br/>
 
  
 
  •	 Conduct exploratory data analysis (EDA) to find the most important variables for predicting type crime <br/>
  •	 Confirm that such a prediction is possible to make using machine learning techniques <br/>
  •	 Compare different approaches for classification and identify the most efficient method <br/>


**Dataset** <br />
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

K – Means 
K means clustering requires the number of clusters to be predefined. To find out the optimum number of clusters, the inertia vs number of clusters graph can be calculated. The goal is to have low inertia and low number of clusters. The “Elbow” is the point in the graph which represents a good balance between the inertia and number of clusters

 From the study of the inertia curve, the number of clusters is chosen as 6. 


Naïve Bayes

The clustering process shows that the 6 groups are well clustered and the overlap between classes is not too much. In the figure 1.5 million points are plotted together. This gives the authors confidence about the ability to get good results from a classification algorithm.

Predicting Arrests

**Naïve Bayes**
Naïve Bayes is a probabilistic classifier that calculates the independent probabilities of each event and the conditional probabilities with the target variable and then uses this probabilistic model to classify the test data. The classifier is Naïve since it assumes that the input variables are all independent of each other. 

In this section, the ‘Arrest’ variable has been used as the target variable and location information including longitude - latitude, ward, community area, location description etc. are taken as input variables.  
 
-	Precision = TP/(TP+FP) =  0.8438
-	Recall = Sensitivity = TP/(TP+FN) = 0.9208
-	Specificity = TN/(TN+TP) = 0.1662
-	Accuracy: 0.8157

**Random Forrest **

Random Forest has been used to run a comparative classifier to Naïve Bayes. The accuracy obtained from Random Forest is 2% better than Naïve Bayes

Random forest classifier is an ensemble learner (learners made of multiple base learners), composed of multiple decision trees. Each decision tree is built using a separate set of variables and the process of calculating the maximum decrease in Entropy is used recursively form a tree. 

The Random forest implementation is used to classify the type of crime based on the other features of the dataset including location information (Longitude, Latitude, Ward, Community, etc.), Arrest information, Domestic Abuse, and FBI code. The target consists of 33 separate values. 

K cross validation is used with a varying size of k to confirm that the model is not overfitting and the resulting accuracies are listed in the table below.

**Accuracies of random forest**
# of folds	| Accuracy
--- | ---
3	|0.9657
4	|0.9677
5	|0.9695
6	|0.9700
7	|0.9703
8	|0.9705
9	|0.9704
10|	0.9707
11|	0.9706
12|	0.9706
13|	0.9707
14|	0.9709



Due to the high dependence of the result on the FBI code being provided, a separate model is studied without the FBI code being present. 
The results showed that the new classifier accuracy fell to 14% when trying to classify the crime as one of 33 distinct types of crime. To improve the accuracy of the classifier, the groups created by k means are used as buckets of crime type instead. The new labels are evaluated by taking the mode of the cluster label within each crime type. For eg. If theft has 100 datapoints labeled as cluster 1 and 10 datapoints labelled as cluster 2, it is assumed that theft belongs to cluster 1. This re-evaluated model is used to train a Random Forest classifier and the results showed an increase in performance to 57% accuracy. The model was also executed with 31 trees but the model accuracy went up to only 58%. The experiments also repeated the process with Max-Min Scaler in use without much change in accuracy. 



**Conclusion**

Naïve Bayes is a good classifier for predicting if someone is like to get arrested based on location and the type of crime being committed. Random Forest is performed for the same target variable and is found to be marginally better. 
Random Forest has good accuracy to predict the type of crime based on the input vector consisting of all features in the dataset except Primary Type. However, the prediction was found to be very dependent on the FBI code and a study of the model minus the FBI code produced a model of only 38% accuracy. In case where Primary Types were clustered together, the Random Forest algorithm was able to predict the correct cluster at 73% accuracy. From the results the authors provide an acceptable baseline model for predicting the type of crime. 


**Visualzing Results**
<br />
![CrimesPerWard](./images/map.png)
<br />
![CrimesPerWard](./images/output.png)
<br />
![CrimesPerWard](./images/clustering.png)
<br />
![CrimesPerWard](./images/roc.png)
