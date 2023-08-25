# Project 4: Comparative Predictive Models of Drought

by Daniel Groneberg, Ben McPeek, and Joey Notaro

---

## Overview

The series of notebooks, data files, data visual images, and slideshow presentation contained herein include multiple machine learning models intended to improve drought predictions from a variety of datasets and modeling approaches. The task of developing a social impact model collectively was generated by General Assembly (GA), but the choice of datasets, problem statement, data collection methods, data analysis and visualization, machine learning models and iterations, and ultimate agency recommendations represent the expertise and opinions of the authors. The following README file contains an executive summary of the problem statement, data collection methods and sources, summary of final production models, and recommendations presented before California State Water Resources Board.

---

## Problem Statement

The California Department of Water Resources has hired a team of data scientists to develop comparative machine learning models for predicting upcoming droughts. The effects of global climate change have made it increasingly challenging to predict when a drought may be looming on the horizon but all the more imperative as more extreme weather events occur with increasing frequency.

The team of data scientists want to know:

**Which predictive model is the best indicator** of whether a drought is likely to occur **given historical weather, climate, and satellite image data? Does one model perform better** than any other in predicting drought or drought-like conditions for the state of California to declare forecasts of droughts more accurately?

The team of data scientists will use **three different models from three different datasets**, all employing different assumptions regarding risk of drought and all employing slightly different metrics to evaluate effectiveness. The team will then present its findings and make recommendations to the State Water Resources Board about how to best anticipate droughts for emergency preparedness.

---

## Data & Modeling Methods


#### Model 1 Dataset

The first dataset was collected from [Visual Crossing Weather](https://www.visualcrossing.com/) which shows the regions mean daily accounts of weather patterns by merging the information provided by the nearest weather stations (1992-2022). The data was cleaned by imputing missing values, dropping redundant columns, dummifying columns, and converting the date-time column to a formatted index. These datasets were used to create RNN, HW autoEST, SARIMA, and EnsembleForecast models which was evaluated using r2 and RMSE. For the reader's convenience this dataset's data dictionary is shown below:

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**datetime**|DateTime Index|Fresno, California|Dates daily from 1992-2022|
|**precip**|float64|Fresno, California|Precipitation in inches|



#### Model 2 Dataset

The second dataset was collected from a Kaggle Wildfire Prediction Dataset [source](https://www.kaggle.com/datasets/abdelghaniaaba/wildfire-prediction-dataset?select=train). The original dataset was compiled by the Kaggle contributor from Canada's government website, sourced from the government and municipalities of Quebec, which compiled images primarily from southern Quebec, dating back to 1976 [source](https://open.canada.ca/data/en/dataset/9d8f219c-4df0-4481-926f-8a2a532ca003). The image dataset was scanned for and removed any corrupted files. These data were used to create a **binary image classification convolutional neural network** which was evaluated using **accuracy**. A data dictionary is not provided for this dataset, as it is a directory of labeled jpg images contained within this git repository. The reader will find more information on this dataset of image in the exploratory data analysis and image preprocessing in Model 2.


#### Model 3 Dataset

The third dataset was collected from The Climatology Lab at UC Merced's TerraClimate model  [source](https://www.climatologylab.org/). and scraped by **explain scraping and cleaning methods here**. These data were used to create a **insert model type here** which was evaluated using **insert evaluation metric here**. For the reader's convenience this dataset's data dictionary is shown below:

|Feature|Type|Dataset|Description|
|---|---|---|---|
**datetime**|DateTime Index|Entire United States|Monthly Dates from 1958-2023|
|**soil_moisture**|float64|Entire United States|Total column moisture (mm)|
---

## Summary of Findings

Three different models were developed to predict drought from three different perspectives.

1. Model 1 predicted precipitation forecasting by month using a SARIMA model giving an RMSE of 0.0389 inches.
2. Model 2 predicted whether an image shows a wildfire region with 95% accuracy.
3. Model 3 predicted soil moisture forecasting using a SARIMA model giving an MSE of .143.

Based on the performance of these three models and the assumptions and limitations inherent in each of the models, the team of data scientists inferred that **Model 1** and **Model 3** might be the most suitable for making accurate forecasting predictions of drought due to being fast and cost-effective models. 

## Agency Recommendations

Based on the highest performing models, we recommend the following: The CNN image classification shows promise based on its high accuracy with a binary classification. We would highly recommend that the California State Water Resources Board invest in procuring satellite images and labeling those images based on drought severity, aligned with the U.S. Drought Monitor. This could be used to train a CNN on drought conditions based on the vegetation and the landscape. However, these kinds of images may be impractical to procure in a large enough dataset, so Sarima models of both soil moisture and precipitation may prove sufficient at forecasting where droughts may be occurring in the short-term. Since soil moisture was best forecast with only data from within the last decade or so, we can use this insight to structure Sarima models that only focus on that time frame. Sarima models are suggested to use for forecasting drought because they have proven to be successful, fast, and cost_effective. Future recommendations are to train our CNN model to determine drought landscape and feed that into a better performing RNN model.

* Based on this finding, the team recommends that the agency should consider using an SARIMA model with this easier accessible data for a cheaper method to forecast precipitation. Although models that use extensive data can have a smaller RMSE score this method can provide a faster and cheaper prediction.
* Satellite image classification is very promising given its high accuracy. The State Water Resources Board should invest in training multi-class models on labeled drought images to anticipate potential drought severity in the future.
* The primary finding of model three is that soil moisture has undergone a fundamental change in trajectory from 1958-2010 compared with 2010 onward. Whereas in earlier decades soil moisture had a neutral trend over time, in later years, the trend is clearly negative. The team recommends primarily using data from 2010 onward in order to create accurate soil moisture forecasts, as the previous era's data can no longer be reliably used.

