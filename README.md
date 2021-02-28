# README

## Installation

This project requires pandas, numpy, matplotlib, sci-kit learn, seaborn, and mplcyberpunk for visualization style. Python version 3.7.3 was used for this project.

## Project Motivation

This project looks at the factors that impact cost of an Airbnb in Seattle. I’m soon interested in renting my own house out on Airbnb, and I wanted to have an idea of what about my house, my location, or myself, would allow me charge more or less than other houses on the market. I look first at factors like zipcode and size, and how they interact with each other. Then I look at a simple model to pull in other factors that may influence price.

## File Descriptions

This repository has two primary files Airbnb_descriptive_dark.ipynb, and Airbnb_model_dark.ipynb. The former looks at some descriptive statistics about price and looks for simple correlations with price. The latter builds a model using numerical and categorical variables to predict Airbnb price. Both files load in the necessary libraries.

## How To Interact With Project

I first looked at a distribution of prices of Airbnb’s in seattle and found a slightly bimodal distribution, would could account for the linear model I tried and will describe in a moment not having a very high rsquared. The next thing i did was to examine how the density of Airbnbs in a zipcode impacted price. A scatterplot shows a relationship visually, and a pearson and spearman each showed a positive correlation, though the spearman was noticeably stronger. This is likely to be because the data for zipcode can be considered nominal in nature.

Next, I wanted to see if the number of bedrooms in an airbnb had more influence than density of zipcode. A scatterplot of price and bedroom colored by zipcode shows a linear relationship between number of bedrooms and price. The zipcode colors can be seen rather evenly distributed amongst these points suggesting that impacts of zipcode and bedroom are somewhat independent. A correlation heatmap shows a rsquared of 0.61 between bedrooms and price. This type of visualisation will be more useful if more variables were added to this analysis.

Finally, I tried a linear regression model using a subset of features to predict price. At first I tried using only numerical features, but this model performed very poorly. In the model given here, I used a subset of categorical and numerical features from the data file. I made dummy variables for the categorical features, and chose to drop the null values of the numerical features, as i did not feel it made sense to impute these features with mean or mode. This model ended up with upsides and downsides. The major downside is that the rsquared on the training and test data was mediocre - 0.61 in both cases. The good upside to this is that the model performed equally well on training and test data, so the model did not overfit.

One other issue with the model is that a few features have coefficients that outweigh any of the other features by several orders of magnitude. This made it hard to understand what besides these 4 features are impacting the model, and suggests it ought to be tuned to have a more balanced set of feature importances. Finally, these 4 most important features were NaN dummys, which makes them hard to interpret, and may indicate that there is an unidentified latent factor accounting for the strength of these features.

## Licensing, Authors, Acknowledgements

The Seattle Airbnb dataset was provided by Kaggle through Udacity.
