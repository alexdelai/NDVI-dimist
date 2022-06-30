# Demystifying normalized difference vegetation index (NDVI) for greenness exposure assessment and policy interventions in urban greening

## Acknowledgements
Thesis project was made in collaboration with S.M. Labib from the Department of Human Geography and Spatial Planning at Utrecht University.

## Aims and objectives
A large volume of nature and health research mainly uses normalized difference vegetation index (NDVI) for measuring greenness exposure. However, little is known about what NDVI measures in terms of vegetation types (e.g., grass, canopy coverage) within certain analysis zones (e.g., 500m buffer). Additionally, little is explored on how changes in NDVI (e.g., 0.1 increments) should be interpreted for policy intervention of urban greening. Therefore, this study aims to demystify NDVI by first investigating the sensitivity of NDVI values in relation to vegetation types and second by exploring how specific value increments of NDVI reflect changes in vegetation types and percent of green spaces.

## Technology
- Programming Language: used Python v3.9.10
- Environment: used Conda v4.11.0
- Computing Platform: used Jupyter Notebook v6.4.8
- Geographic Information System (GIS): used QGIS v3.16.16-Hannover
- Machine: used macOS Big Sur v11.6.5 (OS) and 2,3 GHz Dual-Core Intel Core i5 (processor)
- Running time: approximately 25 minutes

## Data processing

First, run **1_data_processing_ndvi.ipynb** to perform the required steps to process greenness metrics for different buffer zones.

### 1. Step 1: process satellite images
The methodology starts by processing remotely sensed satellite images for five greenness metrics. From left to right, NDVI, overall green spaces, tree canopy, forbs and shrubs, and grass presence:

<img src="/visualizations_ndvi/ndvi_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/greenspace_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/canopy_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/shrubs_input_map.png" width="200" height="160"><img src="/visualizations_ndvi/grass_input_map.png" width="200" height="160">
### 2. Step 2: focal statistics analysis
Then, we assessed greenness exposure by averaging NDVI, greenspace, and vegetation presence at 100, 300, and 500 m buffer distances applying focal statistics. The filters (i.e. buffer zones) convolved over the input images had a rectangle shape and sized 21, 61, and 101 pixels (for 10 x 10 m resolution image), respectively.
### 3. Step 3: development of greenness exposure maps
Here, we created greenness exposure maps (i.e. output layers) for different buffer zones (i.e. spatial scale). From top to down, NDVI and forbs and shrubs density. And from left to right, input image, and greenness exposure for 100, 300, and 500 meters distance:

<img src="/visualizations_ndvi/ndvi_input_map.png" width="250" height="200"><img src="/visualizations_ndvi/ndvi_output_layer_100.png" width="250" height="200"><img src="/visualizations_ndvi/ndvi_output_layer_300.png" width="250" height="200"><img src="/visualizations_ndvi/ndvi_output_layer_300.png" width="250" height="200">

<img src="/visualizations_ndvi/shrubs_input_map.png" width="250" height="200"><img src="/visualizations_ndvi/shrubs_output_layer_100.png" width="250" height="200"><img src="/visualizations_ndvi/shrubs_output_layer_300.png" width="250" height="200"><img src="/visualizations_ndvi/shrubs_output_layer_500.png" width="250" height="200">
### 4. Step 4: random location samplnig within the study area
Then, we performed data reduction by randomly sampling locations within the Greater Manchester boudaries for 100, 300, and 500 meters buffer distance ensuring the data representation of the study area.
### 5. Step 5: extraction of raster values
Finally, we sampled greenness exposure maps at the randomly generated locations to extract raster or cell values and stored them into three different dataframes (one per buffer zone). For instance, greenness metrics at 100 meters data frame should be as follows:

![](/visualizations_ndvi/df_ndvi_100.png)

## Exploratory data analysis

Next, we conducted an exploratory data analysis using the script **2_exploratory_data_analysis_ndvi.ipynb**, where we mainly investigated: 
1. Statistics describing different greenness metrics 
2. Data distributions for greenness metrics
3. Linear regression models

<img src="/visualizations_ndvi/density_ndvi_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_green_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_canopy_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_shrubs_100_plot.png" width="200" height="200"><img src="/visualizations_ndvi/density_grass_100_plot.png" width="200" height="200">

## Exploratory GAMs analysis

Following the methodology, run **3_exploratory_gam_analysis_ndvi.ipynb** to get a better understanding of GAMs:

1.1. Introduction to Generalized Additive Models (GAMs)

1.2. Components and parameteres of GAMs (distribution, link function, functional form, lambda, and splines)

1.3. How to select the best model and tune the model (GCV, Effective DoF, AIC, Pseudo R-Squared, and grid search)?

![](/visualizations_ndvi/exploratory_gam.png)

## Multivariate analysis

Execute the script **4_multivariate_analysis_ndvi.ipynb** to explore the sensitivity of NDVI to vegetation types and amounts of vegetation for different buffer zones in a multivariate model. The multivariate model explaining NDVI for a buffer distance of 100 meters should be as follows:

![](/visualizations_ndvi/gam_ndvi_100_best_plot.bmp)

## Univariate analysis

Finally, run **5_univariate_analysis_ndvi.ipynb** to explore the sensitivity of vegetation types and amounts of vegetation to increments in mean NDVI for different bufffer zones in a univariate model. Univariate models for a buffer distance of 100 meters should be as follows:

<img src="/visualizations_ndvi/gam_greenspace_100_best_plot.bmp" width="300" height="250"><img src="/visualizations_ndvi/gam_canopy_100_best_plot.bmp" width="300" height="250">
<img src="/visualizations_ndvi/gam_shrubs_100_best_plot.bmp" width="300" height="250"><img src="/visualizations_ndvi/gam_grass_100_best_plot.bmp" width="300" height="250">

The results suggest that NDVI is sensitive to vegetation types and amounts of vegetation for different buffer zones and that vegetation densities and types of vegetation are sensitive to increments in mean NDVI (i.e. 0.1 increments) for different buffer zones. Furthermore, these sensitivies usually follow nonlinear patterns. Finally, our results address the mystery behind NDVI for greenness exposure assessment and might be translated into actionable policy interventions in urban greening.

Thesis project submitted to the Department of Information and Computing Sciences in collaboration with the Department of Human Geography and Spatial Planning in candidacy for the degree of Master of Science in Applied Data Science, Utrecht University.
