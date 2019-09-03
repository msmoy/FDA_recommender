# FDA Reported Reactions to Food, Cosmetics, and Dietary Supplements
--------

## Table of Contents:

* [Introduction](#introduction)
* [Technologies](#technologies)
* [Data Description](#data-description)
* [Process Overview](#process-overview)
* [Project Status](#project-status)
* [Contributing](#contributing)
* [Source](#source)

---
### Introduction:

With the nation moving towards being more health conscious, consumers are educating themselves on what products would be deemed safe for themselves and their families. Unfortunately, should a product pose a health risk, it's common for the public to be unaware until an announcement (i.e. recall) is sent out by the FDA (U.S Food and Drug Administration) or the company of the product. As a result, this recommender system takes adverse events that were reported to the FDA for cosmetics, food, and dietary supplments, and empowers consumers to continue to be more proactive towards their health. The system will search for a product under one of the 3 categories (each a separate dataset), and return a list of 10 products that include similar symptoms. The results will act as a forewarning for consumers should they be concerned about experiencing the same negative reaction(s).

---
### Technologies:

- **Programming Language**
    - Python 3.7
    
- **Imported Libraries**
    - Pandas
    - Numpy
    - Seaborn
    - Matplotlib.pyplot
    - String
    - sklearn.feature_extraction.text
        - CountVectorizer
    - sklearn.feature_extraction
        - stop_words
    - sklearn.metrics.pairwise
        - cosine_similarity
        
--- 
### Data Description:

- **datasets**
    - adverse_events.csv
        - combination of datasets downloaded from FDA website
    - adverse_events_2.csv
        - clean dataframe that doesn't include null values or any products that are labeled "EXEMPTION 4"
    - adverse_events_cosmetics.csv
        - clean dataframe for cosmetic products
    - adverse_events_food.csv
        - clean dataframe for food products
    - adverse_events_supplements.csv
        - clean dataframe for dietary supplements products
    - CAERSASCII 2014-20190331.csv
        - dataset downloaded from FDA website for years 2014 to March 31, 2019
    - CAERSASCII-2004-2013.csv
        - dataset downloaded from FDA website for years 2004 to 2013
        
- **Demonstration.ipynb**
    - Clean notebook used for demonstrating recommender system
    - Provides access to original dataframe that contains details of the reported events for further research

- **EDA & Technical Analysis.ipynb**
    - Executive Summary
    - Code for EDA
    - Research & Analysis
    
- **Progress Report.ipynb**
    - Initial plan
    - Discoveries
    - Offers thought process that can be useful when considering future improvements, as well as reasons of why certain steps were taken during EDA
    
- **FDA presentation.pdf**
    - Project presentation
    
- **README.md**
    
---
### Process Overview:

- **Data cleaning**
    - Removed null values for Product
    - Removed observations for Exemption 4 products
    - Removed null values for MedDRA Preferred Terms

- **Recommender System**
    - Created dataframe for each category
        - Cosmetics
        - Supplements (this is for dietary supplements)
        - Food
    - Applied countvectorizer to "MedDRA Preferred Terms" (symptoms) column for each dataframe
    - Created a recommender system that takes in 3 arguments
        - Name of dataframe
        - Name of product
        - Cosine similarity metric
        
---
### Project Status:


This recommender system currently uses data for adverse events that were reported by healthcare practitioners and consumers between 2004 and March 2019. However, the data does not include information as to whether the consumer had an underlying health issue. As a result, there is no guarantee the product(s) were the cause of the adverse event. With that said, the reports are monitored by the FDA (more specifically Center for Food Safety and Applied Nutrition), who will conduct further research if they see a potential risk for the public.

Based on the data, the majority are related to dietary supplements (24,035 products), with food not too far behind (20,842 products). In fact, the top 5 reported products were all a type of dietary supplement that are commonly recommended for their health benefits. To minimize the risk of having a negative reaction, consumers should consult their doctors prior to starting a vitamin regimen, as it can take some time before symptoms appear and certain vitamins may not mix well with others (same goes for medicine). As for cosmetics, despite only having 5,259 products, the results appear to be the most similar when using the recommender system to search for the exact product name versus a keyword. 

In order to confirm the reported adverse events can make an impact, recall announcements have been found for a specific product under each category (cosmetics, food, and supplements), and they reference symptoms ("MedDRA Preferred Terms" column) that were included in the reports to the FDA.

> ***Below are ways this recommender system can be improved:***
> - Automatic updates as soon as new adverse events are reported
> - Provide option for users to search by symptoms (i.e. asthma) rather than just products
> - Adjust system to output more details for each product (i.e. dates of when the events occurred, or most recent date)
    - Consumers can use this to determine if it's currently a potential risk
> - Obtain product ingredients to include in the output
    - Details of what each ingredient is and its purpose
    - Information regarding any risk factors for specific ingredients
        - Allows consumers to be cautious of other products that contain the same ingredient(s)
> - After the system has been improved, it can be made into a user-friendly web/mobile application

---
### Contributing:


If you would like to contribute, please feel free to reach out to discuss any changes or suggestions you may have. 

---
### Source:

- Two datasets downloaded
    - [2004 to March 2019 data](https://www.fda.gov/food/compliance-enforcement-food/cfsan-adverse-event-reporting-system-caers)

- [Data dictionary](https://www.fda.gov/media/97035/download)
    
- Background regarding use of these reported adverse events:
    - [Center for Food Safety and Applied Nutrition ](https://www.fda.gov/about-fda/office-foods-and-veterinary-medicine/center-food-safety-and-applied-nutrition-cfsan)
    - [CFSAN Adverse Event Reporting System - FAQ](https://www.fda.gov/food/compliance-enforcement-food/cfsan-adverse-event-reporting-system-caers)

