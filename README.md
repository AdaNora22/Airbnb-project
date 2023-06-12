# Airbnb Feature Importance Analysis & Recommendation System Project

## Problem Statement:

This project focuses on exploring and analyzing the demand patterns of Airbnb listings in Seattle, WA. The main objective is to identify the most important features and investigate the relationship between availability (availability_365) and booking-related metrics, such as the number of reviews (number_of_reviews) and booking frequency (reviews_per_month). The analysis of these variables aims to provide insights into the process of identifying features of importance for Airbnb properties in this area.

In addition to analyzing demand patterns, another goal of this project is to develop a recommendation system. This system will assist prospective renters in finding their ideal rental place by suggesting properties based on neighborhood, room type, or minimum nights, and further refining the selection based on price or availability_365 value. By leveraging these recommendations, renters can make informed decisions about rental prices and gain an understanding of the expected demand for properties in Seattle, WA.

The dataset used for this analysis consists of Airbnb listings in Seattle, WA. Through correlation analysis and other statistical techniques, we will determine the strength and direction of the relationships between the variables of interest. By uncovering the most influential factors and understanding demand patterns, this project aims to provide valuable insights for rentors and contribute to optimizing rental experince on the Airbnb platform.


## Data Disctionary:

#### Original Sources:
- [`airbnb_listings.csv`](./data/seattle_airbnb_listings.csv): Seattle AirBnb data used during this project

#### Three Created Datasets:
- [`cleaned_data.csv`](./data/cleaned_data.csv): Clean data after Data Cleaning process
- [`encoded_data.csv`](./data/data_ohe_outliers_drop_cols.csv): Data scaved during Feature Engenering process with encoded categorical variables and no outliers
- [`scaled_data.csv`](./data/scaled_data.csv): Data saved in the end of Feature Engenering with scaling and new columns such as 'location_proximity' and 'price_log'

#### Size of datasets:
- seattle_airbnb_listings.csv has 6376 rows and 18 columns so its' total memory weigth is 1122KB


#### Data dictionary for All Used Cloumns:
| Variable Name | Description | Units | Type | Notes |
| --- | --- | --- | --- | --- |
| `id` | ID on the listing | ID | numeric |  |
| `name` | Title or name of the listing | Text | String |  |
| `host_id` | ID of the host | ID | numeric |  |
| `host_name` | Name of the host | Text | String |  |
| `neighbourhood_group` | Group of neighborhoods the listing belongs to | Text | String |  |
| `neighbourhood` | Specific neighborhood the listing is located in | Text | String |  |
| `latitude` | Latitude coordinate of the listing | Degrees | numeric |  |
| `longitude` | Longitude coordinate of the listing | Degrees | numeric |  |
| `room_type` | Type of room available for rental | Text | String |  |
| `price` | Rental price per night | Currency | numeric |  |
| `minimum_nights` | Minimum number of nights required for booking | Nights | numeric |  |
| `number_of_reviews` | Total number of reviews for the listing | Count | numeric |  |
| `last_review` | Date of the last review | Date | Date |  |
| `reviews_per_month` | Average number of reviews per month | Count | numeric |  |
| `calculated_host_listings_count` | Number of listings by the host | Count | numeric |  |
| `availability_365` | Number of days the listing is available in a year | Days | numeric |  |
| `number_of_reviews_ltm` | Number of reviews in the last 12 months | Count | numeric |  |
| `license` | License code or identifier | Text | String |  |
| `name_processed` | Title or name of the listing post text processing | Text | String | new column in [`cleaned_data.csv`](./data/cleaned_data.csv) |
| `assumed_gender` | Femal or Male gender | Text | String | new column in [`cleaned_data.csv`](./data/cleaned_data.csv) |
| `location_proximity` | 'latitude' * 'longitude' | Score | numeric | new column in [`scaled_data.csv`](./data/scaled_data.csv)|
| `price_log` | Price column after Log Transformation | Score | numeric | new column in [`scaled_data.csv`](./data/scaled_data.csv) |
| `income` | (365 - 'availability_365') * 'price' | Currency | numeric | new column considered in RS notebook |



