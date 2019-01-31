# Utilizing Yelp Businesses Categories and price ranges to predict neighborhoods affluency

#### Authors: Jacopo Cecchi, Jason Leung

### Overview

1. [Objectives and Methodology](#Objectives-and-Methodology)
2. [Executive Summary](#Executive-Summary)
3. [Repository Structure](#Repository-Structure)
4. [Interactive Googlemaps Tool](#Interactive-Googlemaps-Tool)
5. [Project Workflow](#Project-Workflow)

<br></br>

### Objectives and Methodology

Within the scope of this work we develop a tool to estimate neighborhood affluency leveraging Yelp prices estimates and business categories information from Yelp.

Our goal is twofold: 

1. Develop a model to predict average income per capita in a given neighborhood leveraging Yelp local business data, each businesses general price range and business categories.
2. Develop a visualization tool that will deploy this model and let the user select any area in the US, view all businesses in the area and receive the income prediction given those businesses, all in real-time. 

![methodology_picture](./Images/Screenshot_2019-01-28.jpg)

<br></br>

### Executive Summary

- A working Googlemaps tool that allows users to retrieve affluency estimates for a given area given Yelp’s businesses and services costs estimates has been developed.
- Several supervised learning models – Logistic Regression, KNN, CART, Random Forest, Bagging Classifier, Adaboost and SVC have been trained and tested on a total count of 7 US cities. Among these, KNN resulted to be the best performing model.
- While models perform well – F1 score of ca. 90% on test sets of cities on which they are trained, their performance is inaccurate on testing sets of cities on which they have not been trained. We believe that this outcome is partially due to the fact that algorithms manage to identify geographic patterns in the data even if they are not fed businesses geographic coordinates directly.
- Our tool is relatively reliable at estimating a city’s neighbors affluency, BUT only when it has been trained on a set of observations of the specific city. Without a city-specific training, the model is not good at serving its purpose as it is accurate ca. less than 20% of the time.
- This study shows possibilities in predicting per capita income of a locality based just on Yelp estimates of surrounding businesses and services activities and prices.
- Further research could explore if models trained on a wide range of US cities would give better baseline predictions of affluency in non-training US cities.

For a more in depth overview of the project please refer to our presentation slides, which summarize our project, objectives, methodology and results. The slide pdf can be found [here](./Project_4_JLJC_01_18_19.pdf).

<br></br>

### Repository Structure

This repository contains all jupyter notebooks used in this project, named with a number prefix that indicates project stage. It also contains all necessary raw data files for the 7 US cities examined in the folder City_Raw_Data_Files, representative data files for each stage of the data processing pipeline, 1st cities and 2nd cities datasets for input to models in two named folders. The final cities datasets folder should primarily be used as it contains the most updated datasets with all Yelp scraped 2019 data. Trained predictive models used for our final results in the Models and Results folder include logistic classifiers and random forest classifiers for a range of bracketing of incomes.

The important notebooks will be summarized in the project workflow section below but for testing please refer to the [10_GoogleMaps_UserSearch.ipynb](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/10_GoogleMaps_UserSearch.ipynb) and [11_GoogleMaps_App.ipynb](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/11_GoogleMaps_App.ipynb) notebooks which utilize all stages of the project to output our Googlemaps visualization tool. In order to run the tool yourself, all files in the main directory should downloaded and the zipcode boundary files in folder zipcodes_geojson should be first unzipped. Lastly, you need a Googlemaps API key which is available to the public for free from google by request https://developers.google.com/maps/documentation/javascript/get-api-key, or please email Jason Leung for the project key.

<br></br>

### Interactive Googlemaps Tool

Our project tool takes advantage of the python module jupyter-gmaps to embed a fully functional googlemaps interface inside the notebook. With this tool, you can search by 1000 meter radius anywhere in the US. It will display all businesses within that radius, color coded by the main category of the business. The 12 buttons at the top of the interface allow you to select or de-select the display of each main business category. A gmaps marker (light red shape) indicates the center your serach radius and the text box right above the map will show the progress of the model behind-the-scenes in its processing and prediction of that specific coordinates average income. After processing, the text box will update with the predicted income bracket of that location, and a new search can be performed. The map will save and display the zip code boundaries, in light blue and the colored business types of only the previous two searches on screen.

![YelpBusinessesTool](C:/Users/Jason/Documents/YelpBusinesses-master/Images/YelpBusinessesTool.png)

<br></br>

### Project Workflow

This Yelp businesses project required intensive data munging and engineering in order to achieve the training datasets fed into each machine learning model. First, the Yelp provided Kaggle dataset was used, available here: https://www.kaggle.com/yelp-dataset/yelp-dataset. Notebooks [01_EngineerRows_andLasVegas.ipynb](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/01_EngineerRows_andLasVegas.ipynb), [03_VectorizeBusinesses_LasVegasTrainset_Model.ipynb](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/03_VectorizeBusinesses_LasVegasTrainset_Model.ipynb) through [04-4_LasVegas_Pipeline_toXtrain_(Readme_Code)](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/04-4_LasVegas_Pipeline_toXtrain_(Readme_Code).ipynb) process these raw latitude/longitude and category business information as well as raw US Census data files for income and population. The [02_Yelp_GetBusinessList.ipynb](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/02_Yelp_GetBusinessList.ipynb) contains all code to extract up to date Yelp city data, (for yelp api key please email Jason Leung). The 1st set of cities processed and analyzed can be walked through in notebooks 04-1 through 04-4, they are the highest business count cities in the Kaggle dataset and include Las Vegas, Phoenix, Charlotte and Pittsburgh. Refer to our slideshow in repository for details and for representative Las Vegas population and business density maps.





The interactive Googlemaps tool integrates all of the primary functionality of notebooks 01 through 09. It queries and extracts from Yelp all business data from locations within 1000 meters of the user given search point. With this raw data, it cleans, processes and engineers columns for distance from search point, and census block group population and income as well as the frequency of each combination of the top 148 business categories and each of Yelps for dollar sign price ranges. The tools current iteration is exclusively run in jupyter notebook. The [11_GoogleMaps_App.ipynb](https://github.com/jaswll/Yelp_Businesses_Project_Final/blob/master/11_GoogleMaps_App.ipynb) notebook provides a minimized interface for testing of the tool. 