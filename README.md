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
                
![](/Images/imagereader.jpg)

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

![](/Images/Distribution%20of%20House%20Prices.png)

Next, let's explore the relationship between the house price and some potential predictor variables. We'll start by examining how the price varies with:

1. Number of bedrooms
2. Number of bathrooms
3. Living space (sqft_living)
4. House grade

We'll use boxplots to visualize these relationships.

![](/Images/Relationship%20between%20House%20Price%20and%20Key%20Features.png)

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

![](/Images/Correlation%20Heatmap.png)
We note that `sqft_above` and `sqft_living` are highly positively correlated, which is expected as `sqft_above` is the square footage of the house apart from basement (and we saw earlier that most houses did not have a basement). We will choose to keep `sqft_living` as it encompasses more information and drop the `sqt_above` feature. We also see that `sqft_living15` is moderately highly correlated with `sqft_living` and so we will drop this feature too.

We also note that `sqft_lot` and `sqft_lot15` are highly positively correlated and we will choose to keep `sqft_lot` as it relates directly to the house as opposed to its neighbours (and so potentially easier to obtain data for and generalise.)

### Modeling

#### Perform regression analyses: simple, multiple, and polynomial.
## Simple Regression

### Price vs. sqft_living

`sqft_living` is selected as the baseline predictor because it had the highest correlation with the target variable (price) with a pearson correlation of 0.71. To build the base model we shall start by visualizing the relationship between `sqft_living` and `price` . 

## Building the base model (OLS) 

### Applying Box-Cox Transformation to address heteroscadasticity

### MULTIPLE LINEAR REGRESSION


From our exploration some of the key predictors identified are bedrooms, bathrooms, sqft_living, and grade .
We decided to use sqft_living for our modelling while excluding bedrooms and bathrooms

**Rationale for Exclusion:**

bedrooms and bathrooms were found to be highly correlated with sqft_living. Including predictors that are highly correlated can lead to multicollinearity, which can destabilize regression estimates Therefore, to avoid this issue, we have  decided to exclude bedrooms and bathrooms since sqft_living  captures the information they provide. We were able to verify these assumptions and decisions with data visualization and correlation matrices during the data exploration stage. 
correlation between sqft_living and bedrooms is 0.57 and sqft_living and bathrooms is 0.75


**Selected Predictors:**
1. **View:**
Rationale: The view from a property can significantly influence its perceived value. A good view can add aesthetic value to the property, making it more desirable to potential buyers.
2. **Grade:**
Rationale: The grade of a house represents its quality and can be a strong indicator of its overall value. A higher grade often means better construction quality, use of superior materials, and adherence to modern design principles. 
3. **Condition:**
Rationale: The overall condition of a house directly affects its marketability. Houses in better condition are likely to sell faster and at higher prices. 
4. **Age of House:**
Rationale: The age of a house can influence its value in various ways. Older houses might have architectural significance or charm, but they might also have outdated systems or require more maintenance. Conversely, newer houses might have modern amenities but lack the character of older homes. The age can give potential buyers an idea of the house's history and the potential costs associated with its upkeep.

## Model 2

We have expanded the base model to include more predictors, specifically property grade, condition, and the square footage of living space.

# Model 3: Includes age of house

we've converted the date column into date time format and extracted the year the house was sold. we've also calculated the years since renovation. This is valuable as properties that were recently renovated might have a different price dynamics compared to those that haven't been updated in a long time.

 ## Model 4: Includes years between renovation and sale (assumption is that houses with zero in the yr_renovation column had not be renovated at the time of sale)
 
 the Model introduces the feature Years_Between_Renovation_and_Sale, which captures the time since a house's last renovation (or since it was built if it hasn't been renovated).
 
 The newly added columns, year_sold and Years_Between_Renovation_and_Sale, can offer additional insights. The time since the last renovation can be a significant factor in house pricing. Homes that were recently renovated might fetch higher prices due to updated features, modern design, or improved functionality.
 
### Years_Between_Renovation_and_Sale is calculated by taking the year in the date column (year of sale) - renovation year

## Model 5: Includes view(encoded)

Model 5 incorporates both the floors and view variables


### Recommendations for Haven-Kings Property Management:

**Prioritize Living Space:** Given the high correlation between sqft_living and the house price, prioritize properties with larger living spaces when considering acquisitions or pricing.

**Consider Property Quality and Condition:**  Model 2 emphasizes property grade and condition as crucial determinants of price. Ensure that properties under management are well-maintained to command higher rental or sale prices.

**Factor in Age:** The age of a house can significantly impact its value. Older houses might carry historical or architectural significance, while newer ones might boast modern amenities. Understand the pros and cons associated with a property's age when setting prices.

**Renovation Impact:** Model 4 focuses on the years since renovation. Properties that have been recently renovated might fetch higher prices. Consider investing in renovations for older properties to increase their market value.

**Views Matter:** The view from a property can significantly influence its perceived value. Properties with better views can command higher prices. Ensure this factor is appropriately considered in pricing strategies.

**Dynamic Pricing Strategy:** Consider developing a dynamic pricing strategy that takes into account various property features and market conditions. Use insights from all models to adjust rental rates or sale prices to maximize returns while staying competitive.

### Recommendations for Data Gurus group 5

Since we shall continue working Haven-Kings Property Management as our client and work on developing the models further as well as do machine learning. we need to check on below items :

**Multicollinearity:** Be wary of multicollinearity, especially with correlated predictors like bedrooms, bathrooms, and sqft_living. While it's essential to capture as much variance as possible, adding correlated predictors can destabilize regression estimates.


**Iterative Model Refinement:** Continuously refine and evaluate models based on new data and feedback. While these models provide valuable insights, the real estate market is dynamic, and models should adapt to changing conditions.


In summary, each model provides unique insights that can guide Haven-Kings Property Management in refining their pricing strategies. By considering the predictors highlighted in these models and being aware of potential pitfalls like multicollinearity, Haven-Kings can make more informed decisions and optimize their returns in the King County real estate market.


