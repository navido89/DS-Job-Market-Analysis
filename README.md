<img src="Images/Think_Outside_The_Box.jpg">

<!-- Add buttons here -->
![Follow me at Twitter](https://img.shields.io/twitter/follow/NMashinchi?style=social)
![GitHub last commit](https://img.shields.io/github/last-commit/navido89/Time-Series-Analysis-ARIMA-Model-Covid19-Predictions)

# California Data Science Job Market Analysis
**Project Status: Completed**
<br>
<a href="https://nbviewer.jupyter.org/github/navido89/Police_Force_US/blob/main/Police%20Force%20Project.ipynb" target="_blank">Jupyter Notebook Viewer</a>
<br>
<a href="https://towardsdatascience.com/an-examination-of-fatal-force-by-police-in-the-us-db897d97085c" target="_blank">Read Article</a>

## Table of contents
- [Project Objective](#project-objective)
- [Methods Used](#methods-used)
- [Technologies](#technologies)
- [Project Description](#project-description)
- [Project Results](#project-results)
- [Installation](#installation)

## Project Objective
[(Back to top)](#table-of-contents)
<br>
The purpose of this project is to examine the factors that play into the horrible event of a fatal shooting by the police in the US. Which ones carry more weight that lead to fatal shootings and are perhaps predictive in nature? Are they race? State location? Mental Illness? Based on our findings from the dataset of the available variables, we are looking to predict the deceased’s race or mental illness status.
<br>
<p align="center">
<img src="images/shootings_by_year.png" style>
</p>

## Methods Used
[(Back to top)](#table-of-contents)
+ Data Cleaning
+ Exploratory Data Analysis
+ Data Visualization
+ Machine Learning

## Technologies:
[(Back to top)](#table-of-contents)
+ Pandas 
+ NumPy 
+ re
+ Seaborn
+ Matplotlib
+ Copy
+ Geopandas
+ Folium
+ Geopy
+ Nominatim
+ Template
+ MacroElement
+ PrettyTable
+ Sklearn - preprocessing
+ Sklearn.linear_model - LogisticRegression
+ Sklearn.preprocessing - StandardScaler
+ Sklearn.metrics - accuracy_score
+ Sklearn.svm - SVC
+ Sklearn.tree - DecisionTreeClassifier
+ Sklearn.ensemble - RandomForestClassifier
+ Sklearn.model_selection - cross_val_score
+ Sklearn.model_selection - RandomizedSearchCV

## Project Description:
[(Back to top)](#table-of-contents)

+ A dataset from the Washington Post was used, which had over 5700 data points and were collected between 2015-2020. 
+ Cleaned the data by using pandas. 
+ As far as feature engineering, 9 out of the total 17 variables type had to be transformed into different types. 
+ To read more about the data cleaning process <a href="https://towardsdatascience.com/an-examination-of-fatal-force-by-police-in-the-us-db897d97085c#9048" target="_blank">click here.</a>

## Project Results:
[(Back to top)](#table-of-contents)
<br>
With race being a big question going into this project, seeing the number of victims based on race seemed to be perfectly logical. Here we see that within all of the dataset White was killed the most and then black was almost half of the white percentage.
<p align="center">
<img src="images/big_observation.png" style>
</p>

Following now in the same line of questioning, we took a look at the physical location by state with respect to the races that were shot in those states:
<p align="center">
<img src="images/shooting_race_location.png" style>
</p>We saw that the majority of victims that are Hispanic have been shot by the police in the following States: Texas, New Mexico and California. This becomes evident when we pay attention to the purple dots. When looking at the dots with the pink colors. We can see that most of those are more centrally located in the country. We could possibly conclude that most of the Native Americans are in most danger in the central part of the country. As we can see with no surprise now, the majority of the victims are white. The green dots are spread all over the country. What is really interesting to point out is the majority of the yellow dots are on the East Coast. We see most of the dots on the right side of the country rather than the left side. This could be an indicator that black people are more in danger on the east coast when they interact with the police. We can definitely see fewer yellow markers on the west coast.<br/> 

Next, we wanted to see if shootings might have some kind of relation based on state.
<p align="center">
<img src="images/shooting_by_state.png" style>
</p>
We can see that a large majority of the victims were shot in California, Texas, and Florida, which makes sense as they are the top three most populated states. Whereas, in some of the smaller states, it shows there are fewer victims. Therefore, we decided to calculate the per capita number of victims by dividing the fatal shooting count per state by the state population size and then multiply that by 100,000.
<p align="center">
<img src="images/shooting_per_100k.png" style>
</p>
Surprisingly, our new top three results Alaska, New Mexico, and Oklahoma are relatively smaller states. It shows that there are more shootings on a relative basis in these states compared to the larger states, such as California. We create a heatmap that shows the level of concentration based on the shootings per 100,000 rate as seen in the previous bar graph. 
<p align="center">
<img src="images/heat_map.png" style>
</p>
Here, we can see that being in the mid-southwest around New Mexico and Oklahoma are not great places per capita for police shootings. Alaska with its size seems a possible outlier here.

In the plot shown below, we can see that the distribution of gender, race and signs of mental illness are unbalanced.
<p align="center">
<img src="images/mental_illness.png" style>
</p>

In the next plot we pay our attention to the feature "body cam footage" and check how that might determine whether an individual was shot. Below we can see that manny officers did have the camera off making this data skewed and hard to have as a determining variable.
<p align="center">
<img src="images/Body_cam.png" style>
</p>

Below we can see a box plot that represents the age distribution by race. The age distribution by race has a strong representation across all between the ages of 22 and 47, with a mean of 37. Please note, we replaced the 262 null values in the “age” column with the mean values based on race and gender.
<p align="center">
<img src="images/box_plot.png" style>
</p>

In order to create a model to predict signs of Mental Illness, we used the following ML algorithms:
   + Logistic Regression
   + SVC (Support Vector Classification)
   + SGD (Stochastic Gradient Descent)
   + Decision Tree
   + Random Forest
We train our model and get the following accuracy scores.
<p align="center">
<img src="images/signs_mental_illness1.png" style>
</p>
We picked the top 2 performing models from above and conducted a cross validation on them. Once we conducted the cross validation with a k-fold of 10 and scoring value of ‘accuracy’, we got the following results:
<p align="center">
<img src="images/signs_of_mental_illness2.png" style>
</p>
Clearly, we could see that our performing models were overfitting. We took the better performing model and started fine tuning it. The Random Forest performed better in comparison to the Decision Tree when cross validated. Next step is to tune the model. We use RandomizedSearchCV and tune the following parameters:

+ bootstrap: [True,False],
+ max_depth: [int(x) for x in np.linspace(start = 10, stop = 110, num =11)],
+ max_features: [“auto”,”sqrt”],
+ min_samples_split: [2,5,10],
+ min_samples_leaf: [1,2,4],
+ n_estimators: [int(x) for x in np.linspace(start = 200, stop = 2000, num =10)]

Our model improved from 0.724 to 0.772. Next we implement our model to the test set and we get an accuracy score of 0.771, which is the percentage of correctly predicted labels. 

In regard to predicting the race, we concluded that we would need to gather further data in order to create an acceptable model to predict the race. For more details <a href="https://towardsdatascience.com/an-examination-of-fatal-force-by-police-in-the-us-db897d97085c#86b5" target="_blank"> click here.</a>


Please <a href="https://towardsdatascience.com/an-examination-of-fatal-force-by-police-in-the-us-db897d97085c#eba2" target="_blank"> click here</a> for final conclusion.

## Installation:
[(Back to top)](#table-of-contents)
+ Clone this repo <a href="https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/cloning-a-repository" target="_blank">(for help see this tutorial).</a>
+ Raw data, data processing/transformation script is being kept in this repo. <a href="https://github.com/navido89/Police_Force_US/blob/main/Police%20Force%20Project.ipynb" target="_blank">Click here for notebook.</a>
+ **Note**: If GitHub doesn't load the notebook please refer to <a href="https://nbviewer.jupyter.org/github/navido89/Police_Force_US/blob/main/Police%20Force%20Project.ipynb" target="_blank">Jupyter Notebook Viewer.</a>