## Background research:
For this project, I conducted extensive research on the rules and regulations for renting in Seattle, WA, as well as the various factors that influence rental demand and prices.

During the data cleaning process, it was observed that several rows in the 'license' column contained NaN values. To ensure compliance with local regulations, I researched the requirements for renting out properties on platforms like Airbnb in Seattle. It was discovered that since September 2021, hosts are required to obtain a Short-Term Rental Operator's License from the City of Seattle's Department of Finance and Administrative Services. This license ensures that hosts meet safety, taxation, and land use regulations. Hosts must fulfill certain criteria, including maintaining liability insurance and providing emergency contact information to guests.

Based on this information, I made the decision to drop all properties that had NaN values in the 'license' column, as they did not comply with the licensing requirement. Additionally, it was observed that different hosts had the same 'license' numbers. Further research revealed that license values can vary in format or naming conventions depending on local regulations or the host's situation. Considering the large number of unique license values in the dataset (3423), it was impractical to investigate each individual value. Therefore, for efficiency, I decided to drop the 'license' column, assuming that the remaining properties with a 'license' value were valid and legally rentable.

Moving forward, the recommendation system implemented in the provided code prompts the user to input parameters such as the category of interest, specific attribute, and desired values. Utilizing a dataset of listings, the system calculates the cosine similarity between items based on the selected parameters. Recommendations are generated by identifying the most similar listings and sorting them based on the user's specified attribute value. The top three recommendations are then displayed, offering personalized suggestions for listings that closely align with the user's preferences.


## Methodology/Steps:

- Data cleaning step: Implement various measures to ensure the integrity of the dataset. This involves identifying and addressing duplicates, handling missing values, and resolving inconsistent or invalid entries. Unnecessary columns are removed to focus the analysis on key variables. Additionally, a column is added to incorporate assumed gender information, acknowledging its potential influence on rental decisions. The processing of textual data for host and listing names is carefully executed. Finally, the refined dataset is securely saved, providing a robust foundation for subsequent analysis. These meticulous data cleaning efforts significantly contribute to the overall reliability and quality of the findings, enabling a comprehensive exploration of demand patterns in Airbnb listings.

- During the Exploratory Data Analysis (EDA) process, the provided dataset is thoroughly examined, encompassing attributes such as id, host_id, neighbourhood_group, neighbourhood, latitude, longitude, room_type, price, minimum_nights, number_of_reviews, reviews_per_month, availability_365, number_of_reviews_ltm, name_processed, assumed_gender, and total_of_host_listings_count. The EDA involves analyzing the distribution and summary statistics of numerical variables, investigating categorical variables, and performing geospatial analysis. Visualizations are employed to gain insightful understanding of relationships and patterns, establishing a strong basis for further analysis and modeling to explore and analyze demand patterns of Airbnb listings in Seattle, WA.

- Correlation Analysis: Initiate a correlation analysis to comprehend the relationships between the variables of interest, such as availability (availability_365), number of reviews (number_of_reviews), and booking frequency (reviews_per_month). Calculate correlation coefficients, such as Pearson correlation, to ascertain the strength and direction of these relationships.

- Regression Analysis: Conduct regression analysis to model the relationship between availability and booking-related metrics. Techniques such as multiple linear regression or Poisson regression (if reviews_per_month is a count variable) can be employed to determine how availability influences the number of reviews and booking frequency. In this context, availability serves as the predictor variable, while the number of reviews or booking frequency represents the dependent variable.

- Feature Importance Analysis: Utilize techniques such as feature importance or feature selection algorithms to determine the most influential features shaping demand patterns. Random Forests or Gradient Boosting algorithms can be applied to examine the importance scores of these features. This analysis aids in identifying the key factors that contribute to demand.

