**Project Title:**  

*Optimizing Real Estate Strategies in King County: A Data-Driven Approach for Haven-Kings Property Management*

**By:**  
                - [Julliet Iswana](https://github.com/Iswana-O)
                - [Wayne Kipngeno Korir](https://github.com/waynekipngeno)
                - [Eva Kiio](https://github.com/evamwende)
                - [Oscar Mulei](https://github.com/omulei)
                
---------------------
   **Supervisor:** 
   [Asha Deen](https://moringaschool.com/courses/data-science-course-part-time/)
   
---------------------
                
<img src="[Images/imagereader.jpg>
![](Images/image%20reader.jpg)
## Introduction

Haven-Kings Property Management, overseeing a vast portfolio of houses in the King County area, faces a dynamic and competitive real estate market. It's undeniable that Seattle and, by extension, King County stand as prime locations for acquiring and overseeing rental assets. Savvy investors understand that while a single property in this thriving market is beneficial, expanding one's real estate holdings is the key to amplifying profits and securing long-term financial stability.

However, improper strategy can lead to an accumulation of properties that fail to generate revenue. A fruitful investment in real estate is not just an assortment of various properties; it must be a well-thought-out portfolio that not only yields income but also capitalizes on tax benefits. Otherwise, these so-called "investments" can quickly become costly burdens. Property managers, real estate agents, and individual property owners need to set the right pricing to maximize their returns while staying competitive. The challenge is to find the optimal balance between high rental or sales prices and market demand. This is where data-driven insights can make a significant difference.

## Executive Summary

Haven-Kings Property Management is our client, overseeing a vast portfolio of houses in King County, and they aim to optimize their rental pricing strategy. Haven-Kings has previously relied on traditional methods of setting rent and pricing for their investors. They have been dependent on Comparative Market Analysis (CMA), where they conduct local comparisons by looking at similar properties in the same area to gauge reasonable pricing. Another method they have relied on is the "1% Rule": The monthly rent/pricing should be approximately 1% of the property's total value. Additionally, they increase prices each year based on the rate of inflation or a fixed percentage.

The aim of this project is to revolutionize Haven-Kings Property Management's approach to house pricing. This will be achieved by developing a predictive model using data analytics, specifically linear regression and machine learning techniques, to provide dynamic pricing recommendations based on various property features. This initiative is not just a step but a leap towards maximizing revenue and maintaining a competitive edge in Seattle's ever-evolving real estate market. The implementation of a predictive model for rental pricing is a forward-looking initiative that will position Haven-Kings Property Management as an industry leader in adopting data-driven strategies.

## Business Problem 

"Haven-Kings Property Management" manages a portfolio of houses in the King County area and seeks data-driven solutions to optimize property management and investment decisions. The business problem is to develop predictive models that leverage data from the King County House Sales dataset to assist in optimizing house pricing, making informed decisions about property renovations and investments, and providing dynamic pricing recommendations for their rental properties.

## Objective 

The primary objective is to create predictive models using multiple linear regression that "Haven-Kings Property Management" can use for the following purposes:

1. **Optimize House Pricing:** Provide "Haven-Kings Property Management" with a tool to determine optimal pricing for the houses in their portfolio in the King County area. This tool should consider house characteristics, location, and market conditions, enabling the company to maximize property value while remaining competitive in the local real estate market.

2. **Dynamic Pricing Recommendations:** Develop dynamic pricing recommendations for "Haven-Kings Property Management's" rental properties, leveraging data analytics and machine learning techniques, particularly linear regression, to adjust rental rates based on property features and market conditions. This will enhance revenue optimization.

## Research Questions 

To address the business problem and achieve the objectives, the following research questions can guide the analysis:

1. **House Pricing:**
   - What are the key factors that most strongly influence house prices in the King County area?
   - How do house characteristics (e.g., size, number of bedrooms, amenities) and location impact property values in this specific market?
   - Can a predictive model accurately estimate house prices for "Haven-Kings Property Management's" portfolio?

2. **Dynamic Pricing Recommendations:**
   - How can dynamic pricing recommendations be generated for "Haven-Kings Property Management's" rental properties using linear regression and machine learning?
   - What data-driven factors should be considered when adjusting rental rates based on property features and market conditions?
   - How will the implementation of dynamic pricing impact the company's revenue and competitiveness in the real estate market?

These refined business problem, objective, and research questions, with consistent naming, provide a comprehensive framework for addressing the challenges and opportunities faced by "Haven-Kings Property Management" in the competitive real estate market.

### **Data Overview: King County House Sales**

**Objective**: Predict the sales price of houses in King County, Seattle.

**Time Frame**: Homes sold between May 2014 and May 2015.

**Structure**:
- **Observations**: 21,613
- **Features**: 20 (excluding target variable)
- **Target Variable**: Price

**Key Features**:
- **Size & Structure**: `bedrooms`, `bathrooms`, `sqft_living`, `sqft_lot`, `floors`, `sqft_above`, `sqft_basement`
- **Location & View**: `waterfront`, `view`, `zipcode`, `lat`, `long`
- **Quality & Condition**: `condition`, `grade`
- **Age & Renovation**: `yr_built`, `yr_renovated`
- **Recent Renovations**: `sqft_living15`, `sqft_lot15`

**Insights**: 
- Price is heavily influenced by features like `bedrooms`, `sqft_living`, and the house's location.
- No missing values, aiding in model accuracy.

**Analysis Steps**:
1. Import necessary libraries.
2. Load the dataset.
3. Explore data structure, types, and basic statistics.
4. Visualize data for insights.
5. Perform regression analyses: simple, multiple, and polynomial.

#### Data Exploration:

Let's begin with data exploration to better understand the dataset's characteristics.

We'll start by:
1. Checking the distribution of the target variable, which is the house **price**.
2. Exploring relationships between the **price** and other potential predictor variables.
3. Analyzing the distribution of key features such as **bedrooms**, **bathrooms**, **sqft_living**, and **grade**.

The distribution of house prices is right-skewed, meaning that there are a few houses with extremely high prices compared to the majority. Most of the houses are priced in the lower to mid-range, with a peak around 300,000  to  500,000 dollars($).

Next, let's explore the relationship between the house price and some potential predictor variables. We'll start by examining how the price varies with:

1. Number of bedrooms
2. Number of bathrooms
3. Living space (sqft_living)
4. House grade

We'll use boxplots to visualize these relationships.

Here's a summary of the visualizations:

1. **Price vs. Bedrooms**:
   - Generally, houses with more bedrooms tend to have higher prices. However, there's an outlier with a house that has 33 bedrooms, which seems unusual given its price range.
   
2. **Price vs. Bathrooms**:
   - Houses with more bathrooms generally have higher prices. The trend is evident until around 6-7 bathrooms, after which the price variation becomes more dispersed.
   
3. **Price vs. Living Space (sqft)**:
   - There's a positive correlation between living space (in sqft) and house price. As the living space increases, the house price also tends to increase.
   
4. **Price vs. Grade**:
   - House grade also has a clear impact on price. Higher grade houses generally fetch higher prices. The variation in prices also seems to increase with higher grades.

From the visualizations, it's evident that features like the number of bedrooms, bathrooms, living space, and grade have an influence on house prices.

As expected there are some multicollinearity issues which we need to address.

We note that `sqft_above` and `sqft_living` are highly positively correlated, which is expected as `sqft_above` is the square footage of the house apart from basement (and we saw earlier that most houses did not have a basement). We will choose to keep `sqft_living` as it encompasses more information and drop the `sqt_above` feature. We also see that `sqft_living15` is moderately highly correlated with `sqft_living` and so we will drop this feature too.

We also note that `sqft_lot` and `sqft_lot15` are highly positively correlated and we will choose to keep `sqft_lot` as it relates directly to the house as opposed to its neighbours (and so potentially easier to obtain data for and generalise.)

```
