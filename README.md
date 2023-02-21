# Amazon_Vine_Analysis

## Overview

### Purpose
The purpose of this analysis was to analyze Amazon reviews written by members of the paid Amazon Vine project and determine if there is any bias toward favorable reviews from Vine members in the Sports dataset. 

### Dataset
The dataset was pulled from https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt and I selected the following dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz

### Technology used
I used Google Colab, pgAdmin, PySpark, and PostgreSQL in order to complete the analysis

## Results:
I was then instructed to answer a few questions:
1. How many Vine reviews and non-Vine Reviews were there?
2. How many Vine reviews were 5 stars? How many non-Vine Reviews were 5 stars?
3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

![image](https://user-images.githubusercontent.com/114685724/220220941-1e6dda2d-3838-4062-baad-c1379f186ea7.png)

I was able to answer these questions by importing the dataset (linked in the Dataset seection above) into Google Colab using PySpark and SparkFiles. 

![image](https://user-images.githubusercontent.com/114685724/220220968-180c9c48-8ff1-47d2-bc28-2d20124d2fb8.png)

From there, I filtered the dataset down to the necessary fields in order to complete the rest of the analysis. 

![image](https://user-images.githubusercontent.com/114685724/220221088-48cc3c67-51b3-4357-be62-576e33f2b8ab.png)

I also cleaned this dataset up a little bit to avoid any potential DIV0 errors and so I filtered the dataset to only reviews that received greater than or equal to 20 votes.

![image](https://user-images.githubusercontent.com/114685724/220221200-b70602dd-8880-49ae-bf55-b5ad2e822e3b.png)


From there, I filtered the dataset even further to avoid "unhelpful" reviews and I only left reviews that at least 50% of people voting it as "useful"

At that point, I was ready to dive in and answer the questions posed.

### Number of Reviews

![image](https://user-images.githubusercontent.com/114685724/220221370-3d837ec1-8810-4317-892c-3d891988a30e.png)

I first filtered the helpful_votes dataframe into two separate dataframes (paid_df and unpaid_df). 

![image](https://user-images.githubusercontent.com/114685724/220221450-60efe503-60c9-4237-b11a-7b11df5f2576.png) ![image](https://user-images.githubusercontent.com/114685724/220221456-55aed258-7ccc-4b37-8b36-e6ae60d5cb8c.png)


*Once completed, I was able to import the count function and I found there were 334 Vine reviews and 61614 non-Vine reviews.*

### 5 Star Reviews

![image](https://user-images.githubusercontent.com/114685724/220221519-759115b8-a761-446d-9258-edb9247f9a3c.png) ![image](https://user-images.githubusercontent.com/114685724/220221534-55093bd3-4ad9-4b72-b2ef-acba4639bcb6.png)

*Next, I filtered the paid_df and unpaid_dfs into their own subsequent "five_star" dataframes and counted those to determine that there were 139 five-star reviews given by Vine members and 32665 five-star reviews written by non-Vine members*

### Percentage of 5 star reviews

![image](https://user-images.githubusercontent.com/114685724/220221727-072b994e-8658-46f2-9d9e-f55254f7772b.png) ![image](https://user-images.githubusercontent.com/114685724/220221733-f5901de7-78f4-4332-9e8b-b3804debf303.png)

*Lastly, I just had to do the math. Divide 5 star reviews by total reviews and multiply by 100 to get the percentages: 41.62% five-star reviews for Vine members and 53.02% five-star reviews for non-Vine members*


## Summary:

The results are a little shocking: paid reviews resulted in a much lower percentage of 5 star reviews. It almost appears that there is a bias AWAY from favorable reviews when they are paid for it. 

I think some additional analysis is required. I think we need to see if there are any differences across other datasets, not just Sports. I also think we could use a larger dataset of Vine reviews. This analysis only had 334 paid reviews and 61614 non-paid reviews. That means that less than half of one percent of all reviews were paid, which is an extremely small amount. I also think we need to look at the sentiment of the members. Do Vine members feel more entitled to a great product and therefore are harsher with their grades? Overall, I think the data shows some interesting results but more research is required prior to making any rash decisions on the Vine program. 
