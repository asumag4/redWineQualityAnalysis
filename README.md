<img src="https://media.istockphoto.com/id/1422994721/photo/red-wine-in-glass-and-grape-on-wooden-barrel-with-vineyard.jpg?s=612x612&w=0&k=20&c=QoiffPIamBz8_B5eNrxbKPs2inAB2vhh4ua0afq02ow=" alt="red-wine">
# Red Wine Quality Analysis

## Project Overview
This project explores what makes red wine "good" by analyzing the publicly available [Red Wine Quality DataSet](https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009/code). The dataset, originally sourced from Cortez et al. (2008) at the University of Minho, contains physicochemical measurements (e.g., acidity, alcohol content) of various red wines, along with quality scores assigned by wine tasters.

Using statistical modeling and regression techniques, this project identifies key factors contributing to wine quality and builds predictive models to estimate wine ratings based on chemical properties.

## Objectives
1. Identify the most influential chemical properties affecting red wine quality.
2. Develop a multi-linear regression model to predict wine quality.
3. Evaluate the performance of the regression model on unseen data.
4. Address assumptions of linear regression, including normality and homoscedasticity.
5. Provide actionable insights for winemakers to enhance wine quality.

## Dataset
The dataset contains 1,599 observations with 12 variables:
- **Fixed Acidity**: Non-volatile acids contributing to wine's total acidity (g(tartaric acid)/dm³).
- **Volatile Acidity**: Acetic acid levels (g(acetic acid)/dm³).
- **Citric Acid**: A natural preservative and flavor enhancer (g/dm³).
- **Residual Sugar**: Sugar remaining after fermentation (g/dm³).
- **Chlorides**: Salt content (g(sodium chloride)/dm³).
- **Free Sulfur Dioxide**: Free form of SO2, a preservative (mg/dm³).
- **Total Sulfur Dioxide**: Bound and free forms of SO2 (mg/dm³).
- **Density**: Density relative to water (g/cm³).
- **pH**: Acidity level.
- **Sulphates**: Adds to wine’s bitterness and acts as an antioxidant (mg/dm³).
- **Alcohol**: Percentage of alcohol by volume (% vol).
- **Quality**: Quality score (integer values between 0 and 10).

## Methodology
### 1. Exploratory Data Analysis
- Inspected the distribution of each variable and its relationship to wine quality.
- Identified potential multicollinearity and interaction effects among predictors.

### 2. Data Splitting
- Divided the dataset into training (80%) and testing (20%) subsets for model building and evaluation.

### 3. Statistical Modeling
#### First-Order Additive Model
- Built a linear regression model using all independent variables.
- Used stepwise selection (via the `olsrr` package) to identify the most significant predictors.

#### Interaction and Higher-Order Terms
- Included interaction terms and polynomial terms for key predictors (e.g., sulphates and alcohol).
- Evaluated models using adjusted R-squared and residual standard error.

### 4. Assumption Testing
- Checked for linearity, homoscedasticity, and normality of residuals.
- Addressed violations using transformations but retained the original scale due to better interpretability.

### 5. Model Evaluation
- Assessed model performance on the test set using:
  - R-squared
  - Mean Absolute Percentage Error (MAPE)

## Key Findings
1. The top three factors influencing wine quality are:
   - **Alcohol**: A 1% increase in alcohol content raises the quality score by 0.292.
   - **Volatile Acidity**: A decrease of 1 g(acetic acid)/dm³ increases the quality score by 0.962.
   - **Sulphates**: A 1 mg/dm³ increase raises the quality score by 0.547.

2. Interaction terms involving volatile acidity, sulphates, and total sulfur dioxide also significantly affect wine quality.

3. The final model explains 38.13% of the variability in wine quality, with a mean absolute percentage error (MAPE) of 8.87% on the test set. While not highly predictive, the model provides valuable insights into the key drivers of wine quality.

## Limitations
- **Discrete Dependent Variable**: Wine quality is an integer, whereas the model predicts continuous values, leading to some mismatch.
- **Dataset Imbalance**: Most wines have quality ratings of 5 or 6, limiting the model's ability to predict higher-quality wines (e.g., quality = 8).
- **Unexplained Variance**: The model explains only 38.13% of the variability, suggesting other unmeasured factors (e.g., taste preferences, vineyard practices) contribute to wine quality.

## Technologies Used
- **R Programming**: Data manipulation, modeling, and visualization.
- **Libraries**:
  - `ggplot2` and `GGally`: Data visualization.
  - `olsrr`: Stepwise regression.
  - `lmtest`: Assumption testing.
  - `plotly`: Interactive plots.

## Conclusion
This project highlights the chemical properties that most influence red wine quality, providing a foundation for further research and refinement. While the model has limitations in predictive power, it offers actionable insights for winemakers to optimize wine quality through targeted adjustments to alcohol content, volatile acidity, and sulphates.

## Future Work
1. Explore non-linear models (e.g., Random Forest, Gradient Boosting) for better predictive accuracy.
2. Investigate additional features, such as grape variety, fermentation duration, or sensory attributes.
3. Address dataset imbalance to improve model performance for high-quality wines.

## References
1. Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical properties. *Decision Support Systems, 47(4)*, 547-553.

