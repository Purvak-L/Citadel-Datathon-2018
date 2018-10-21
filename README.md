# Citadel-Datathon-2018

What does a county's chemical contaminants say about its industrial activity?
We need a profile of each county's industrial activity.
We will build a profile of each county for a given year by concatenating a vector representing a county's water usage in 2010 and their occupation statistics for the given year. We normalize the water usage data for population and droughts during 2010 by predicting water usage based on population and drought, and subtracting these predictions from the water usage data. This will give us a baseline measurement of a county's industrial activity in 2010. We will also need to remove socioeconomic patterns from the industrial occupation data. We do this by performing PCA on water usage+occupation+earnings+education data and remove the eigenvectors heavily corresponding to earnings+education patterns. We will then concatenate the water usage data and the occupation data into a single feature vector for each year representing the county's industrial profile for that year. We normalize every column to a mean and variance of 1.

We can then correlate the profile with chemical contaminant levels
We will build a regression model to measure what an increase/decrease in contaminants say about industrial activity and vise versa. We will then cluster chemicals based on how they relate to industrial profiles (similarity of regression coefficients). We will then build a regression model from contaminants to changes in industrial activity (instead of the value at a given year). We then perform the same covariance and clustering as before.

Statistics:
Step 1
Build regression model from historical education attainment and the 2010 population to water usage. Subtract this inferred value from water usage.
Calculate covariance between occupation and water, earnings, and education.
Perform PCA on water usage, occupation, earnings and education (normalizing first).
Recompute occupation data with SES-heavy components removed.
Recalculate covariance between occupation and water, earnings, and education.
Concatenate occupation vector and water usage data (duplicating water usage data for each year).
Step 2
Build a regression model from industrial vector to chemical contaminants data (normalizing first).
Calculate contaminant predictions after perturbing regression and vise-versa.
Cluster chemicals based on their regression coefficients.
Repeat except using year-wise change in industrial vector (y_n+1 - y_n) instead of y_n.
Visualizations/graphs:
Covariance matrix of water usage, drought and population before and after normalizing water usage data.
Covariance matrix of occupation and peripherals before and after PCA.
Visualize PCA removal of SES.
Feature importances of the industrial vector.
Visualize effect of perturbing regression?
Cluster map visualizing similarity of regression coefficients for each chemical.
