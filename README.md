# Amazon_Vine_Analysis

*Note: This repository was created to fulfill an assignment (Module 16  Challenge) for the UC Berkeley Data Analytics and Visualization Bootcamp. Submitted on 2-11-22 for grading.*


## Overview

This report presents a very basic analysis of a subset of Amazon Vine reviews to demonstrate use of the AWS RDS service and PySpark. Kitchen product reviews were analyzed for bias for 5 star ratings between Vine program (paid) reviewers and non Vine program reviewers.

---

## Results

Dataset: Amazon Vine kitchen products reviews
https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Kitchen_v1_00.tsv.gz

ETL was performed on the above dataset using PySpark, then loaded to an AWS RDS database. 

To analyze Vine versus non-Vine reviews, the dataset was filtered for reviews with more than 20 votes and at least 50% helpful votes. These blunt conditions should eliminate products with too few reviews, irrelevant reviews, and bot reviews while focusing on reviews from users who gave thoughtful evaluations.


**Figure 1: Best Vine Reviews for Kitchen Products**

![Vine.png](/Images/Vine.png)


**Figure 2: Best Non-Vine Reviews for Kitchen Products**

![NoVine.png](/Images/NoVine.png)


From the filterd data set, the following observations were made about favorable reviews:
- There were 1160 Vine reviews and 92,308 non-vine reviews (Figures 1 and 2 above)
- There were 489 5-star Vine reviews and 43,247 5-star non-vine reviews
- 42% of Vine (paid) reviews were 5-stars while about 47% of non-vine (unpaid) reviews were given 5-stars 


---

## Summary

Based on our basic analysis above, there does not appear to be an overt positivity bias by Vine reviewers. The percentage of 5-star reviews was actually slightly less than non-vine reviews. However, further analysis could be performed across all the star ratings to see if there is a skew. Figures 3 and 4 below show the total number of reviews for all stars. Based on the raw data, there may be a negativity bias from non-vine reviews. An ANOVA analysis could be performed with Vine and non-Vine reviews as categories for each star rating. 


**Figure 3: Total Vine Reviews by Star Rating for Kitchen Products**
 
![VineStar.png](/Images/VineStar.png)


**Figure 4: Total Non-Vine Reviews by Star Rating for Kitchen Products**

![NoVineStar.png](/Images/NoVineStar.png)

