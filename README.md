# airbnb-ML
Predicting Customers for Airbnb Listings in Seattle

# Practical Motivation
If our goal is to establish an Airbnb listing in Seattle and attract the highest number of customers, what are the essential factors or predictors that require adjustments or careful attention?


# Response 
We encountered an initial challenge when selecting a response column: No immediate columns displayed the number of customers per listing. Consequently, we addressed this by performing feature engineering. We utilized the count of reviews for each listing to estimate its customer count. This approach is justified, given that Airbnb representatives have noted a 72% review rate among guests. Therefore, the review count serves as a reasonable proxy for estimating customer numbers.

Ultimately, we employed two response columns:

    Reviews/Month: Reflects the monthly review rate for each listing.
    Total Reviews per Listing Age: Obtained by dividing the total reviews a listing has received by its duration on Airbnb up until the data collection date.

Both values were extracted from the "listings.csv" dataset.

# Data Types of Variables selected
This outline presents the comprehensive data cleaning and feature engineering process, focusing solely on the "listings.csv" and "reviews.csv" datasets. Our efforts resulted in the creation of five distinct predictor groups highlighted in yellow, aimed at predicting two responses: "reviews/month" and "reviews/day".
<img src="https://github.com/ytia001/airbnb-ML/assets/136459037/ac1f8e38-c66d-4dbb-ab98-631481488904" alt="Image" width="700">


# Features used and details:

## Positive/Negative Word Count 
For one of our predictors, we aimed to analyze the textual comments to extract positive and negative reviews. To achieve this, we obtained a list of words associated with positive and negative sentiments. We then processed the "reviews.csv" dataset through this list to categorize the comments.
<img src="https://github.com/ytia001/airbnb-ML/assets/136459037/9757667c-eed7-4d12-869b-ccf6b87518d1" alt="Image" width="400">

By subtracting the total count of negative words from positive words for each listing, we generated a new numerical column representing the difference between positive and negative word usage.
<img src="https://github.com/ytia001/airbnb-ML/assets/136459037/0fbd0a2e-115f-4d77-8418-f0f22634a18c" alt="Image" width="400">

An important point to acknowledge is that this method does not address phrases. For instance, if a phrase like "NOT clean" was used, the code would only recognize "clean" and register it as positive.

## One Hot / Integer Encoding
We employed both one-hot encoding and integer encoding during our data cleaning process. This was essential because the Airbnb datasets encompassed a mix of numeric, categorical, and non-numeric and non-categorical variables, like amenities.

Our regression models, such as linear regression and random forest regression, exclusively accept numeric inputs. Hence, we utilized these encoding techniques to transform categorical values into numerical formats suitable for these models. Moreover, we utilized one-hot encoding to break down valuable variables like amenities – which don't fall strictly into categorical or numerical categories – into distinct variables. This allowed us to integrate them effectively into the models.

For categorical variables with a substantial number of distinct values, we opted for one-hot encoding. On the other hand, categorical variables with fewer unique values were subjected to integer encoding.
<img src="https://github.com/ytia001/airbnb-ML/assets/136459037/3e98a3b3-3c55-463c-b542-a3f5dcfadd1e" alt="Image" width="400">
<img src="https://github.com/ytia001/airbnb-ML/assets/136459037/f1fb2a3a-31ec-448a-b1c4-84dd45653a50" alt="Image" width="400">

# Machine Learning Models 
1. Linear Regression
2. Random Forest Regression
3. CatBoost Regression
