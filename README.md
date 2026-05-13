Wine Quality Prediction 

Tools & Technologies Used 

Python 
Google Colab 
Pandas 
NumPy 
Matplotlib 
Seaborn 
Scikit-learn 
Pickle 

PHASE 1: Understanding the Dataset 

The dataset contains chemical properties of wine samples and their quality ratings. 
Total Rows: 1143 
Total Columns: 13 

Columns 
1. Fixed Acidity 
2. Volatile Acidity 
3. Citric Acid 
4. Residual Sugar 
5. Chlorides 
6. Free Sulfur Dioxide 
7. Total Sulfur Dioxide 
8. Density 
9. pH 
10. Sulphates 
11. Alcohol 
12. Quality 
13. Id 

PHASE 2: Data Loading & Preprocessing 
Initially, the dataset was loaded into Google Colab using Pandas. 

import pandas as pd 
df = pd.read_csv('Wine quality dataset.csv') 

The following operations were performed: 
 df.head() → Displayed first few rows. 
 df.shape → Checked number of rows and columns. 
 df.columns → Displayed column names. 
 df.info() → Checked data types and missing values. 
 df.describe() → Generated statistical summary. 

Data Cleaning Performed 
1. Checked for missing values using: 
df.isnull().sum() 
Result: 
 No missing values were found. 

2. Checked duplicate values using: 
df.duplicated().sum() 
Result: 
 Duplicate rows were identified and analyzed. 

 PHASE 3: Exploratory Data Analysis (EDA) 
1.Quality Distribution Analysis 
A count plot was created to visualize wine quality distribution. 
sns.countplot(x='quality', data=df) 
 Most wines belonged to quality ratings 5 and 6. 
 Very few wines had extremely low or extremely high quality. 
 The dataset was slightly imbalanced. 

2. Correlation Analysis 
A heatmap was generated to analyze relationships between features. 
sns.heatmap(df.corr(), annot=True, cmap='coolwarm') 
 Alcohol showed positive correlation with quality. 
 Volatile acidity showed negative correlation with quality. 
 Sulphates and citric acid also influenced quality positively. 
 Density had slight negative relationship with quality.

3. Histogram Analysis 
Histograms were plotted for all numerical features. 
df.hist(figsize=(12,8)) 
 Most features were not perfectly normally distributed. 
 Some features contained skewness. 
 Alcohol values were concentrated in a specific range. 

4. Boxplot Analysis 
A boxplot was created between alcohol and wine quality. 
sns.boxplot(x='quality', y='alcohol', data=df) 
 Higher quality wines generally contained higher alcohol levels. 
 Outliers were present in certain quality categories. 
Alcohol content plays a major role in determining wine quality. 

 PHASE 4: Feature Engineering 
The quality column originally contained multiple quality ratings. 
To simplify the prediction problem, the target variable was converted into binary 
classification. 
df['quality'] = df['quality'].apply(lambda x: 1 if x >= 7 else 0) 
 Quality ≥ 7 → Good Wine (1) 
 Quality < 7 → Bad Wine (0) 

Benefits 
 Simplified model training. 
 Improved classification performance. 
 Easier interpretation of predictions. 

PHASE 5: Feature & Target Separation 
The dataset was divided into: 
 Features (X) 
 Target Variable (y) 
X = df.drop(['quality', 'Id'], axis=1) 
y = df['quality'] 

Features Used 
 Acidity values 
 Sugar levels 
 Sulfur dioxide levels 
 Alcohol percentage 
 Density 
 pH value 
 Sulphates 
Target Variable 
 Wine Quality (Good or Bad) 

PHASE 6: Train-Test Split 
The dataset was divided into training and testing data. 
from sklearn.model_selection import train_test_split 
X_train, X_test, y_train, y_test = train_test_split( 
X, y, test_size=0.2, random_state=42 
) 

Split Ratio 
 80% → Training Data 
 20% → Testing Data 

Purpose 
 Training data is used to train the model. 
 Testing data is used to evaluate performance. 

PHASE 7: Feature Scaling 
Feature scaling was applied using StandardScaler. 
from sklearn.preprocessing import StandardScaler 
scaler = StandardScaler() 
X_train = scaler.fit_transform(X_train) 
X_test = scaler.transform(X_test) 

Why Scaling is Important? 
 Ensures all features are on similar scale. 
 Improves performance of ML algorithms. 
 Prevents features with larger values from dominating. 

PHASE 8: Model Building 
Three Machine Learning algorithms were used for prediction. 

1.Random Forest Classifier (RFC) 
from sklearn.ensemble import RandomForestClassifier 
rf = RandomForestClassifier() 
rf.fit(X_train, y_train) 

 Random Forest is an ensemble learning algorithm that combines multiple 
decision trees. 

Advantages 
 High accuracy 
 Handles complex relationships 
 Reduces overfitting 

2.SGD Classifier 
from sklearn.linear_model import SGDClassifier 
sgd = SGDClassifier() 
sgd.fit(X_train, y_train) 

 Uses stochastic gradient descent optimization for classification. 
Advantages 
 Faster training 
 Efficient for large datasets 
 Memory efficient 

3.Support Vector Classifier (SVC) 
from sklearn.svm import SVC 
svc = SVC() 
svc.fit(X_train, y_train) 

 Support Vector Machine identifies optimal boundary between classes. 

Advantages 
 Effective in high-dimensional data 
 Good classification performance 
 Robust against overfitting 

PHASE 9: Model Evaluation 
The models were evaluated using accuracy score, classification report, and confusion 
matrix. 
from sklearn.metrics import accuracy_score 

Accuracy Comparison 
 Random Forest Accuracy was highest among the models. 
 SGD showed moderate performance. 
 SVC also performed well. 

Conclusion 
Random Forest was selected as the best model for wine quality prediction. 

Classification Report 

print(classification_report(y_test, rf_pred)) 

Metrics Used 
 Precision 
 Recall 
 F1-Score 
 Support 

Interpretation 
 High precision means fewer false predictions. 
 High recall means better identification of good wines. 
 F1-score balances precision and recall. 

Confusion Matrix 
cm = confusion_matrix(y_test, rf_pred) 
sns.heatmap(cm, annot=True, fmt='d') 

Purpose 
Shows: 
 Correct Predictions 
 Incorrect Predictions 
 False Positives 
 False Negatives 

Observation 
The model achieved strong prediction capability with fewer misclassifications. 

PHASE 10: Feature Importance Analysis 
Feature importance was analyzed using Random Forest. 
importance = rf.feature_importances_ 
A bar graph was generated for visualization. 

Important Features Influencing Quality 
1. Alcohol 
2. Volatile Acidity 
3. Sulphates 
4. Citric Acid 

Conclusion 
Alcohol content had the highest impact on wine quality prediction. 

PHASE 11: Model Saving 
The trained model and scaler were saved using Pickle. 

import pickle 
pickle.dump(rf, open('wine_model.pkl', 'wb')) 
pickle.dump(scaler, open('scaler.pkl', 'wb')) 

Purpose 
 Enables future predictions without retraining. 
 Useful for deployment in web applications. 

PHASE 12: Model Download 
The trained files were downloaded from Google Colab. 
from google.colab import files 
files.download('wine_model.pkl') 
files.download('scaler.pkl') 

Final Insights & Conclusions 
 Alcohol content strongly influences wine quality. 
 Volatile acidity negatively affects wine quality. 
 Most wine samples belonged to medium-quality range. 
 Random Forest outperformed other ML algorithms. 
 Feature scaling improved model efficiency. 
 Binary classification simplified prediction. 
