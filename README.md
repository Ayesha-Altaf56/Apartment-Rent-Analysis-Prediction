# Apartment Rent Analysis and Prediction

This project is an R-based data analysis and machine learning pipeline designed to analyze apartment rental data and build predictive models for rent prices. It uses a dataset of apartment listings (`apartments.csv`) to perform data cleaning, exploratory data analysis (EDA), and machine learning using Linear Regression and Random Forest algorithms.

## Prerequisites

To run this script, you will need R installed on your system along with the following R packages:
- `dplyr`: Data manipulation
- `tidyr`: Data tidying
- `ggplot2`: Data visualization
- `VIM`: Visualization and imputation of missing values
- `mice`: Multivariate imputation by chained equations
- `corrplot`: Graphical display of a correlation matrix
- `randomForest`: Random Forest algorithm for regression and classification

You can install these packages using the following R command:
```R
install.packages(c("dplyr", "tidyr", "ggplot2", "VIM", "mice", "corrplot", "randomForest"))
```

## Dataset

The analysis relies on a dataset named `apartments.csv`. The dataset is expected to be placed in the same directory as the R script or you must update the `setwd()` function inside the script to point to the correct path. It uses `;` as the column separator.

## Project Workflow

### 1. Data Cleaning and Preprocessing
- **Type Conversion:** Cleans and converts `price`, `square_feet`, `bedrooms`, and `bathrooms` columns into numeric data types by removing non-numeric characters (like `$` and `,`).
- **Missing Values:** Identifies and removes rows containing missing (`NA`) values.
- **Deduplication:** Removes any duplicate rows.
- **Outlier Handling:** Detects outliers in `price` and `square_feet` using the Interquartile Range (IQR) method and caps them at the upper and lower bounds.
- **Categorical Encoding:** Converts relevant text columns (e.g., `category`, `currency`, `pets_allowed`, `cityname`, `state`) into categorical factors.
- **Feature Scaling:** Applies Min-Max scaling to `square_feet` and Z-score standardization to `price` for certain analyses.

### 2. Exploratory Data Analysis (EDA)
- **Univariate Analysis:** Visualizes the distribution of rent prices and apartment square footage using histograms, and charts the top 10 cities by listing count.
- **Multivariate Analysis:** Explores relationships between variables, such as price vs. square feet, price variations by pet policies using boxplots, and the top 10 states with the highest average rents.
- **Correlation Analysis:** Computes and visualizes a correlation matrix for numeric variables (`price`, `square_feet`, `bedrooms`, `bathrooms`).

### 3. Predictive Modeling
The project builds and evaluates several models to predict apartment rent prices:
- **Data Preparation:** Limits factor levels (e.g., `cityname`, `state`) to the top 10 most frequent categories to prevent errors with the Random Forest model (>53 levels limit). The data is split into an 80% training set and a 20% testing set.
- **Linear Regression (Part 5A):** Trains a baseline linear model using dummy variables for categorical features. Evaluates performance using Root Mean Squared Error (RMSE) and plots actual vs. predicted values.
- **Random Forest Regression (Part 5B):** Trains a Random Forest model with 100 trees. Evaluates performance using RMSE and generates plots for actual vs. predicted values, residuals, and feature importance.
- **Random Forest Classification (Part 5C):** Categorizes rent prices into "Low", "Medium", and "High" tiers based on quantiles. Trains a Random Forest classifier to predict the price tier, evaluating it using Accuracy and a Confusion Matrix heatmap.
- **Model Comparison (Part 5D):** Compares the RMSE of the Linear Regression and Random Forest regression models using a bar chart to determine the best-performing model.

## How to Run

1. Clone or download the repository to your local machine.(Kaagle dataset link: https://www.kaggle.com/datasets/shashanks1202/apartment-rent-data)
2. Ensure you have R installed and the required libraries.
3. Place `apartments.csv` in your working directory.
4. Open `Apartment_Analysis_Final (2).R` in RStudio or your preferred R environment.
5. Update the `setwd("")` line (around line 16) to match your local project directory path where the data file is stored.
6. Run the script entirely or block by block to see the analysis and visualizations.
