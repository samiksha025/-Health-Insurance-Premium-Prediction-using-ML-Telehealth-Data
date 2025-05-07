# -Health-Insurance-Premium-Prediction-using-ML-Telehealth-Data
**Introduction:**
Health insurance providers face challenges in accurately pricing premiums due to reliance on static demographic and actuarial tables, which often overlook personalized health data and behavioral patterns like telehealth usage. This leads to inequitable and opaque premium estimates. Our primary stakeholder, a health insurance provider, requires an automated, transparent, and fair pricing model to better assess risk and offer customers understandable premium estimates.

Our solution leverages machine learning to predict premiums using personal health attributes (e.g., chronic conditions, BMI) and telehealth engagement metrics. By incorporating real-world behaviors and health indicators, our model aims to improve accuracy (targeting ≥85% prediction accuracy) and transparency, addressing the stakeholder’s need for equitable pricing and risk assessment.

**Literature Review:**
>> Current Methods in Medical Insurance Premium Prediction: Traditionally, medical insurance premiums have been determined using actuarial models that assess risk based on demographic factors, medical history, and lifestyle choices. These models often employ statistical techniques such as linear regression to estimate costs. However, recent studies have explored the application of machine learning (ML) techniques to enhance prediction accuracy and provide more personalized premium assessments.

For instance, a study by Orji and Ukwandu (2024) deployed ensemble ML models, including Extreme Gradient Boosting (XGBoost), Gradient Boosting Machine (GBM), and Random Forest, to predict medical insurance costs. They utilized explainable artificial intelligence methods to identify key factors influencing premium prices, demonstrating that ML models can outperform traditional actuarial approaches in predictive accuracy and interpretability [^1].

Another research effort by Cenita et al. (2023) evaluated the performance of regression models such as Linear Regression, Gradient Boosting, and Support Vector Machine in predicting medical insurance costs. Their findings indicated that Gradient Boosting achieved the highest R² score and the lowest Root Mean Square Error (RMSE), suggesting its superiority over other models in capturing complex relationships within the data [^2].

Despite these advancements, current ML approaches face limitations, including challenges in model interpretability, potential overfitting, and the need for large, high-quality datasets. Additionally, many models do not account for temporal changes in healthcare costs or integrate real-time data, which can affect their predictive accuracy.

**Relevance to Stakeholder Needs:**
Our literature review justifies the chosen methods:

Insurers: ML models automate pricing while improving accuracy (Wuthrich & Merz, 2021).
Policyholders: SHAP visualizations (Lundberg & Lee, 2017) provide transparency into premium calculations.
Regulators: Bias audits (Chen et al., 2018) ensure compliance with fairness laws.
Key References:

Bühlmann, H., & Gisler, A. (2005). A Course in Credibility Theory. Springer.
Chen, J., et al. (2018). Fairness in Machine Learning. NeurIPS.
Lundberg, S., & Lee, S. (2017). A Unified Approach to Interpreting Model Predictions. NeurIPS.
Wuthrich, M., & Merz, M. (2021). Statistical Foundations of Actuarial Learning. SSRN.
Data and Methods:

**Data:**
Source: CMS

The Medicare telehealth and beneficiary health dataset provides a comprehensive picture of beneficiary characteristics, health conditions, healthcare utilization, and insurance metrics. The dataset integrates standard Medicare enrollment data with detailed health status information and telehealth usage statistics.

**Key Variable Categories The dataset includes the following major variable categories:**
>>Demographic Information
Age: Beneficiary age in years
Height and Weight: Physical measurements in cm and kg respectively
Geographic Variables: Beneficiary geographic location and rural/urban status (in the original Medicare data)
Race/Ethnicity and Sex: Standard demographic identifiers (in the original Medicare data)

>>Health Status Indicators
Chronic Disease Status: Binary indicator (0/1) for presence of chronic conditions
Diabetes Status: Binary indicator (0/1) for diabetes
Blood Pressure Status: Binary indicator (0/1) for hypertension
Transplant History: Binary indicator (0/1) for past organ transplantation
Allergies: Binary indicator (0/1) for presence of known allergies
Family Cancer History: Binary indicator (0/1) for cancer in family medical history
Surgical History: Count of major surgeries the beneficiary has undergone

