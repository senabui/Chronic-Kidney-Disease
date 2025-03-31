# Predictive Analysis and Early Detection of Chronic Kidney Disease

## Within this project, the goal was to answer the following two questions: 
## To what extent do diabetes, hypertension, and a family history of chronic kidney disease contribute to the likelihood of chronic kidney disease diagnosis, and how do their individual and combined effects impact predictive accuracy in a machine learning model? Can we develop a personalized risk scoring system for chronic kidney disease that incorporates clinical, lifestyle, and family history related risk factors to improve early detection and intervention?

Chronic Kidney Disease (CKD) is a continuously growing public health concern that often progresses slowly until advanced stages. This can lead to severe health complications and increased healthcare burdens. Understanding different key contributing factors to CKD development is crucial for early intervention and detection. Some significant risk factors are diabetes, hypertension, and a family history of CKD that have been widely recognized for their combined or individual roles in CKD progression. By leveraging machine learning techniques, this research aims to quantify these relationships and further evaluate the incorporation of multiple risk factors to enhance the ML CKD prediction models. By developing an in-depth ML model, this research seeks to bridge the gap between risk identification and proactive management, improving patient outcomes and reducing CKD morbidity.

The following ML models were used in our research methodology:
* Random Forest Model
* Clustering
* Logistic Regression

<img src="Images/K-Means Clustering Visualization copy.jpeg" width="700">
The dataset underwent Z-score normalization and Synthetic Minority Oversampling Technique (SMOTE) to handle class imbalance before clustering. Principle Component Analysis (PCA) was utilized to reduce dimensionality while retaining the most important variance in the data. Two clustering configurations were tested: K=3 clustering used 11 PCA components, explaining 91.3% variance and producing three primary CKD risk groups. K=5 clustering used 5 PCA components, explaining 55.1% variance, leading to more granular risk stratification but increased cluster overlap. 

The optimal number of clusters was determined using the Elbow Method and Silhoutte Score, with K=3 providing clearer distinctions between risk groups. Cluster assignments revealed patterns in CKD risk progression, with high-risk clusters showing higher serum creatinine levels, lower GFR, and more severe CKD symptoms, while lower-risk clusters had near-normal clinical values. Clustering analysis identified diabetes and hypertension as primary risk factors for high-risk clusters, whereas family history played a secondary role. 

<img src="Images/K-Means Cluster Feature Means.png" width="700">


<img src="Images/Random Forest Evaluation Metrics and Class Confusion Matrix.png" width="700">
Random Forest was used to predict whether patients were diagnosed with CKD. Hyperparameter tuning was performed using GridSearchCV with 5-fold cross-validation. The optimal parameters included n_estimators=200, max_depth=20, min_samples_split=2, min_samples_leaf=1, class_weight=None. The model demonstrates excellent performance with an accuracy of 94.5%. The balanced precisio and recall metrics indicate the Random Forest model is effective at identifying both CKD and non-CKD cases, with high accuracy, precision, and recall. 

<img src="Images/Distribution of Risk Scores.png" width="700">
A weighted sum approach was used in which each clinical and lifestyle feature was assigned a risk weight based on its contribution to the regression model. A logistic function was applied to the risk scores to convert them into probabilities, making them more interpretable for clinical decision-making. To further refine risk assessment, a dynamic thresholding approach was used to categorize patients into low, moderate, and high risk based on percentile ranking. Low risk was classified
as anything below 33rd percentile, moderate was between 33rd-67th percentile and high was above 67th percentile. 

The system was also integrated into an interactive input systems to allow for medical professionals to enter patient data and receive real-time risk predictions. This feature makes the system more accessible for clinical use, offering a way to incorporate machine learning outpouts into early CKD detection. 

<img src="Images/Real-time Risk Score Predictions .png" width="700">

