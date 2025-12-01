# Prediction of Customer Churn
This project is an assignment for the Statistical Inference and Modelling course. The goal of the project is to perform a **formal statistical analysis** of the dataset and build a **general linear model that predicts the churn rate** of customers in the Telco public dataset. The project was done in a group of 3 people and was written in **R programming language**. The project contains the following steps:

1. Missing value handling: The value 0 was given for missing numerical variables where it made sense, like number of fireplaces, while other missing data was imputed using MICE.
2. Oversampling: Because the dataset is imbalanced, ROSE was used to generate more positive samples
3. Discovery and handling of outliers: Univariate outliers were chosen based on the inter-quartile range (IQR). Severe outliers, i.e. values exceeding the median by 3*IQR were few and so removed to enable building a better model. Mutlivariate outliers were discovered using moutlier function in R, which uses Mahalanobis distance. These were alse few and subsequently removed. The removed outliers were kept separately, but their analysis was outside the scope of this assignment.
4. Each variable was analyzed individually: The analysis included normality, autocorrelation and feature importance using a general linear model (GLM).
5. Feature transformation: The transformation were log-transform, and polynomial transformation using MLE
6. Model: Model was built iteratively by adding the most influential (transformed) numerical variables, then categorical ones and finally their interactions. The final model is has the AUC of 0.82 and has the following definition (written in R): \\\\ model <- glm(Churn ~ poly(MonthlyCharges,2) + poly(TotalCharges,2) + poly(tenure,3), data = train, family = "binomial")
7. Residual analysis