>>Insurance and Financial Information Premium Price: Medicare premium cost in dollars
Part B Enrollment: Total Medicare Part B enrollment figures

>>Telehealth Utilization Metrics
Telehealth Eligible Total: Number of beneficiaries eligible for telehealth services
Telehealth Usage Total: Number of beneficiaries who actually used telehealth services
Telehealth Usage Percentage: Proportion of eligible beneficiaries utilizing telehealth (values between 0-1)

**Methods:**
Preprocessing:
In this stage, we prepared the data for modeling:

Removed any duplicate records to ensure unique entries.
Handled missing values introduced during simulation using median imputation, which is robust to outliers.
Enforced consistent data types (e.g., all binary features as integers) to maintain compatibility with ML algorithms. These steps ensure that the model receives clean, well-structured data for training.
EDA Analysis:
In this section, we analyze the distribution and relationships between our variables.

The histogram helps us understand the skewness and spread of premium_price.
The heatmap reveals correlations, helping us identify highly related features (e.g. weight vs. premium).
The histogram visualization to reveal the multimodal distribution of premium prices
The pairplot visualizations to examine the interactions between multiple demographic and health variables simultaneously.
In-Depth EDA Analysis:
1) Premium Distribution by Health Group
The box plot visualization (Image 3) clearly demonstrates premium variation across health status groups:
Chronic + No Diabetes: Highest median premium (approx. $27,000) with a relatively narrow IQR
No Chronic + No Diabetes: Lowest median premium (approx. $22,000) with the widest IQR, suggesting more premium variability in this group
Chronic + Diabetes: Moderate-high median premium (approx. $25,000)
No Chronic + Diabetes: Moderate median premium (approx. $24,000)
This analysis reveals that chronic conditions appear to impact premium costs more significantly than diabetes alone. The presence of a chronic condition is associated with approximately $3,000-$5,000 higher median premiums, while diabetes without chronic conditions adds approximately $2,000 to median premiums.

2) Telehealth Usage Distribution
The scatter plot visualization (Image 2) provides deeper insights into telehealth usage patterns:
Distinct Usage Clusters: There are noticeable clusters around 20%, 40-45%, and 50-60% telehealth utilization.
Premium Distribution: Premium prices range from approximately $13,000 to $41,000, with most concentration between $20,000-$35,000.
Health Status Impact: Yellow points (indicating presence of chronic disease) appear more frequently in higher telehealth usage ranges (45-60%), suggesting patients with chronic conditions may be slightly more likely to be high telehealth users.
Surgical Correlation: The bubble sizes (representing number of surgeries) show that beneficiaries with higher surgical intervention rates span across all telehealth usage percentages but tend to be concentrated in the 40-50% usage range.
The clustering pattern rather than an even distribution suggests specific barriers or enablers to telehealth adoption among certain beneficiary segments. These might include technology access, provider practice patterns, specific clinical conditions, or reimbursement policies.

3) Pairwise Feature Relationships
The pairplot visualizations provide detailed insights into the pairwise relationships between key variables:
Age Distribution by Diabetes Status: The age distribution shows that non-diabetic beneficiaries (green points) have a higher density at younger ages compared to diabetic beneficiaries (orange points), who skew slightly older.
Weight-Diabetes Relationship: Diabetic beneficiaries show a higher concentration in the upper weight ranges, consistent with the known association between weight and Type 2 diabetes.
Premium-Age Relationship: The scatterplot between age and premium shows a positive correlation that is stronger in middle age ranges (35-60) than at the extremes.
Premium Distribution by Diabetes: The premium distribution density curves show that diabetic beneficiaries have a slightly higher concentration in the upper premium ranges compared to non-diabetic beneficiaries.
These pairwise comparisons effectively illustrate how various demographic and health factors correlate with each other and with premium costs, revealing subtle patterns that might not be apparent in aggregate statistics.

**Modeling:**

