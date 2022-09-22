# Amazon_Vine_Analysis
Analysis on Amaozon's vine review with PySpark, Google Colab, PostgreSQL, and Amazon Web Services (AWS)

## Overview of the Analysis
In this project, I used the Amazon video games reviews dataset to analyze if there is any bias toward favorable reviews from Vine members. The Vine Program is an incentive program that gifts customers free products to exchange for a review for the product. Companies pay a small fee to Amazon and provide products to Amazon Vine members to receive reviews for their products. 
I used PySpark to extract, transform, and load the dataset to an AWS RDS and connected it to my PostgreSQL server. Then, I created table schemas in PdAdmin and transferred data into these tables with PySpark. 
Next, I used PySpark to perform a statistical analysis to determine if there is a bias between the paid reviews and unpaid reviews. 

## Data 
Video Games Review Datatset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz

## Results
### How many Vine reviews and non-Vine reviews were there?
Only reviews with 20 or more votes and the ratio between helpful votes and total votes greater or equal to 50% were considered for the analysis. With these filters applied, it leaves 40565 records. 

![paid_reviews_df](https://github.com/Wuyang080510/Amazon_Vine_Analysis/blob/main/image/paid%20vine%20df.png)

![unpaid_reviews_df](https://github.com/Wuyang080510/Amazon_Vine_Analysis/blob/main/image/unpaid%20vine%20df.png)

- Paid Vine Reviews
    - total reviews: 94
    - 5-star reviews: 48
    - % of 5-star reviews: 51.1%

- Unpaid Vine Reviews
    - total reivews: 40471
    - 5-star reviews: 15663
    - % of 5-star reviews: 38.7%

## Summary

There is a bias toward favorable reviews from vine members. As the above results show,  there is a significant difference in the percentage of 5-star rating reviews between vine members (51.1%) and non-vine members (38.7%). The result describes a positivity bias for reviews made by vine members.
If we pull the number of reviews written by vine members in the original dataset, there are 4291 paid vine reviews. If we apply the more than 20 votes filter, the number of paid reviews dropped to 104 reviews. This is a sign that most of the reviews made by vine members did not get at least 20 votes. The reason for this result may vary. Vine members with gifted products tend to give favorable reviews of products. This leads to the reviews being biased rather than neutral. Also, users might be biased on the reviews left by vine members and non-vine customers. They may suspect the validity of the reviews made by vine members.

![no_filter_review_count](https://github.com/Wuyang080510/Amazon_Vine_Analysis/blob/main/image/vine%20count%20without%20filter.png)

![with_vote_filter_applied](https://github.com/Wuyang080510/Amazon_Vine_Analysis/blob/main/image/vine%20reviews%20count%20with%20atLeast%2020%20votes.png)

Additionally, we can use a larger dataset to perform the analysis, as the paid vine reviews dataset only has 94 records with the two filters applied. Furthermore, we can conduct a central tendency analysis of the dataset to check the average, median, and mode of the reviews' ratings.
