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
    - In the classification report, average precision is 0.99 and average recall is 0.60 giving it an average f1 score of 0.75 reflecting the weight of the low risk instances which is in every resampled model.
<br><img src='Resources/ros.png' height=400 width=450><br>


- SMOTE Oversampling
    - The balanced accuracy score is 0.662 which is marginally better than ROS.
    - The confusion matrix shows that this algorithm isn't as good as identifying high risk true positives but does identify fewer false positives as well identifying 82.6 false positives for each true positive.
    - In the classification report, high risk has a 0.01 precision and a recall of 0.63, ie the precision is relatively the same but the recall has decreased. The For low risk the model is still good at identifying true positives for low risk with a precision of 1.0 and the recall has improved to 0.69 for an f1 score of 0.82. Overall this model performs better than the previous one but isn't good enough to use in a real scenario because of the high false positives for high risk.
<br><img src='Resources/smote.png' height=400 width=450 ><br>

- ClusterCentroids Resampler (Undersampling)
    - The balanced accuracy score dropped to 0.544 with this resampling, performing worse than SMOTE and SMOTE.
    - According to the confusion matrix, this model captured 70 high risk instances out of 101  but also returned a large amount of false positives for every true positive the model returned about 148 false positives. Thus this model is less accurate. This is reflected in the classification report.
    - The high risk precision is 0.01 having identified a large amount of low_risk instances as high risk. The recall increased to 0.69 resulting in an f1 score of 0.01, a slight decrease. For the low risk the model is 1.00 for precision and 0.40 for recall giving an over all f1 score much lower than SMOTE and ROS. The recall is disappointing given how weighed the model is for low risk. 
    <br><img src='Resources/cc.png' height=400 width=450 ><br>

- SMOTEENN (Combination Sampling)
    - The balance accuracy score is 0.688, the highest of all resampling algorithms.
    - The confusion matrix shows the number of high risk instances found increased to 80 while the false positives is 7298. This model would return about 90 false positives for every true positive, so there is a trade off. It returned more true high risk instances than all the other resampling algorithms but it also returned a high number of low risk as high risk. 
    - The recall for the high risk and low risk reflects this, both increasing to 0.80 and 0.57 respectively. This increase both of the f1 scores resulting in 0.02 for high risk and 0.73 for low risk.
    <br><img src='Resources/smoteenn.png' height=400 width=450><br>

Ensemble algorithms results are listed below. Both models were trained using the original training sets. 

- BalancedRandomForestClassifier
    - The balanced accuracy score is 0.788, higher than all resampling algorithms.
    - With this model there is a significant decrease in the amount of false positives returned while the amount of true positives remain high at 71 out of 101. So for every true high risk instance it returns 30 false high risk that are actually low risk. This is a high decrease, making this model more attractive at identifying credit risk according to the confusion matrix.
    - The recall for both high risk and low risk are 0.70 and 0.87 respectively, yielding average f1 score of 0.93, higher than all resampling models.
    <br><img src='Resources/brfc.png' height=400 width=450><br>

- EasyEnsembleClassifier (Easy Ensemble AdaBoost Classifier)
    - The balanced accuracy score is 0.932, the highest overall.
    - The confusion matrix shows why the accuracy increased The number of true positives is extremely high while the false positives increased by a large margin. This means that for every true positive only 10.6 false positives.
    - The precision has increased to 0.09 for the high risk while the recall for both high risk and low risk remains high, both over 0.90. This model performed the best out of all models with an f1 score of 0.97.

    results go here
    <br><img src='Resources/eec.png' height=400 width=450><br>


## Summary
Overall the poorest performing model was the Cluster Centroids resampler with a the lowest accuracy score and f1 score. It would also return the highest amount of false negatives for each true positive. So if Lending Tree used this model, it would reject 148 low risk cases for every high risk case.The other resampling models are ok but not applicable to real world use. This isn't conducive to a good loan strategy. The EasyEnsemblerClassifier is the best overall score with the highest, accuracy score, true positive returns, highest f1, precision and recall scores. EEC is the recommended model. 