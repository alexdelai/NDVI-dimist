# Demystifying normalized difference vegetation index for greenness exposure assessment and policy interventions in green cities

## Acknowledgements

## Aim of the thesis

A large volume of nature and health research mainly uses normalized difference vegetation index (NDVI) for measuring greenness exposure. However, little is known about what NDVI measures in terms of vegetation types (e.g., grass, canopy coverage) within certain analysis zones (e.g., 500m buffer). Additionally, little is explored on how changes in NDVI (e.g., per 0.1 increments) should be interpreted for policy intervention of urban greening. Therefore, this study aims to demystify NDVI by first investigating the sensitivity of NDVI values in relation to vegetation types and second by exploring how specific value increments of NDVI reflect changes in vegetation types and total greenness percentage.

## Technology
1. Programming Language: used Python v3.9.10
2. Environment: used Conda v4.11.0
3. Computing Platform: used Jupyter Notebook v6.4.8
4. Geographic Information System (GIS): used QGIS v3.16.16-Hannover
5. Machine: used macOS Big Sur v11.6.5 (OS) and 2,3 GHz Dual-Core Intel Core i5 (processor)
6. Running time: approximately 25 minutes

## Data processing

Data processing was designed as the first script of the project and to be executed in a single command. The script's name is XXX. 
1. Read satellite images[NDVI / Greenspace / Tree Canopy / Forbs and Shrubs / Grass input maps visualizations]
2. Perform focal statistics
Assessed greenness exposure by averaging NDVI, greenspace, and vegetation values at 100, 300, and 500 meter buffer distances using focal statistics. The filters convolved over the input images were square-shaped and sized 21, 61, and 101 pixels, respectively.
3. Write output layers
[NDVI / Greenspace / Tree Canopy / Forbs and Shrubs / Grass output layers visualizations]
4. Generate random point locations
Performed data reduction randomly filtering 10,000 locations 100 and 300 meters apart and 5,000 points 500 meters away from each other to obtain a complete data representation of the area of interest.
5. Extract raster values into a data frame
Sampled output layers at randomly generated locations to extract greenness exposure values. The obtained datasets look as follows:
Data frame 100 / Data frame 300 / Data frame 500

## Exploratory data analysis

Next, we conducted an exploratory data analysis using the script XXX, where we mainly obtained: 
1. Descriptive statistics of the greenness variables 
2. Data distributions in form of histograms 
3. Linear regression models

[Introduce some EDA visualizations]

## Modelling
1. Generalized Additive Models exploration

The script XXX was used to get a better understanding of GAMs and includes:

1.1. What are GAMs

1.2. What parameters do those models include (distribution, link function, functional form, lambda, and splines)

1.3. How to perdorm model tuning (GCV, Effective DoF, AIC, Pseudo R-Squared, and grid search)

2. Multivariate modelling

The script XXX was used to explain NDVI using tree canopy, forbs and shrubs, and grass as predictors at 100, 300, and 500 m buffer sizes.

[Include multivariate partial dependence plots]

3. Univariate modelling

The script XXX was used to explain greenspace, tree canopy, forbs and shrubs, and grass using NDVI as a predictor at 100, 300, and 500 m spatial scales.

[Include univariate partial dependence plots]

The final structure of the repo and order of scripts should be as follows:
1. Readme
2. data_processing_ndvi
3. exploratory_data_analysis_ndvi
4. exploratory_gam_analysis_ndvi
5. multivariate_modelling_ndvi
6. univariate_modelling_ndvi
