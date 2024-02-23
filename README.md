# IBM-Data-Science-Capstone-SpaceX

# Introduction

![image](https://github.com/natrinJump/IBM_DataScience_CapStone_SpaceX/assets/143831822/9478a22d-ae1e-4ba1-b276-fe16e5e8855d)

## Background
SpaceX, a pioneering force in the space industry, is committed to democratizing space travel by striving to make it affordable for everyone. Their remarkable achievements encompass missions such as sending spacecraft to the International Space Station, deploying a satellite constellation for global internet access, and conducting crewed missions to space. SpaceX's ability to achieve these feats is attributed to the cost-effectiveness of their rocket launches, priced at $62 million per launch. This affordability is primarily due to their innovative approach of reusing the first stage of the Falcon 9 rocket. In contrast, other space providers, unable to replicate this reusability, have launch costs that soar to over $165 million per mission. The key to determining the launch price hinges on predicting the successful recovery of the first stage, a task that can be accomplished by leveraging publicly available data and employing machine learning models. This prediction allows for a more precise evaluation of whether SpaceX or a competing company can reutilize the crucial first stage.

## Summary
The research attempts to identify the factors for a successful rocket landing. To make this determination, the following methodologies where used:
* **Collect** data using SpaceX REST API and web scraping techniques
* **Wrangle** data to create success/fail outcome variable
* **Explore** data with data visualization techniques, considering the following factors: payload, launch site, flight number and yearly trend
* **Analyze** the data with SQL, calculating the following statistics: total payload, payload range for successful launches, and total # of successful and failed outcomes
* **Explore** launch site success rates and proximity to geographical markers
* **Visualize** the launch sites with the most success and successful payload ranges
* **Build Models** to predict landing outcomes using logistic regression, support vector machine (SVM), decision tree and K-nearest neighbor (KNN)

## Results

### Exploratory Data Analysis:
* Over time, there has been a noticeable enhancement in launch success rates.
* Among the various landing sites, KSC LC-39A stands out with the highest rate of success.
* The orbits ES-L1, GEO, HEO, and SSO have all maintained a flawless track record with a 100% success rate.

### Predictive Analytics
* All models performed similarly on the test set. The decision tree model slightly outperformed when looking at .best_score_

# Methodology
## Data Collection - API

* **Request Data**: Retrieve rocket launch data from the SpaceX API through API requests.
* **Decode Response**: Decode the received API response using `.json()` and convert it into a DataFrame using `.json_normalize()`.
* **Custom Functions**: Use custom functions to gather specific launch information from the SpaceX API.
* **Create Dictionary**: Organize the collected data into a dictionary.
* **Create DataFrame**: Transform the dictionary into a DataFrame for structured data analysis.
* **Filter Falcon 9 Launches**: Apply a filter to the DataFrame, keeping only Falcon 9 launch data.
* **Replace Missing Payload Mass Values**: If any payload mass values are missing, fill them with the calculated mean.
* **Export to CSV**: Save the processed data as a CSV file for future reference.

## Web Scraping Data Collection

* **Request Data**: Fetch Falcon 9 launch data from a Wikipedia page using web scraping techniques.
* **Create BeautifulSoup Object**: Parse the HTML response into a BeautifulSoup object for structured data extraction.
* **Extract Column Names**: Identify and extract column names from the HTML table header.
* **Collect Data from HTML Tables**: Parse HTML tables to gather information about Falcon 9 launches.
* **Create Dictionary**: Structure the scraped data into a dictionary.
* **Create DataFrame**: Convert the dictionary into a DataFrame for organized data analysis.
* **Export to CSV**: Save the web-scraped data as a CSV file for storage and future analysis.

## Data Wrangling
* **Convert outcomes** into 1 for a successful landing and 0 for an unsuccessful landing

## Maps with Folium
* **Create maps** to visualize launch sites, view launch outcomes and see distance to proximities

## Dashboard with Plotly Dash
* **Create dashboard**
* Pie chart showing successful launches
* Scatter chart showing Payload Mass vs. Success Rate by Booster Version

## Predictive Analytics

* **Create NumPy Array**: Generate a NumPy array from the Class column.
* **Standardize Data**: Apply data standardization using StandardScaler. Fit and transform the data.
* **Split Data**: Divide the data into training and testing sets using train_test_split.
* **GridSearchCV Optimization**: Construct a GridSearchCV object with 10-fold cross-validation for parameter optimization.
* **Apply GridSearchCV**: Utilize GridSearchCV to evaluate various algorithms, including logistic regression (LogisticRegression()), support vector machine (SVC()), decision tree (DecisionTreeClassifier()), and K-Nearest Neighbor (KNeighborsClassifier()).
* **Accuracy Calculation**: Calculate the accuracy on the test data for all models using the .score() method.
* **Confusion Matrix Assessment**: Assess the confusion matrix for each model.
* **Best Model Identification**: Identify the best model based on Jaccard Score, F1 Score, and overall Accuracy.

# Conclusion

* **Model Performance**: The models demonstrated comparable performance on the test dataset, with a slight advantage observed for the decision tree model.
* **Equatorial Advantage**: Notably, most launch sites are situated near the equator, capitalizing on the natural rotational speed of the Earth. This proximity helps reduce the need for additional fuel and boosters, enhancing cost-efficiency.
* **Proximity to Coast**: All launch sites are strategically located near coastal regions.
* **Launch Success Trend**: There is a discernible trend of increasing launch success rates over time.
* **KSC LC-39A Success**: KSC LC-39A stands out with the highest success rate among launch sites. Notably, it boasts a 100% success rate for launches with payloads less than 5,500 kg.
* **Orbit Success**: Orbits such as ES-L1, GEO, HEO, and SSO exhibit a remarkable 100% success rate.
* **Payload Mass Influence**: Across all launch sites, there is a clear correlation between higher payload mass (kg) and increased launch success rates.