- The implemented recommendation system prompts users to input parameters including the category of interest, specific attribute, and desired values. It leverages a dataset of listings to calculate cosine similarity between items based on the selected parameters. Subsequently, the system generates recommendations by identifying the most similar listings and sorting them based on the user's specified attribute value. The top three recommendations are displayed, offering personalized suggestions for listings that closely align with the user's preferences.


## Conclusoion:

Through our analysis, we have uncovered several key findings related to the demand patterns of Airbnb listings in Seattle. Firstly, we identified the most important features that influence demand. In the non-scaled data analysis, features such as total_of_host_listings_count, reviews_per_month, price, latitude, and longitude emerged as the top contributors. Additionally, factors like number_of_reviews, number_of_reviews_ltm, minimum_nights, assumed_gender, and specific neighborhoods such as University District played significant roles in predicting availability patterns.

In the scaled data analysis, room_type_Private room, number_of_reviews, total_of_host_listings_count, and reviews_per_month stood out as the most influential features. Other important factors included assumed_gender, price, number_of_reviews_ltm, minimum_nights, and specific neighborhoods like University District, View Ridge, and Adams.

It is important to note that the order of importance between non-scaled and scaled data analyses may differ due to data scaling affecting feature importance scores.

Additionally, our exploratory data analysis (EDA) revealed interesting insights. In terms of gender analysis, the dataset showed a higher number of assumed males than females. Neighborhood analysis highlighted variations in listing distributions, with some neighborhood groups having a higher concentration of listings than others. Certain neighborhoods also displayed higher average prices, while availability did not significantly differ based on assumed gender.

Lastly, based on Kendall's Rank correlation test, there was evidence of a weak negative correlation between availability and review-related variables such as number_of_reviews, reviews_per_month, and number_of_reviews_ltm. This suggests that as availability decreases, there is a tendency for review activity to increase, albeit with a weak effect size.

Overall, these findings provide valuable insights into the demand patterns of Airbnb listings in Seattle, allowing property owners to make informed decisions regarding rental prices, understand the factors influencing demand, and optimize their rental income on the platform.

## Recommendations for Future Analysis

1. **Incorporate Text Data:** Utilize textual data from reviews and listing names to extract meaningful insights. Perform text preprocessing techniques such as tokenization, removal of stop words, and stemming/lemmatization to enhance the analysis of these text-based features.

2. **Incorporate Datetime Data:** Explore the potential seasonality patterns in the dataset by analyzing datetime variables such as availability, price, and income. Consider extracting additional temporal features, such as month, day of the week, or time of the year, to capture any temporal trends that may influence demand and pricing.

3. **Further Feature Engineering:** Expand the feature set by deriving new variables or combining existing ones to capture additional aspects of rental demand. For example, consider creating variables related to amenities, proximity to popular attractions, or distance to transportation hubs. These engineered features can provide more insights into the factors driving demand.

4. **Beyond Seattle, WA:** Extend the analysis to include Airbnb markets beyond Seattle, WA. Explore datasets from other cities or regions to identify common trends or unique characteristics in different rental markets. This broader perspective can offer valuable insights into the general dynamics of Airbnb rentals and help uncover region-specific patterns.

5. **Beyond Airbnb:** Consider incorporating data from other platforms or sources to gain a comprehensive understanding of the rental market. Explore data from alternative accommodation platforms, hotels, or local tourism statistics. By comparing Airbnb data with other sources, you can assess Airbnb's market share and identify potential opportunities or challenges in the broader accommodation industry.

6. **Improve Recommendation System:** Enhance the existing recommendation system by incorporating advanced algorithms or techniques. Consider implementing collaborative filtering methods, content-based filtering, or hybrid approaches to improve the accuracy and personalization of recommendations. Experiment with different similarity measures and ranking algorithms to optimize the system's performance and provide more relevant and diverse recommendations to users.