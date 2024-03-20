# Bike Sharing Demand Prediction
## Main Objective
The primary objective of this project is to predict the hourly demand of a bikesharing system in Seoul, with the ultimate goal of enhancing availability and accessability of bikes, minimizing waiting times for users, and ensuring a responsive supply that alligns with the dynamic demand of the urban environment. This project encompasses the utilization of regression models to provide accurate forecasts of demand, along with an employment of causal inference to understand the main causalities behind demand fluctations.

## Project Steps
### Data Pre-processing
1. **Data Structure Analysis:** Conducted an in-depth exploration of dataset statistics and distributions to form a foundational understanding of the underlying data structure.

*Figure: The distributions of features in the bike sharing dataset*
![Example: The distributions of different features within the dataset](https://github.com/MohamedElenany/Bike-Sharing-Demand-Prediction/assets/89152453/23e31c80-e209-4de0-abaa-5e57fe6264a4)

3. **Data Visualization for Insights:** Performed comprehensive correlation studies and experimented with diverse attribute combinations to uncover nuanced relationships within the dataset.

*Figure: The correlation matrix of features in the bike sharing dataset*
![image](https://github.com/MohamedElenany/Bike-Sharing-Demand-Prediction/assets/89152453/7967bfe1-da7b-474d-8619-984414647f9d)

5. **Preparing Data:** Executed rigorous data preparation, involving handling missing data, one-hot encoding categorical features, addressing multicollinearity through VIF testing, detecting and removing outliers using isolation forests. Additionally, I applied feature scaling using Standard Scaler and MinMax Scaler to ensure compatibility with machine learning models, and employed feature selection utilizing LASSO to mitigate noise in the data and enhance the predictive power of the models.

### Models used for Regression
All of the models tested during the project underwent accuracy performance evaluation through Grid Search cross-validation. Here is a breakdown of model results:

- **Linear Regression:** The Linear Regression model was identified as the least performer among the models, highlighting its limitations in capturing the complexity of the underlying patterns in the dataset.

- **Decision Tree Regressor:** The Decision Tree model was the second worst performer, exhibiting a tendency to overfit the training data, leading to suboptimal generalization.

- **Gradient Boosting Regressor:** The Gradient Boosting model was the second best performer, substantially outperforming the decision tree and the linear regression models.

- **Random Forest Regressor:** The Random Forest model emerged as the best performer, showing superior predictive accuracy. To strike a balance between predictive accuracy and unseen data generalization, the model underwent hyperparameter tuning, involving fine-tuning parameters such as max_depth, min_samples_leaf, min_samples_split, and n_estimators using a combination of Grid Search CV and Randomized Search CV.


### Causal Inference
Evaluated the effect of hot weather on the hourly demand for bikes by employing causal inference using Light Gradient Boosting (LGBM) and XGBoost with the S,T, and X meta-learners. Using model AUUC (Area Under the Uplift Curve) scores as the evaluation metric, the T-learner with LGBM emerged as the as the best model for explaining the causal impact of hot weather on bike demand.

*Figure: AUUC Plot of the S, T, X, and Random Meta-Learners using LGBM*
![image](https://github.com/MohamedElenany/Bike-Sharing-Demand-Prediction/assets/89152453/bb6f10e3-74a5-4ee9-91c0-3af5f39d3afd)

## Results
- **Regression Model:** The Random Forest Regressor emerged as the most proficient model for predicting hourly bike demand by having the lowest test set Mean Squared Error (MSE) of 26738.55.
- **Causal Inference Model:** The T-learner with LGBM achieved the highest AUUC score of 0.74, providing a nuanced understanding of the causal relationship between hot weather and bikesharing demand.
  
## Causal Inference Insights:
Here are some major insights about the causal relationship between hot weather and the hourly bikesharing demand identified using causal inference:
- The analysis revealed an Average Treatment Effect (ATE) of 512, indicating an average increase in hourly bike demand of 512 bikes during hot weather compared to cold weather.
- The top predictive features identified during feature importance analysis in hot weather include Solar Radiation, Autumn, Humidity, and Spring.
- Shap Value analysis offered detailed insights into feature importance. Taking the example of 'Solar Radiation,' lower levels were associated with a negative Shap value, indicating a decrease in demand. Conversely, higher radiation levels corresponding to hotter weather yielded a positive Shap value, suggesting an increase in demand due to the rise in solar radiation.

These insights from causal inference provide crucial input for strategic business decisions, enabling a thorough understanding of the factors driving bikesharing demand.

*Figure: Hot Weather Treatment on Hourly Bike Demand Feature Importances*
![image](https://github.com/MohamedElenany/Bike-Sharing-Demand-Prediction/assets/89152453/deeff2f3-5aea-4c12-afe3-4223be12398a)

*Figure: Hot Weather Treatment on Hourly Bike Demand Feature Shap Values*
![image](https://github.com/MohamedElenany/Bike-Sharing-Demand-Prediction/assets/89152453/a6175b5a-2bce-458e-8644-f23d867c3424)


## Business Value and Applicability
By providing the bikesharing business with precise demand predictions and a nuanced understanding of the impact of weather temperature on bike demand, here are some valuable practical uses of such a project:
* The findings of this project directly benefit bikesharing service providers, urban planners, and policymakers.
* The project empowers strategic decision-making in areas such as marketing, service optimization, and infrastructure planning, contributing to an enhanced user experience and operational efficiency.
* The understanding of demand factors enables proactive management, ensuring an optimal supply of bikes during peak hours and favorable weather conditions.

*Thus, the findings would empower the business to develop a more responsive, efficient, and user-centric bikesharing system, aligning seamlessly with the evolving needs of the urban community.*
## Dataset Source
The project utilizes the "Seoul Bike Sharing Demand" dataset from the UCI Machine Learning Repository. This dataset contains hourly counts of public bicycles rented in the Seoul Bike Sharing System, complemented by corresponding weather data and holiday information.
