# Are Amazon Vine Reviews Biased? An Analysis of Kitchen Products Reviews

*Note: This repository was created to fulfill an assignment (Module 16  Challenge) for the UC Berkeley Data Analytics and Visualization Bootcamp. The analysis, content, and format of this report were based on module instructions and the grading rubric.*

*Module exercises included:*
- *Introduction to MapReduce*
- *Introduction to Spark*
- *Installation and use of PySpark on Google servers using Google Collab*
- *Basic dataframe functions and manipulations using PySpark*
- *Introduction to natural language processing*
  - *Creating an NLP pipeline*
- *Introduction do Amazon Web Services*
  - *S3 Buckets*
  - *Amazon RDS*
- *Using AWS with PySpark*

*The report below is based on analysis from notebooks Amazon_Reviews_ETL.ipynb and Vine_Review_Analysis.ipynb*


## Overview

This report presents a very basic analysis of a subset of Amazon Vine reviews to demonstrate use of the AWS RDS service and PySpark. Kitchen product reviews were analyzed for bias for 5 star ratings between Vine program reviewers and regular reviewers. Although Vine reviewers are not paid, they do recieve free products for review, which may subconsciously influence their opinions.

**Data Source:** 

Amazon Vine kitchen products reviews (automatic download)

(https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Kitchen_v1_00.tsv.gz)

---

## Results

ETL was performed on the above dataset using PySpark, then loaded to an AWS RDS database and accessed remotely via PostgreSQL. As part of module exercises, the data was cleaned and split into four separate tables. The analysis of Vine product reviews presented below is based on the vine_table as described.


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

Based on our basic analysis above, there does not appear to be an overt positivity bias by Vine reviewers. The percentage of 5-star reviews was actually slightly less than non-vine reviews. However, further analysis could be performed across all the star ratings to see if there is a skew. Figures 3 and 4 below show the total number of reviews for all stars. Based on the raw data, there may be a negativity bias from regular reviewers. An ANOVA analysis could be performed with Vine and non-Vine reviews as categories for each star rating to determine statistically significant differences. 


**Figure 3: Total Vine Reviews by Star Rating for Kitchen Products**
 
![VineStar.png](/Images/VineStar.png)


**Figure 4: Total Non-Vine Reviews by Star Rating for Kitchen Products**

![NoVineStar.png](/Images/NoVineStar.png)

