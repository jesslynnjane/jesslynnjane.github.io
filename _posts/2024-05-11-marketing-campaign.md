---
layout: article
title: "Data Science: Marketing Campaign"
share: true
modified: 2017-02-12T14:18:57-04:00
image:
    teaser: marketing-campaign.png
categories: portofolio
---

*A project aimed to create a predictive classifciation model to identify the appropriate users for the upcoming campaign.*

<strong>Authors: Jesslyn Jane, Aditya Ridwan, Ann Sinaga, Lhutfia Ichsan, Mustiadi Zakki, M. Triargi</strong>. This is a project I have worked through as part of the final capstone in [Rakamin Academy: Data Science Bootcamp](https://www.rakamin.com/job-guarantee-bootcamp/data-science). 

[Github](https://github.com/Triargi/project_repo) | [Google Colab](http://localhost:8888/lab/tree/Documents/-Jeje-/-Rakamin-/Final_Project_Group9_Halcyon.ipynb) | [PPT](https://drive.google.com/file/d/1T77LtLIkWN8fb7LBPpI46ZkMPaJQmB5e/view?usp=sharing) | [All Processes](https://drive.google.com/drive/folders/1VtyL13TSufB3XsdLRxPZuVIMI_-8wlDU)


# Introduction 
​
PT Halcyon is a company operating in the marketing industry as a marketing consultant company. The company is known to have an acceptance rate for marketing campaigns of around 14.91%, which is still considered low by management in facing business competition.

Therefore, the management has requested the marketing team to further increase the acceptance rate for marketing campaigns so that the costs incurred by the company in conducting marketing campaigns are more efficient and the amount of revenue they achieve in the following years increases.

Hence, the marketing team plans to implement Targeted Marketing strategy with the assistance of the data science team to process historical sales data that they have previously compiled and group users into specific categories according to their respective characteristics, so that they can distinguish between those who are eligible for the campaign and those who are not eligible for the campaign.

## Goal

Increase the response rate to the company's campaigns can lead to higher profits for the company.

## Objective

Create a predictive classification model system that can determine the appropriate target users. This will certainly increase the value of predefined business metrics such as traffic and sales performance. The system will identify which users are genuinely interested or part of the target market for the upcoming campaign.

## Business Metrics
- Response rate
- Revenue rate

# Exploratory Data Analysis (EDA)
## Descriptive Analysis
The [dataset](https://www.kaggle.com/datasets/rodsaldanha/arketing-campaign) consists of 28 features and 1 target variable, which is Response (the ratio of the number of customers who respond compared to the total impressions of the campaign).

## Univariate Analysis
![eda numerik](/images/git1.PNG)

Using a boxplot, outliers were found in the features Year_Birth and Income.

![eda numerik](/images/git2.PNG)

Additionally, outliers were also found in the features related to purchases of goods ('MntWines', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds').

![eda numerik](/images/git3.PNG)

Similarly, outliers were also identified in the features related to purchases ('NumWebPurchases', 'NumCatalogPurchases', 'NumStorePurchases', 'NumWebVisitsMonth').

![eda response](/images/git4.PNG)

In the category plot, an interesting insight was found regarding the response feature, indicating an imbalance between customers who responded and those who did not respond. This suggests the presence of class imbalance, necessitating over/undersampling during the pre-processing stage.

## Multivariate Analysis
![eda heatmap](/images/heatmap.png)
From the heatmap plot, it can be seen that the features AcceptedCmp1 and AcceptedCmp5 have the highest correlation with the target response, with respective values of 0.33 and 0.29.

Below are some features that we are likely to retain and use for future analysis:
- Recency
- MntWines
- MntMeatProducts
- NumCatalogPurchases
- AcceptedCmp3
- AcceptedCmp5
- AcceptedCmp1

From all the correlations between features and the target, they all range from 0.00 to 0.33. Therefore, we decided to set a threshold value at 0.20. The features listed above that we retained are those with correlation values >0.20.

Furthermore, based on the initial analysis of feature-to-feature relationships that we conducted for features with higher correlations with the target, we obtained the following results:

From these results, it is highly likely that they will be prioritized as features in the decision-making process for determining which customers are eligible for campaigns.

# Business Insights & Recommendations
## Business Insights
- What is the influence of having kidhome and teenhome on customer response rates?
<img width="240" alt="image" src="https://user-images.githubusercontent.com/88579085/212469071-dcc51597-7187-4304-bb56-0b508b9f4ff3.png">
<img width="442" alt="image" src="https://user-images.githubusercontent.com/88579085/212469081-afb0c656-ee40-47a8-9b13-81a6829ac992.png">
<img width="432" alt="image" src="https://user-images.githubusercontent.com/88579085/212469095-d0848247-7312-43ff-ba11-1125d3c55b4d.png">

- What is the percentage of customers who Responded and Did Not Respond based on marital status?
<img width="728" alt="image" src="https://user-images.githubusercontent.com/88579085/212469194-ef9914e6-2a94-40e0-ba3b-9de3a57d4126.png">

- What is the percentage of customers who Responded and Did Not Respond based on education level?
<img width="709" alt="image" src="https://user-images.githubusercontent.com/88579085/212469226-864b4796-1dae-4a4d-8e37-457ca67c6150.png">

## Business Recommendations
Based on the visualization, the Data Science team can provide recommendations for the marketing team, such as:

- From the kidhome and teenhome visualization, it can be seen that the majority of respondents come from customers who do not have children or teenagers, so the marketing team can focus campaigns on customers without children or teenagers.
- From the Marital Status pie chart, it can be seen that the majority of respondents come from customers with "Absurd" (50%) and "Yolo" (50%) marital statuses, followed by "Alone" (33%) and "Widow" (25%), so the marketing team can focus campaigns on "Absurd" and "Yolo" customers.
- From the Education pie chart, it can be seen that the majority of respondents come from customers with a PhD (20.78%) education level, followed by Master's (15.41%), so the marketing team can focus campaigns on customers with a "PhD" education level.

### Next Improvement
In addition to the three business insights, we also have one more insight regarding a trend of a product that has a strong correlation (Gold, Meat, and Wines) with campaigns 1 through 5. Then, the results of visualizing this insight can be used by the company to prioritize which products to sell or promote in order to attract more customers. Therefore, it is hoped that with an increase in the number of customers, the company's revenue will also increase.

However, due to time constraints, we have not had the opportunity to create visualizations for this last insight and plan to make it a next improvement.

# Data PreProcessing
## Data Cleansing & Feature Engineering
### Handle Missing Values
<img width="169" alt="image" src="https://user-images.githubusercontent.com/88579085/213911728-2146d73b-5ae0-4b7c-8e5b-07dc220b363b.png">

Based on the initial analysis, it can be observed that there are missing data in the income column totaling 24 rows, with a percentage of 1.07% of the total data, which is far below the safe data deletion threshold (10%). Therefore, the decision we made regarding the missing value is to delete all rows in the Income column with null (empty) values.
<img width="300" alt="image" src="https://user-images.githubusercontent.com/88579085/213911819-aae8c1b5-28bd-4f75-ac5b-ac2d2a48e052.png">

### Handle Duplicated Data
> Based on the checking results, no duplicated data rows were found. Therefore, we do not need to handle duplicated data.

### Handle Outliers
<img width="642" alt="image" src="https://user-images.githubusercontent.com/88579085/213911867-96706d1e-ad23-457e-a1ab-eac426bcbd3b.png">
<img width="645" alt="image" src="https://user-images.githubusercontent.com/88579085/213911878-635a87b3-cc62-4ff4-bbda-a708ca3dce4c.png">
<img width="648" alt="image" src="https://user-images.githubusercontent.com/88579085/213911900-b849123e-2692-4ba8-b56a-ede8f51c1c7c.png">

Based on the plots shown above, outliers exist in the 'Income', 'Year_Birth', 'Recency', 'MntWines', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds', 'NumDealsPurchases', 'NumWebPurchases', 'NumWebVisitsMonth' features. Therefore, we made corrections to these features using the Z-score method and also the IQR method to minimize the number of outliers contained in the dataset.

#### Remove Outliers berdasarkan Z-score
<img width="266" alt="image" src="https://user-images.githubusercontent.com/88579085/213911935-f124f965-9aef-4ae7-b34f-0c9f360786b7.png">

#### Remove Outliers berdasarkan IQR
<img width="271" alt="image" src="https://user-images.githubusercontent.com/88579085/213911947-9f947ea7-ed65-4aec-adea-59423e98a1ef.png">
Based on the calculations using Z-score and IQR, it can be seen that the number of rows deleted based on IQR is much higher than based on Z-score, which is about >30% of the total data rows deleted. Therefore, we decided to choose the Z-score method for removing outlier rows.

After that, we plotted boxplots to re-examine the distribution of outliers in each feature.
<img width="651" alt="image" src="https://user-images.githubusercontent.com/88579085/213911967-c2489736-df69-4b58-a54f-e7392315e145.png">
<img width="650" alt="image" src="https://user-images.githubusercontent.com/88579085/213911972-24b2d496-c0f4-4105-86dc-c10e1c743504.png">
<img width="654" alt="image" src="https://user-images.githubusercontent.com/88579085/213911983-2aa5c3f2-3c03-4c77-81c7-ff9026c166ec.png">

### Feature Transformation
<img width="940" alt="image" src="https://user-images.githubusercontent.com/88579085/213912057-41853e15-6707-4fa8-8768-a374abe8b230.png">
<img width="943" alt="image" src="https://user-images.githubusercontent.com/88579085/213912067-c4bfcb6b-83cf-480f-aab1-e82c8bde63c2.png">
<img width="929" alt="image" src="https://user-images.githubusercontent.com/88579085/213912078-e9783b68-a1f2-461d-8cd9-67fad33ed8cd.png">

Based on the plots shown above, there is positively skewed data in the 'MntWines', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds', 'NumDealsPurchases', 'NumWebPurchases', 'NumCatalogPurchases' features. Therefore, we made adjustments to these features using the log transformation method.

<img width="368" alt="image" src="https://user-images.githubusercontent.com/88579085/213912103-c0130629-21da-418f-a34f-3ed39eb5e2fe.png">

#### Log Transformation
<img width="953" alt="image" src="https://user-images.githubusercontent.com/88579085/213912234-700d41b6-fe25-47ab-8478-1eb90856cc61.png">
<img width="948" alt="image" src="https://user-images.githubusercontent.com/88579085/213912244-494b6d9b-0161-43be-a044-83de8e7f4459.png">
<img width="472" alt="image" src="https://user-images.githubusercontent.com/88579085/213912251-b0e34142-3e8a-4c9f-a942-c171e3592034.png">
<img width="372" alt="image" src="https://user-images.githubusercontent.com/88579085/213912259-69ad4a1e-2343-4043-b622-1bf38437860f.png">

Based on the re-check of some features that have been processed using the log transformation previously, it can be seen that all skewness values ​​now have a more uniform range (not too far and not too varied). Therefore, it can be concluded that the feature transformation technique we have done is valid, and we decided to create a new column with the filled values ​​of the features that have been processed.

<img width="962" alt="image" src="https://user-images.githubusercontent.com/88579085/213912286-08069ad1-9bf0-494b-b3c1-f27aa8540d32.png">

### Feature Encoding
After performing feature transformation, here we also decided to perform feature encoding on columns that have categorical data types to be converted into numerical. We did this in the hope of improving the machine learning capabilities we would create later. Below are some features we processed at this stage:

1. Mapping_marital, based on Marital_status
2. Mapping_education, based on Education

#### Label Encoding
Mapping_marital, based on Marital_status
![image](https://user-images.githubusercontent.com/88579085/213912402-e830deeb-3d11-4ee3-a498-5a6ea691ec51.png)
Mapping_education, based on Education
![image](https://user-images.githubusercontent.com/88579085/213912429-d8836507-690d-4e2c-85d7-830f44a9b5aa.png)

#### One Hot Encoding
<img width="666" alt="image" src="https://user-images.githubusercontent.com/88579085/213912485-7b434af6-d506-4205-aad0-96fec4a946bd.png">

<img width="213" alt="image" src="https://user-images.githubusercontent.com/88579085/213912490-3bf70fe7-570f-4f66-9f99-47051bed50a9.png">

<img width="295" alt="image" src="https://user-images.githubusercontent.com/88579085/213912511-be28f70e-9f51-4300-beb9-5115176f417f.png">

### Feature Extraction
> After performing feature encoding, we also decided to perform feature extraction at this stage. We did this with the aim of facilitating the feature selection step that would be done next. Below are some features we created at this stage:

1. primer_purchase & tersier_purchase, a feature that combines columns of fruit, meat, and fish purchases, wine, sweet food, and gold into 2 groups, namely primary and tertiary.
2. total_accepted_campaign, a feature that combines acceptedcmp 1 - 5. This feature was created to see the intensity of customers in accepting campaigns from all campaigns previously carried out by the company.
3. total_revenue, a feature created by summing the total acceptance of customers in all previous campaigns (1-5) with the amount of revenue per accepted campaign.
4. total_spent, a feature that combines total purchases of various products ranging from wines, fruits, meats, fish, sweets, to gold to summarize the total expenses incurred by each customer.
5. total_order, a feature containing a summary of the total purchases or orders made by customers from various purchase methods.
6. month_customer, the month when customers start enrolling/registering for marketing campaigns.
7. age, a feature that categorizes customers into 3 age groups, namely: Elderly (2), Middle Age (1), and Young (0).
8. income_category, a feature that categorizes customers based on their income into 3 categories, namely High-Income (2), Mid-Income (1), and Low-Income (0)
9. total_dependents, a feature that combines marital status, kidhome, and teen home columns to see the number of people in 1 household considered as household dependents.

All of these features will be re-evaluated during feature selection to see how much influence they have on the target or the probability of customer response in a campaign.

Primer and tersier product
<img width="988" alt="image" src="https://user-images.githubusercontent.com/88579085/213912690-e76e8fcf-8c03-4d48-8e47-e5b69ebb7246.png">

Total accepted campaign
<img width="975" alt="image" src="https://user-images.githubusercontent.com/88579085/213912707-8c64d389-8496-4a52-af79-7dea33cc883c.png">

Total revenue
<img width="170" alt="image" src="https://user-images.githubusercontent.com/88579085/213912721-564e455a-0025-4226-967f-509677265208.png">

Total spent
<img width="987" alt="image" src="https://user-images.githubusercontent.com/88579085/213912730-91ae3c72-afec-44f2-ab50-25716a66c50b.png">

Total purchase/total order
<img width="967" alt="image" src="https://user-images.githubusercontent.com/88579085/213912750-144c7039-ba13-4002-be49-d5816ddbfe58.png">

Convert the date of enrolment to datetime
<img width="976" alt="image" src="https://user-images.githubusercontent.com/88579085/213912791-dd594ae2-c7da-480d-808c-118a057d6d14.png">

Age_category customer according to WHO:
<img width="968" alt="image" src="https://user-images.githubusercontent.com/88579085/213912827-a6ff8999-f82b-4f63-aec9-36f7a262c733.png">

<img width="183" alt="image" src="https://user-images.githubusercontent.com/88579085/213912832-6045c4e1-358b-454a-9dc0-e6cf74c988b5.png">

Income Category
<img width="974" alt="image" src="https://user-images.githubusercontent.com/88579085/213912856-bf69b2a8-d894-423a-9f31-622dcf95fe13.png">

Total Dependants
<img width="977" alt="image" src="https://user-images.githubusercontent.com/88579085/213912878-2251be60-db6b-4bec-9b88-79bebba6344c.png">

<img width="283" alt="image" src="https://user-images.githubusercontent.com/88579085/213912893-1979e639-e1dd-4816-b76e-92d4b216076f.png">

### Feature Selection
After performing feature extraction, at this stage is when we select some features that we consider less important, especially those with low correlations with the target or other features. We did this to facilitate the ML learning process we would create later.

The images below show the heatmap before performing feature selection. The image after shows the heatmap after performing feature selection. We set the threshold at 0.19 where above the threshold, the correlation of the feature with the target is quite high, so the feature is taken. Meanwhile, feature-target with correlation <0.19 is not taken.

Before

<img width="647" alt="image" src="https://user-images.githubusercontent.com/88579085/213912951-ef645a87-f70b-435d-b525-d2777a8392b0.png">

After

<img width="653" alt="image" src="https://user-images.githubusercontent.com/88579085/213912977-26285817-2f5f-465a-b514-b264786e5f94.png">

### Handle Class Imbalance
Ratio Check for target

<img width="148" alt="image" src="https://user-images.githubusercontent.com/88579085/213912995-a3dedb0c-2462-473d-9f37-420bf8e04874.png">
<img width="162" alt="image" src="https://user-images.githubusercontent.com/88579085/213913002-a4e669cd-8f54-4427-8b0c-281bb3a71eed.png">

Use oversampling

<img width="73" alt="image" src="https://user-images.githubusercontent.com/88579085/213913020-755e076f-0114-4c78-aab3-c7a1168736fe.png">

Due to the presence of class imbalance or a very far data imbalance in the target column (response) and the number of samples learned by ML is more (1692 samples), therefore we decided to use oversampling to handle this problem.

### Additional Feature 
1. ***Area/ Region***: The location of the customer's residence can affect the customer's response rate to product purchases. The closer they live to the city center, the fewer responses they may have because of the many campaign competitions from other markets around the city.
2. ***Time call***:  Time when called: during working hours or break time.
3. ***Day call***: Day when called: weekend/weekday.
4. ***Payment method***: Payment method used for purchasing goods: credit card/COD/bank transfer/e-money. Customers who use credit card methods may have a higher response rate than other payment methods.
5. ***Job position***: The type of job of the customer can affect the campaign response rate: student/professional/unemployed.

# ML Modelling & Evaluation
## Data Preparation
Before modeling, we split the data first to separate between training data (70%) and test data (30%).

Then, because there was an intermediate class imbalance in the target data, we decided to perform oversampling so that the machine learning algorithm or model we created could learn the data more balancedly.

## Default Modelling
At this stage, we conducted exploration using all algorithms previously taught with the following results:
![Modelling](/images/marketing-campaign_model1.png)

Based on these results, we decided to delve deeper into 3 algorithms with the best precision and recall results, namely Decision Tree, Random Forest, and XGBoost.

After further exploration with Hyperparameter Tuning on Decision Tree, Random Forest, and XGBoost, here is the summary of the final performance obtained:
![Modelling](/images/marketing-campaign_model2.png)

Based on the consideration of precision train value, recall, and the train-test gap obtained in these three models, it can be concluded that the most optimal model we obtained is Random Forest. This is because the model produces output with the highest precision and recall metrics values. Additionally, this model also tends to be the best fit, making it a suitable choice.

## Feature Importance
From the previously selected modeling results, the following feature importance was obtained, which influences whether customers will respond to the campaign or not.
![Modelling](/images/marketing-campaign_model3.png)

# Recommendation
## Income
![Modelling](/images/marketing-campaign_model4.png)
Based on the visualization results displayed above, we recommend the company to focus more on the campaign towards customers with income above 70000 to enhance campaign response. Additionally, to increase traffic, the company can implement a loyalty system by offering special points to customers meeting this criteria. These points can be redeemed for various attractive rewards such as discounts or free product offerings.

## Recency
![Modelling](/images/marketing-campaign_model5.png)
Based on the visualization results above, in the future, the company can focus more on the campaign towards customers who have recently made purchases close to the time of the upcoming campaign.

Furthermore, in the future, the company should also pay more attention to reaching out to customers who haven't shopped for a long time or who have never shopped before by offering special promotions such as new user discount vouchers, old user discount vouchers, etc. Additionally, the company can conduct direct monthly promotions (like 2.2, 3.3, etc.) to maintain customer traffic by establishing a monthly shopping habit. Lastly, the company can also invest in placing e-billboards or other ads aimed at attracting new users in general.

## Total Spent
![Modelling](/images/marketing-campaign_model6.png)
Based on the visualization results above, in the future, the company can offer special campaigns to customers who have the highest total spent before the upcoming campaign period.

Additionally, the company needs to increase customers' total spending by improving and maintaining the quality of the products sold, for example, by consistently offering fresh produce such as fruits, fish, and meat. Moreover, the company can provide special promotions using the "up-selling/cross-selling" strategy, offering additional discounts on supporting products related to the items purchased by customers. Finally, the company can also offer special vouchers to customers with a minimum spending requirement.

[Github](https://github.com/Triargi/project_repo) | [Google Colab](http://localhost:8888/lab/tree/Documents/-Jeje-/-Rakamin-/Final_Project_Group9_Halcyon.ipynb) | [PPT](https://drive.google.com/file/d/1T77LtLIkWN8fb7LBPpI46ZkMPaJQmB5e/view?usp=sharing) | [All Processes](https://drive.google.com/drive/folders/1VtyL13TSufB3XsdLRxPZuVIMI_-8wlDU)