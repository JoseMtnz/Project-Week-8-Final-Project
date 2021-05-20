<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100"/>

# Machine Learning to predict hotel cancellations
*[Jose Miguel Martinez Montero]*

*[Data Analytics Bootcamp Full Time | Mar21 - May21 | Iron Hack]*

## Content
- [Project Description](#project-description)
- [Hypotheses / Questions](#hypotheses-questions)
- [Dataset](#dataset)
- [Cleaning](#cleaning)
- [Analysis](#analysis)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Workflow](#workflow)
- [Organization](#organization)
- [Links](#links)

## Project Description

For this final project of the Bootcamp, I wanted to look into the possible applications of Data Analytics and Machine Learning in Tourism, specifically in the Hotel Industry, to which I belong for many years. 

The main goal of the project is to use the different statistical and Machine Learning techniques we learnt during the Bootcamp to predict the possibility of cancellation of a hotel reservation, based on the rest of the characteristics. Then, I will present the results altogether with other interesting data visualizations in a styled and engaging presentation.

The use of these Data Analytics techniques will allow the company to anticipate the possibility of cancellation of a reservation and act beforehand, adding value to the company and improving the business results through data-driven decisions.

To achieve this, we will use real data of 2019 provided by a recognized 4-star hotel located in central London, whose name will not be published for data protection reasons.

## Hypotheses / Questions

In this project, I will try to answer a business question which would be "Is it possible to predict and anticipate the possibility of cancellation of a reservation based on the details we have at booking time?". 

This project would ultimately help the Sales and Revenue department of the hotel to apply data-driven decisions to reduce the rate of cancellations during some moments of the year or give them more flexibility to deal with overbooking, among other applications.

## Dataset

As I mentioned before, the dataset was kindly provided by a well-known hotel located in Central London, and it contains all the reservations (cancelled and not) for the year 2019, the last year with proper figures before the outbreak of Covid-19.

The dataset contains 36.607 rows and 16 columns, and for each reservation we will have information related to the following topics:

- Reservation info (reservation ID, guest name, voucher, etc.) This information will be the first to be removed as it’s not interesting for our project.
- Reservation status (if the reservation was cancelled or not)
- Date (arrival date, departure date, booking date, cancellation date )
- Characteristics (rate, room type, number of people, meal, if the guest is VIP or not)
- Segmentation (market segment, market channel, country)

## Cleaning

The first step in a project of this type will be always inspecting the data to see what information it provides, and if there are any missing values and in which columns.

The next step was dropping the columns I already knew was not interesting for this project, (and also for data protection purposes) such as guest name, voucher, contact information, etc.

Then, I’ve also dropped the duplicated rows from the dataset to finally make a copy before doing further transformations to avoid modifying the original dataset.

## Analysis

First thing first, I checked the data types in the data set and I realized only the column ‘Reservation ID’ and ‘Number of people’ was numerical, the rest were python type ‘object’. 

Then, I went through an exploratory analysis of every feature to see the unique values contained and to see if any further transformation were needed, filling the null values and plotting some charts to display the information contained in each column in a clear way.

The first one was the column ‘Status', where the variable we wanted to predict was included (‘Cancelled' status), among another status as ‘Confirmed’ (if the customer finally checked in in the hotel), ‘No Show’ (not cancelled but never arrived) and 'Rejected'. These las two status has been removed as there were not interesting for this project, but I could perform another project to predict the possibility of a reservation to be 'No Show' in future improvements of this project.

Secondly, I've converted the time variables available in the dataset (arrival date and departure date) into 'date object type in order to perform Feature Engineering to make new features, which I thought could be interesting to predict the possibility of cancellation of one reservation (as it finally was):

- Length of the stay: number of nights stayed in the hotel (arrival-departure)
- Arrival month.
- Lead time: time elapsed between the booking date and the final arrival date (booking date - arrival)
- Cancellation Lead Time: number of days between the cancellation date and the arrival date (cancellation - arrival)
- Cancellation gap: number of days elapsed between the booking date and the cancellation date (booking - cancellation)
- Type of stay (if the reservation starts in a labour day and finishes in a labour day, if it starts in a labour day but finishes on a weekend day, etc)

For the remaining variables (Market channel, country, room type, rate etc), I've followed the next procedure: cleaning, relabeling when necessary to do it more understandable, and finally grouping the values ​​in the less number of categories possible in order to reduce the number of future rows when doing the next step before training the model: performing a preprocessing method named One Hot Encoding process.

For this previous step, my own knowledge in the field of study was really useful at the time of grouping the valued in a few big groups according to its nature.

At this point, I've got a dataset with only the features interesting for my model, with no null values and with the possible categories dummified (created new columns for each category and assigned 1 to each row if the condition is accomplished, and otherwise 0). This is the common procedure when we don't have numerical variables, being impossible to find the correlation between variables.

## Model Training and Evaluation

First of all, after splitting the dataset using de Train-Test split available in ScikitLearn library for python, I've tried different classification algorithms (Logistic Regression, K-N Neighbors, RandomForestClassifier, GradientBoostingClassifier) with different transformers for the data (StandardScaler and RobustScaler mainly) in order to identify the model with the best performance.

To achieve this, I've compared the Confusion Matrix of each one and compared the metrics of each one (accuracy, recall and Kappa/Cohen score). These metrics told me which were the model with more probability of predicting well if a reservation was cancelled or not, that finally is the K-N Neighbors with Robust Scaler, applying also the GridSearchCV to get the best number of neighbours (K). The recall for this model was 0.55 which is quite good but could be improved

Evaluating the model, we can observe there is a significant proportion between instances of one class and the other. This is very common when we are trying to predict binary variables, where the difference between instances is usually huge.

I handled this by performing an undersampling of the dataset with a method named TomekLinks from a python library called imblearn, typically used to deal with imbalanced datasets, as it's the case, for applying later the RandomUnderSampler method. What this method is doing is basically reducing the number of samples of the most frequent instance in a binary scenario in order to have a trained data set with the correct proportion between instances.

Applying the results of the same model that performed the best before (K-N Neighbors + Robust Scaler + GridSearchCV) the recall I've got (which is the metric I was using as a reference to compare the models according to this business case) was of an outstanding 0.77.

I've also compared the results doing an oversampling with a method named SMOTE, which is a method that artificially increases the number of samples of the less frequent instance, but the results were worse than with undersampling.

Finally, I've checked the importance of the features of the best model to find the more important features, which were the length of the stay, the lead time and the market channel, among others.

## Conclusion

As the main conclusion, I can confirm that it's possible to highly predict the possibility of a hotel reservation being cancelled with the information we have at booking time. as the algorithm found some patterns in common between the reservations that will be finally cancelled.

We can definitely apply Machine Learning in almost every sector of the industry in order to make accurate predictions and taking decisions based on data which can ultimately improve to performance of any business if we are aware of the importance of the data we generate while running a business, which were usually underestimated until now.

## Future Work

Future steps of this project would be:

- Performing timing series analysis with data of previous and posterior years, and investigating the effect of the Covid-19 pandemic in the cancellations of 2020 and 2021.

- Following the same procedure, as I've mentioned before, we can try to predict the possibility of a reservation being a ‘No show’, a problem which represents a huge amount of losses for every hotel at the end of the year and that could be anticipated as we saw at this project.

- In the same way, we can also anticipate a reservation to be fraudulent which is also a matter of importance, as like in the previous case, the main goal of the hotel is selling the maximum amount of rooms to maximize its revenue, and having fraudulent reservations or 'No Show's' will represent a lost opportunity to sell the room in another way.

## Workflow

The workflow used in this project was as follows:

1 - Data collection
2 - Data exploration / Data cleaning.
3 - Pre-processing / Feature selection.
4 - Model training
5 - Undersampling vs Oversampling
6 - Model evaluation / Error analysis
7 - Communicating the results

## Organization

For this project, I’ve used a Trello board in order to organize the tasks and the deadlines, which you can find in the links section, and also an amazing application named Canva to prepare the slides of the presentation.

Moreover, on this GitHub repository, you will find the different Juptyer notebooks used to perform the analysis (one for data cleaning/data preprocessing, a second one for modelling/evaluating the model and a third one just for testing purposes) altogether with the data sets used for the project.

## Links

[Repository](https://github.com/JoseMtnz/Project-Week-8-Final-Project)  
[Slides](https://www.canva.com/design/DAEeRqmhbEw/FD_VNRLcqHL8qYUI3DtQlQ/view?utm_content=DAEeRqmhbEw&utm_campaign=designshare&utm_medium=link&utm_source=sharebutton)  
[Trello](https://trello.com/b/zqJWZqOs/ml-for-hotel-cxls)  


