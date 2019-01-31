# Utilizing Yelp Businesses Categories and price ranges to predict neighborhoods affluency

## Authors: Jacopo Cecchi, Jason Leung

### Overview

1. [Objectives and Methodology](Objectives-and-Methodology)
2. [Executive Summary](###Executive-Summary)
3. [Structure of the repository]()

### Objectives-and-Methodology

Within the scope of this work we develop a tool to estimate neighborhood affluency leveraging Yelp prices estimates and business categories information from Yelp.

Our goal is twofold: 

1. Develop a model to predict average income pro capita in a given neighborhood leveraging Yelp prices estimates and Yelp business categories.
2. Develop a tool and a UX that simplify the deployment of the model and the fruition of its predictions for a non technical user. 

![methodology_picture](./Images/Screenshot_2019-01-28.jpg)





Our presentation slides also summarizes our project, objectives, methodology and results. The slide pdf can be found [here](./Project_4_JLJC_01_18_19.pdf).





### Executive-Summary

- A working tool that allows to retrieve affluency estimates for a given area given Yelp’s businesses and services costs estimates has been developed and is available for deployment.
- Several supervised learning models – Logistic Regression, KNN, CART, Random Forest, Bagging Classifier, Adaboost and SVC have been trained and tested on a total count of 7 US cities. Among these, KNN resulted to be the best performing model.
- While models perform well – F1 score of ca. 90% on test sets of cities on which they are trained, their performance is inaccurate on testing sets of cities on which they have not been trained. We believe that this outcome is partially due to the fact that algorithms manage to identify geographic patterns in the data even if they are not fed businesses geographic coordinates directly.
- Our tool is relatively reliable at estimating a city’s neighbours affluency, BUT only when it has been trained on a set of observation of the specific city. Without a city-specific training, the model is not good at serving its purpose as it is accurate ca. less than 20% of the time.
- This study shows possibilities in predicting per capita income of a locality based just on Yelp estimates of surrounding businesses and services activities and prices.
- Further research could explore if models trained on a wide range of US cities would give better baseline predictions of affluency in non-training US cities.

For a more in depth overview of the project please refer to the [project presentation](./Project_4_JLJC_01_18_19.pdf).

**3. Structure of the repository**



kaggle dataset USA cities: Las Vegas (27k count), Phoenix (17k), 

Charlotte (8.5k), Pittsburgh (6.4k)



![YelpBusinessesTool](./Images/YelpBusinessesTool.png)