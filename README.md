# IBM Data Science Professional Certificate Project

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DS0701EN-SkillsNetwork/api/Images/landing_1.gif)

## Table of content

- [Introduction](#introduction)
- [Background](#background)
- [Structure of the repository](#structure-of-the-repository)
- [Executive Summary](#executive-summary)
- [Results](#results)
- [Conclusion](#conclusion)


## Background

SpaceX, a leader in the space industry, strives to make space travel affordable for everyone. Its accomplishments include sending spacecraft to the international space station, launching a satellite constellation that provides internet access and sending manned missions to space. SpaceX can do this because the rocket launches are relatively inexpensive ($62 million per launch) due to its novel reuse of the first stage of its Falcon 9 rocket. Other providers, which are not able to reuse the first stage, cost upwards of $165 million each. By determining if the first stage will land, we can determine the price of the launch. To do this, we can use public data and machine learning models to predict whether SpaceX – or a competing company – can reuse the first stage.

## Structure of the repository

- [`notebooks/`](notebooks/): Includes Python notebooks for data cleaning, exploratory data analysis (EDA), and machine learning models.
- [`datasets/`](datasets/): Includes the datasets used and created for the project.
- [`images/`](images/): Includes images used in the readme, such as the cover and visualizations.
- [`presentation/`](presentation/): Includes the analisys presentation in PDF format and the dashboard.

## Executive Summary

The research attempts to identify the factors for a successful rocket landing. To make this determination, the following methodologies where used:

- **Collect** data using SpaceX REST API and web scraping techniques
- **Wrangle** data to create success/fail outcome variable
- **Explore** data with data visualization techniques, considering the following factors: payload, launch site, flight number and yearly trend
- **Analyze** the data with SQL, calculating the following statistics: total payload, payload range for successful launches, and total # of successful and failed outcomes
- **Explore** launch site success rates and proximity to geographical markers
- **Visualize** the launch sites with the most success and successful payload ranges
- **Build models** to predict landing outcomes using logistic regression, support vector machine (SVM), decision tree and K-nearest neighbor (KNN)

## Results

### Exploratory Data Analysis:

- Launch success rate has improved over time.
- Orbits ES-L1, GEO, HEO, and SSO have a 100% success rate.
- KSC LC-39A has the highest success rate among landing sites.
- Most launch sites are near the equator, and all are close to the coast.

### Data Collection - SpaceX REST API 

- **Request data** from SpaceX API
- **Normalize** json data to convert into a dataframe
- **Filter** dataframe to contain only Falcon 9 launches
- **Replace** missing values with mean PayloadMass value

### Data Collection - Web Scrapping 

- **Request** Falcon 9 launch data from Wikipedia with BeautifulSoup
- **Extract** column names from HTML table header
- **Create** a dataframe by parsing the launch HTML tables

### Data Wrangling  

- **Calculate** the number of launches on each site, occurrence of each orbit, and occurence of mission outcome of the orbits.
- **Create** a landing outcome label from Outcome column

### EDA with SQL

- **Query** connecting to sqlite to see insights of the data

### Visualization 

- **Create charts** from the data using matplotlib and seaborn to compare and analyze relationships.

### Interative maps with Folium

- **Create interactive maps** to visualize launch sites, results and calculate the distance to proximities like railways, highways and cities.

### Predictive Analytics

- **Create** variable 'Y' with a NumPy array from the column Class in data.
- **Standardize** the data in 'X' with StandardScaler. Fit and transform the data.
- **Split** the data using train_test_split with test_size=20
- **Create** a GridSearchCV object with cv=10 for parameter optimization
- **Apply** GridSearchCV on different algorithms: logistic regression (LogisticRegression()), support vector machine (SVC()), decision tree (DecisionTreeClassifier()), K-Nearest Neighbor (KNeighborsClassifier())
- **Calculate** accuracy on the test data using .score() for all models
- **Assess** the confusion matrix for all models
- **Identify** the best model performance using Jaccard_Score, F1_Score and Accuracy

## Conclusion
* **Model Performance:** The models performed similarly on the test set with the decision tree model slightly outperforming
* **Equator:** Most of the launch sites are near the equator for an additional natural boost - due to the rotational speed of earth - which helps save the cost of putting in extra fuel and boosters
* **Coast:** All the launch sites are close to the coast just in case of failure of the launch, the satellite does not fall on built-up hinterland
* **Launch Success:** Increases over time thanks to new technology.
* **KSC LC-39A:** Has the highest success rate among launch sites. Has a 100% success rate for launches less than 5,500 kg 
* **Orbits:** ES-L1, GEO, HEO, and SSO have a 100% success rate
* **Payload Mass:** Across all launch sites, the higher the payload mass (kg), the higher the success rate