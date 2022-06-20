# Demystifying normalized difference vegetation index for greenness exposure assessment and policy interventions in green cities

## Acknowledgements
Thesis project made in collaboration with S.M. Labib, Department of Human Geography and Spatial Planning, Utrecht University.

## Aims and objectives
A large volume of nature and health research mainly uses normalized difference vegetation index (NDVI) for measuring greenness exposure. However, little is known about what NDVI measures in terms of vegetation types (e.g., grass, canopy coverage) within certain analysis zones (e.g., 500m buffer). Additionally, little is explored on how changes in NDVI (e.g., per 0.1 increments) should be interpreted for policy intervention of urban greening. Therefore, this study aims to demystify NDVI by first investigating the sensitivity of NDVI values in relation to vegetation types and second by exploring how specific value increments of NDVI reflect changes in vegetation types and total greenness percentage.

## Technology
- Programming Language: used Python v3.9.10
- Environment: used Conda v4.11.0
- Computing Platform: used Jupyter Notebook v6.4.8
- Geographic Information System (GIS): used QGIS v3.16.16-Hannover
- Machine: used macOS Big Sur v11.6.5 (OS) and 2,3 GHz Dual-Core Intel Core i5 (processor)
- Running time: approximately 25 minutes

## Data processing

First, run **1_data_processing_ndvi.ipynb** to perform the required data processing in a single execution.

### 1. Read satellite images
The 5 steps process starts by reading greenness remote-sensed satellite images (i.e. input maps). From left to right, NDVI, Greenspace, Tree Canopy, Forbs and Shrubs, and Grass:

<img src="/visualizations_ndvi/ndvi_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/greenspace_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/canopy_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/shrubs_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/grass_input_map.png" width="200" height="160">
### 2. Perform focal statistics
Then, we assessed greenness exposure by averaging NDVI, greenspace, and vegetation values at 100, 300, and 500-meter buffer distances using focal statistics. The filters convolved over the input images were square-shaped and sized 21, 61, and 101 pixels, respectively.
### 3. Write output layers
In step number 3, we create output layers for greenness exposure at different spatial scales. From top to down, NDVI and Forbs and Shrubs. And from left to right, input map, 100, 300, and 500 meters greenness exposure:

<img src="/visualizations_ndvi/ndvi_input_map.png" width="250" height="200"><img src="/visualizations_ndvi/ndvi_output_layer_100.png" width="250" height="200"><img src="/visualizations_ndvi/ndvi_output_layer_300.png" width="250" height="200"><img src="/visualizations_ndvi/ndvi_output_layer_300.png" width="250" height="200">

<img src="/visualizations_ndvi/shrubs_input_map.png" width="250" height="200"><img src="/visualizations_ndvi/shrubs_output_layer_100.png" width="250" height="200"><img src="/visualizations_ndvi/shrubs_output_layer_300.png" width="250" height="200"><img src="/visualizations_ndvi/shrubs_output_layer_500.png" width="250" height="200">
### 4. Generate random point locations
Then, we performed data reduction by randomly filtering locations for 100, 300, and 500 meters buffer distance ensuring a complete data representation of the area of interest.
### 5. Extract raster values into a data frame
Finally, we sampled output layers at randomly generated locations to extract greenness exposure values. For instance, greenness metrics at 100 meters data frame should be as follows:

![](/visualizations_ndvi/df_ndvi_100.png)

## Exploratory data analysis

Next, we conducted an exploratory data analysis using the script **2_exploratory_data_analysis_ndvi.ipynb**, where we mainly obtained: 
1. Descriptive statistics of the greenness variables 
2. Data distributions (i.e. histograms) 
3. Linear regression models

<img src="/visualizations_ndvi/density_ndvi_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_green_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_canopy_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_shrubs_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_grass_100_plot.png" width="200" height="200">

## Exploratory GAMs analysis

Following the methodology, run **3_exploratory_gam_analysis_ndvi.ipynb** to get a better understanding of GAMs and including:

1.1. What are Generalized Additive Models (GAMs)

1.2. What parameters do those models include (distribution, link function, functional form, lambda, and splines)

1.3. How to perform model tuning (GCV, Effective DoF, AIC, Pseudo R-Squared, and grid search)

![](/visualizations_ndvi/exploratory_gam.png)

## Multivariate modelling

Execute the script **4_multivariate_modelling_ndvi.ipynb** to model NDVI using tree canopy, forbs and shrubs, and grass as predictors at 100, 300, and 500 m buffer sizes. The multivariate model explaining NDVI at an exposure of 100 meters should look like the following plot:

![](/visualizations_ndvi/gam_ndvi_100_best_plot.bmp)

## Univariate modelling

Finally, run **5_univariate_modelling_ndvi.ipynb** to model greenspace, tree canopy, forbs and shrubs, and grass using NDVI as a predictor at 100, 300, and 500 m spatial scales. Univariate models at 100 meters should be as follows:

<img src="/visualizations_ndvi/gam_greenspace_100_best_plot.png" width="300" height="250"><img src="/visualizations_ndvi/gam_canopy_100_best_plot.png" width="300" height="250">
<img src="/visualizations_ndvi/gam_shrubs_100_best_plot.png" width="300" height="250"><img src="/visualizations_ndvi/gam_grass_100_best_plot.png" width="300" height="250">

This thesis project acts as a final graduation project for the MSc in applied data science at Utrecht University.