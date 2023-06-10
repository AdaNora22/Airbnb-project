# Airbnb-project

## Problem Statement:

The objective of this project is to explore and analyze the demand patterns of Airbnb listings by investigating the relationship between availability (availability_365) and booking-related metrics such as the number of reviews (number_of_reviews) and booking frequency (reviews_per_month). Additionally, we aim to develop a recommendation system that assists future landlords in determining the desired rental payout by suggesting properties based on their size, location, and other relevant features.


## Data Disctionary:

#### Sources:
- [`airbnb_listings.csv`](./data/seattle_airbnb_listings.csv): Seattle AirBnb data used during this project


#### Size of datasets:
- seattle_airbnb_listings.csv has 6376 rows and 18 columns so its' total memory weigth is 1122KB


#### Data dictionary for all_test_dateset_merged_together cloumns that I ended up useing:
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


## Methodology:

By analyzing the relationship between availability, number of reviews, and booking frequency, we seek to understand the factors that influence the popularity and demand for different Airbnb listings. This analysis will provide valuable insights to future landlords, enabling them to make informed decisions when setting rental prices and understanding the anticipated demand for their properties. By identifying the key factors that contribute to high demand, such as availability and positive reviews, landlords can adjust their pricing strategies to maximize occupancy rates and rental income.

Furthermore, the recommendation system will utilize various features, including property size, location, room type, price, and other relevant attributes, to suggest similar listings to future landlords based on their preferences. By considering these factors, the recommendation system will help landlords identify properties that are most likely to attract high demand, providing guidance on desirable property characteristics and optimal locations.

Through this project, we aim to assist future landlords in understanding the demand patterns of Airbnb listings and provide personalized recommendations that facilitate informed decision-making regarding rental payouts, property size, and location. Ultimately, this will enable landlords to optimize their rental income and increase the desirability and profitability of their properties on the Airbnb platform.


## Background research:
**For this project i had to learn more about rules for renting in Seattle, WA as well as about different features that influence renting demand and prices"

There was few rows in the 'license' column have had NaN values. Hence, I needed to research does renting out on Airbnb in Seattle requere license. Me research showed that since September 2021, in Seattle, Washington, hosts are required to have a license to legally rent their properties on platforms like Airbnb. The City of Seattle has specific regulations in place for short-term rentals, including Airbnb rentals.

Hosts in Seattle are required to obtain a Short-Term Rental Operator's License from the City of Seattle's Department of Finance and Administrative Services. This license ensures that hosts comply with regulations related to safety, taxation, and land use. Hosts must also meet certain requirements, such as maintaining liability insurance and providing emergency contact information to guests.

Hence, I decieded to drop all properties that have NaN for 'license' column.

Furthermore, different hosts seem to have the same 'license' numbers. After conducting some research, I have found that license values can vary and may have different formats or naming conventions depending on local regulations or the host's specific situation. Additionally, since we have 3423 unique license values in the dataframe, it would be impractical to investigate each individual license value. Therefore, I have made the decision to drop the 'license' column in the next step, as all the remaining properties have a 'license' and, for the sake of time, we will assume that the 'license' value is valid and that the hosts can legally rent the properties.