Random Forest: Chosen for handling non-linear relationships and feature importance.
SHAP: Applied to explain predictions and ensure transparency.
Evaluation: 5-fold cross-validation with RMSE (USD) and R² scores.
Notebooks:

data_wrangling.ipynb: Cleaning and feature engineering.
model_training.ipynb: Hyperparameter tuning (GridSearchCV).
shap_analysis.ipynb: Interpretability visualizations.

**Final Outcomes:**
Our results were as follows: Random Forest gave the best performance with an R² score of 0.81, MAE around 1774, and the lowest RMSE. That means it was both accurate and consistent.

LightGBM, after hyperparameter tuning using GridSearchCV, came very close with an R² of 0.80 and slightly higher MAE and RMSE than Random Forest.

XGBoost, without tuning, had an R² of 0.78, which is still solid, but not quite as competitive as the other two for our data.

So, Random Forest was selected as our best model overall. 
![image](https://github.com/user-attachments/assets/e5fbd8e4-ce9f-43fb-947a-94e269eb0c87)


Why This Matters (SHAP) For example, if a customer questions why their premium is high, this plot shows it's likely due to a combination of their age, health status, and healthcare usage patterns This transparency is not just helpful — it’s increasingly required by regulators and expected by customers.

Metrics:
Mean Absolute Error (MAE): $1,774.63 Root Mean Squared Error (RMSE): $2,751.09 R-squared (R²): 0.81, indicating that 81% of the variance in premium prices can be explained by our model. Cross-Validation: We used 5-fold cross-validation to ensure the robustness of our metrics.

Feature Importance:
The top 5 most influential features in predicting insurance costs were:
-Age
-Weight (kg)
-Presence of chronic disease
-Telehealth usage percentage
-Major surgeries count

**Visualizations:**

Age v/s Premium Density Plot: Illustrated the relative impact of 'Age' feature on Premium cost.
![image](https://github.com/user-attachments/assets/d7f1675c-06d4-4a17-a177-0190c8c79131)

Premium Distribution by Combined Health Group: Visualized how different health risk groups influence the spread and central tendency of premium costs.
![image](https://github.com/user-attachments/assets/61effb30-a511-4160-97dc-a2b6254d32f3)

Telehealth Usage v/s Premium: Depicted the relationship between telehealth utilization rates and corresponding premium costs.
![image](https://github.com/user-attachments/assets/f2f8ea54-1453-4446-86eb-f8ba2284f84b)

Feature v/s SHAP value (Impact on model output): Highlighted each feature’s contribution to individual predictions, revealing their influence on the model's output. image

Discussion:
Achievement of Goals:
We successfully developed a predictive model for medical insurance costs with an R² of 0.81, indicating strong predictive power. The model addresses the stakeholder's need for accurate cost predictions to improve pricing models and enhance cost awareness for individuals.

Stakeholder Needs:
Insurers: The model provides a data-driven approach to pricing, potentially reducing risk and improving profitability. Individuals: Users can estimate their insurance costs based on personal health metrics, promoting transparency.

Gaps:
While the model performs well, it does not yet account for external factors like regional healthcare costs or inflation, which could further refine predictions.

Limitations:

Data Quality: The dataset had missing values, which were imputed using median values. This may introduce bias.
Feature Scope: The model does not include external economic factors (e.g., regional healthcare costs) or lifestyle data (e.g., smoking status), which could improve accuracy.
Generalizability: The model is trained on Medicare data, which may not generalize well to younger populations or private insurance schemes.
Prototype Limitations:
The current prototype is a static application; a dynamic version with real-time data integration would be more useful.

Future Work:

Incorporate Additional Data: Expand the dataset to include lifestyle factors, regional cost variations, and more detailed telehealth metrics.
Model Enhancement: Experiment with ensemble methods to improve predictive performance. -Real-Time Prototype: Develop a fully interactive web application with real-time data processing and user feedback integration.
Explainability: Implement SHAP (SHapley Additive exPlanations) to provide users with interpretable insights into how each feature affects their predicted cost.
Longitudinal Study: Validate the model over time to assess its stability and adaptability to changing healthcare trends.


