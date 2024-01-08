# Breast-Cancer-EDA
Analysis of the Breast Cancer Wisconsin (Diagnostic) DataSet, found on Kaggle an exploratory data analysis using machine learning classification models and comparing results. The best model found for this EDA was the Logistic Regression model.
<br>
<p align="center" width="100%">
    <img width="65%" src="/data-cover.png">
</p>
<br>
<b>INTRODUCTION</b> <br>
<i>Using the Breast Cancer Wisconsin (Diagnostic) Database, I explore the data and create a classifier that can help diagnose patients and predict whether the cancer is benign or malignant. Machine learning techniques are explored. In this exercise, Random Forest is being implemented with 98% accuracy.</i> <br>
<br>
<br>
<b>DATA</b> <br>
The Breast Cancer Wisconsin (Diagnostic) Data Set provides data on the features that are computed from a digitized image of a fine needle aspirate (FNA) of a breast mass. The features describe the characteristics of the cell nuclei present in the image. There are 30 variables that offer a lot of information in the dataset as features. These are listed as 'diagnosis', 'radius_mean', 'texture_mean', 'perimeter_mean',  'area_mean', 'smoothness_mean', 'compactness_mean', 'concavity_mean',  'concave points_mean', 'symmetry_mean', 'fractal_dimension_mean', 'radius_se', 'texture_se', 'perimeter_se', 'area_se', 'smoothness_se', 'compactness_se', 'concavity_se', 'concave points_se', 'symmetry_se',  'fractal_dimension_se', 'radius_worst', 'texture_worst', 'perimeter_worst', 'area_worst', 'smoothness_worst', 'compactness_worst', 'concavity_worst', 'concave points_worst', 'symmetry_worst', 'fractal_dimension_worst'. The variable ‘diagnosis’ listed holds the values ‘m’ for Malignant, or  ‘b’ for benign. All the variables including the ‘id’ and ‘Unamed’ were of numeric values with ‘diagnosis’ being the exception, categorical. The dataset was clean in that when checked for missing or null values, there were none, though the ‘Unamed: 32’ variable has NaN values. 
<p align="center" width="100%">
    <img width="60%" src="/data.png">
</p> 
<br>
Attribute Information from the dataset is as follows:
ID number
Diagnosis (M = malignant, B = benign)
Ten real-valued features are computed for each cell nucleus:
radius (mean of distances from the center to points on the perimeter)
texture (standard deviation of gray-scale values)
perimeter
area
smoothness (local variation in radius lengths)
compactness (perimeter^2 / area - 1.0)
concavity (severity of concave portions of the contour)
concave points (number of concave portions of the contour)
symmetry
fractal dimension ("coastline approximation" - 1)

The mean, standard error, and "worst" or largest (mean of the three
largest values) of these features were computed for each image,
resulting in 30 features. For instance, field 3 is the Mean Radius and field
13 is Radius SE, field 23 is Worst Radius.
All feature values are recoded with four significant digits.

Missing attribute values: none
Class distribution: 357 benign, 212 malignant
<br>
<br>
<b>PROCEDURE</b> <br>
Exploratory data analysis
Create analytical models – classification
Create train and test datasets
Test accuracy of predictions
Exploratory data analysis
The dataset I worked from is included in the files, this dataset was downloaded from Kaggle, after importing all the relevant libraries, I imported the dataset and started to look at the data. When looking at the information, the data held 569 entries and 33 columns. In the data, the variables ‘ID’ and  ‘Unamed: 32’ held no significant values, ‘ID’ values are arbitrary values and the ‘Unamed: 32’ variable contained NaN values that offer nothing to the data. As both had no significance, they were removed. Having checked the types I confirmed that the only variable which is not numeric was ‘diagnosis’. This variable for ‘diagnosis’ contained either an ‘M’ for malignant or ‘B’ for benign. The distribution for the ‘diagnosis’ showed  212 for malignant and 357 for benign. Below is an image from the EDA showing the count for benign in colour purple and the count for malignant in colour rust.
<p align="center" width="100%">
    <img width="60%" src="/count-plot.png">
</p> 
<br>
Studying a boxplot of the variables showed some considerable outliers. It is important to know when to keep or remove your outliers as either approach can have impacts on your data. After looking at the IQR and checking the shape after removing the outliers, I decided to keep the outliers for this project.

Using KDE Kernel Density Estimate plots to further review the data and see if there are any trends or correlations between variables. The Kernel Density Estimate plot was used in this instance as they are known to be better at accentuating patterns in data distributions. When looking at the pair plots there were noticeable interesting patterns visible. The ones that stood out were the almost perfect linear patterns between the radius, perimeter, and area attributes, implying that there is indeed multicollinearity between these variables. Another set of variables that possibly imply multicollinearity are concavity, concave points, and compactness.
<br>
<p align="center" width="100%">
    <img width="60%" src="/kde.png">
</p> <br>
There was quite a bit of correlation as seen on the heatmap in the EDA, I looked more into this by looking at each set of variables within the data frame separately, all the mean, se, and worst variable groups.
As can be seen by the pair plots there was a lot of correlation. Once feature selection was complete, I went through classification with Random Forest. After reducing the features down to 16 from 30, from just looking at the data, I also implemented a Feature Recursive Elimination to compare how well my selection did compared to the feature recursive elimination in the testing.
A logistic Regression Predictor was used with a Correct Prediction score of 97.1 %
<br>
<br>
<b>RESULTS</b>
<br>
Once the data had been split for Training and Testing I used Random Forest classifier and the results were quite good:
Recall:  0.9814814814814815
Accuracy:  0.9707602339181286
F1 score:  0.9769585253456222 
The results with the features selected using feature recursive elimination were the same:
	Recall:  0.9814814814814815
Accuracy:  0.9707602339181286
F1 score:  0.9769585253456222
Testing the accuracy of the predictions with models Logistic Regression, K Neighbors, and Random Forest classifiers. Initially when done all classifiers worked well, though after a recent update, I noted that the KNeighbours classifier was throwing an error. After some research, I managed to get the classifier working again, providing the lowest result of the three classifiers.  <br>
<p align="center" width="100%">
    <img width="60%" src="/model_accuracy.png">
</p> <br>
<br>
<b>CONCLUSION</b> 
<br>
As seen from the Logistic Regression prediction, we can make predictions with a 97% accuracy based on the attributes chosen. This of course can be improved with a deeper look at the attributes and perhaps using a different classifier.
