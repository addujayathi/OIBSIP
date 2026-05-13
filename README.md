Predicting House Prices using Linear Regression 

Tools Used:

• Python (Google Colab) 
• Pandas, NumPy 
• Matplotlib, Seaborn 
• Scikit-learn 
• GitHub 

PHASE 1: Understanding the Dataset 
• 545 rows and 13 columns 
• Target variable:  
• Price (house sale price in INR) 

Columns 
1. Price 
2. Area 
3. Bedrooms 
4. Bathrooms 
5. Stories 
6. Parking 
7. Main Road 
8. Guest Room 
9. Basement 
10. Hot Water Heating 
11. Air Conditioning 
12. Preferred Area 
13. Furnishing Status 

PHASE 2: Data Loading and Cleaning 
Loaded the dataset (Housing.csv) into Google Colab and performed the following cleaning 
steps: 
• No missing values found — df.isnull().sum() returned all zeros 
• No duplicate rows detected — df.duplicated().sum() returned 0 
• Encoded binary categorical columns (yes/no) into 1/0 
• Applied One-Hot Encoding on furnishing status (semi-furnished, unfurnished) 

PHASE 3: Descriptive Statistics 
Summary Statistics (Price column): 
Mean Price 
₹ 4,766,729 
Std Deviation 
₹ 1,870,440 
Min Price 
₹ 1,750,000 
Max Price 
₹ 13,300,000 
Median (50th %ile) 
₹ 4,340,000 
• High standard deviation indicates a wide spread in house prices 
• Mean is significantly higher than the median, suggesting right skew in price distribution 

PHASE 4: Exploratory Data Analysis (EDA) 
1. Correlation Heatmap 
Generated a heatmap using sns.heatmap() on numeric columns. Area, bathrooms, and stories 
showed the strongest positive correlations with price. 

2. Price Distribution (Histogram + KDE) 
The histogram showed that most house prices are concentrated in the lower range, with a 
right-skewed distribution — a few premium properties drive the mean upward. 

3. Area vs Price (Scatter Plot) 
A positive linear trend was visible between area and price, confirming area as a strong 
predictor variable. 

PHASE 5: Data Preprocessing 

Feature Engineering: 
• Dropped the target variable (price) to create the feature matrix X 
• Kept price as the target vector y 

Encoding: 
• Binary columns (mainroad, guestroom, basement, hotwaterheating, airconditioning, 
prefarea) mapped from yes/no to 1/0 
• furnishingstatus encoded via pd.get_dummies() with drop_first=True to avoid 
multicollinearity 

Feature Scaling: 
• Applied StandardScaler on numerical columns: area, bedrooms, bathrooms, stories, 
parking 
• Scaling ensures all features contribute proportionally to the model 
Handling Missing Values (Post-Encoding): 
• Used SimpleImputer (strategy='mean') to handle any NaN values in the feature matrix 
before model training 

PHASE 6: Model Building — Linear Regression 

Train-Test Split: 
• 80% training data → 436 rows 
• 20% testing data → 109 rows 
• random_state=42 used for reproducibility 

Model: 
• Algorithm: LinearRegression() from sklearn.linear_model 
• Fit on imputed training data (X_train_imputed, y_train) 
• Predicted house prices on X_test_imputed 

PHASE 7: Model Evaluation 

R-squared (R²) 
0.6529 

Mean Absolute Error (MAE) 
970,043.40 

Mean Squared Error (MSE) 
1,754,318,687,330.67 

Interpretation: The R² score of 0.65 means the model explains ~65% of the variance in house 
prices. The MAE of ~970K indicates an average prediction error of roughly ₹9.7 lakh. 

PHASE 8: Data Visualization 

Correlation Heatmap 
Highlighted that area, bathrooms, and stories are the most correlated features with price. 
Parking had a weaker correlation. 

Price Distribution Histogram (with KDE) 
Showed right-skewed distribution of house prices. Most houses fall in the ₹1.75M–₹5M range. 

Area vs Price Scatter Plot 
Positive linear relationship confirmed. Larger area generally commands a higher price. 

Actual vs Predicted Price Scatter Plot 
Points clustered around the red diagonal (perfect prediction line), indicating the model 
performs reasonably but has room for improvement at extreme values. 

PHASE 9: Recommendations & Insights 
• Area is the strongest predictor of house price — larger properties consistently fetch 
higher prices. 
• Amenities like air conditioning, preferred area location, and number of bathrooms 
significantly push prices upward. 
• Furnishing status matters — furnished homes tend to be priced higher than semi
furnished or unfurnished ones. 
• The model achieves a reasonable R² of 0.65, but the high MAE suggests that non-linear 
models (e.g. Random Forest, Gradient Boosting) could better capture complex 
interactions. 
• Right-skewed price distribution suggests applying log transformation on the target 
variable could improve model performance. 
• Feature importance analysis with tree-based models would help identify which variables 
contribute most to pricing. 
