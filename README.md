# Airbnb Price and Performance Analysis

## About the Project
This project analyzes an extensive Airbnb listings dataset to understand the critical factors that influence rental prices. Using data science techniques such as data cleaning, exploratory data analysis (EDA), and regression/classification modeling, the goal is to identify key variables that affect pricing and build a model capable of predicting whether a listing will be classified as "expensive" or not. The insights derived from this project can help hosts better understand market dynamics and optimize their pricing strategies on the Airbnb platform.
**Project Repository:** [Airbnb-Price-and-Performance-Analysis](https://github.com/roshninair45-prog/Airbnb-Price-and-Performance-Analysis)

## Team Members
* [Valeria Vazquez Rueda]
* [Ni Xie]
* [Roshni Ramanathan]
* [Jiaqi Yuan]
* [Luis Gadiel Reyes Perez]
## About the Dataset
The data utilized for this project is stored in `Airbnb_Data.csv`, encompassing 74,111 listings with 29 feature columns. 
The dataset contains a mix of categorical, geographical, and numerical information about the listings, including:
* **Listing Details:** Property type, room type, accommodates, bathrooms, bedrooms, and beds.
* **Pricing & Policies:** Log price, cleaning fee, and cancellation policy.
* **Location Data:** City, latitude, longitude, and zipcode.
## Analysis Approach & Methodology
The analysis was conducted in a structured pipeline, transitioning from raw data processing to predictive modeling:
### 1. Data Cleaning & Imputation
To maintain dataset integrity and reduce noise, irrelevant columns or those with excessively high missing values (such as `first_review`, `host_response_rate`, `last_review`, `neighbourhood`, `review_scores_rating`, and `thumbnail_url`) were dropped. For critical numerical and categorical features with minor missing data (like `bathrooms`, `bedrooms`, `beds`, and host details), missing values were imputed using the mode (most frequent value) of their respective columns.
### 2. Feature Engineering & Target Creation
Raw temporal and pricing data were transformed into more interpretable formats. The `log_price` was converted back to an absolute `price` variable using an exponential function. For the predictive modeling phase, a new binary target variable named `expensive` was created, classifying listings as `1` (expensive) if their price was above the median, and `0` (not expensive) otherwise. Categorical features like `room_type` were also mapped to numerical values for machine learning compatibility.
### 3. Exploratory Data Analysis & Visualizations
To understand the geographical and physical profiles of the listings, we conducted visual analysis using Bar charts. We visualized the average prices grouped by `room_type` (Entire home vs. Private/Shared), `property_type` (Villa, Condominium, Loft, etc.), and `city` (San Francisco, DC, Boston, etc.). This helped identify specific listing characteristics and geographic trends that command premium pricing.
### 4. Correlation Analysis
Before modeling, we performed a thorough correlation analysis using a heatmap visualization. This step was crucial for identifying multicollinearity among independent variables (like `accommodates`, `bedrooms`, and `beds`) and understanding the underlying statistical relationships between the physical features of the listing and the actual price.
### 5. Predictive Modeling
We utilized the pre-processed and structured feature set (`room_type`, `accommodates`, `bathrooms`, `bedrooms`, `beds`, `number_of_reviews`) to train a classification algorithm. The data was split into 80% training and 20% testing sets, and standardized using `StandardScaler`. We performed **Logistic Regression** modeling to predict the `expensive` target variable. The model's performance was evaluated using Accuracy, Precision, Recall, F1-Score, ROC-AUC, and a Confusion Matrix.
## Conclusions
The exploratory analysis revealed that "Entire home/apt" and property types like "Villas" in cities like San Francisco command the highest average prices. The Logistic Regression model achieved a solid predictive **Accuracy of ~73.2%** and an **ROC-AUC of 0.78**. 
Analyzing the model's coefficients demonstrated that the number of people a listing `accommodates` and the number of `bedrooms` have the strongest positive impact on driving a listing into the "expensive" category. Conversely, a higher `number_of_reviews` and shared room types tend to correlate negatively with premium pricing. This framework provides a robust foundation for hosts to assess listing valuations based on fundamental property attributes.
## Tools and Techniques
* **Language:** Python
* **Data Manipulation & Cleaning:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Machine Learning & Modeling:** Scikit-Learn (Logistic Regression, StandardScaler)
* **Environment:** Google Colab
