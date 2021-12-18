# Credit_Risk_Analysis
Evaluating the performances of different models to predict credit risk.

## Overview
The purpose of this analysis is to evaluate the performance of resampling algorithms, RandomOverSampler, SMOTE, ClusterCentroids and SMOTEENN; and evaluate the performance of two ensemble classifiers, BalancedRandomForestClassifier and EasyEnsembleClassifier, on an imbalanced dataset from LendingTree. The accuracy score, confusion matrix, and classification report are used to access each model and determine whether they should be used to predict credit risk.

## Tools
- Jupyter Notebook
- Python (scikit-learn and imbalanced-learn libraries)


## Results
For each resampling algorithm, LogisticRegression classifier from scikit-learn is used to evaluate their performances. All images below contain the balanced accuracy score, confusion matrix, and the classification report for each result. '0' represents 'high_risk' rand 1 represents 'low_risk'.

- RandomOversampler (Naive Random Oversampling)
    - The balanced accuracy score is 0.657 which isn't great since the dataset is heavily weighted towards low risk and this is reflected later in the classification report.
    - The confusion matrix shows that this algorithm was good at catching true positives ie catching genuine high risk instances returning 72 of 101 instances that were high risk. However there is an abundance of false positives with a ratio of 83.5 false positives for each true positive. In a practical sense this model this would not be an acceptable model.
    - In the classification report, precision and recall for the high risk category reflects this with a precision of 0.01 and recall of 0.71 giving it an f1 score of 0.02. The low risk's precision and recall are 1.00 and 0.60 respectively. The high precision of low risk and it's low recall affects the overall accuracy of model.
<br><img src='Resources/ros.png' height=400 width=450><br>


- SMOTE Oversampling
    - The balanced accuracy score is 0.662 which is marginally better than ROS.
    - The confusion matrix shows that this algorithm isn't as good as identifying high risk true positives but does identify fewer false positives as well identifying 82.6 false positives for each true positive.
    - In the classification report, high risk has a 0.01 precision and a recall of 0.63, ie the precision is relatively the same but the recall has decreased. The For low risk the model is still good at identifying true positives for low risk with a precision of 1.0 and the recall has improved to 0.69 for an f1 score of 0.82. Overall this model performs better than the previous one but isn't good enough to use in a real scenario because of the high false positives for high risk.
<br><img src='Resources/smote.png' height=400 width=450 ><br>

- ClusterCentroids Resampler (Undersampling)

    results go here
    <br><img src='Resources/cc.png' height=400 width=450 ><br>

- SMOTEENN (Combination Sampling)

    Results go here
    <br><img src='Resources/smoteenn.png' height=400 width=450><br>

Ensemble algorithms results are listed below. Both models were trained using the original training sets. 

- BalancedRandomForestClassifier
    
    Results go here
    <br><img src='Resources/brfc.png' height=400 width=450><br>

- EasyEnsembleClassifier (Easy Ensemble AdaBoost Classifier)

    results go here
    <br><img src='Resources/eec.png' height=400 width=450><br>


## Summary
