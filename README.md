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

The next step was dropping the columns I already knew were not interesting for this project, (and also for data protection purposes) such as guest name, voucher, contact information, etc.

Then, I’ve also dropped the duplicated rows from the dataset to finally make a copy before doing further transformations to avoid modifying the original dataset.

## Analysis

First thing first, I checked the data types in the data set and I realized only the column ‘Reservation ID’ and ‘Number of people’ was an integer, the rest were python type ‘object’. 

Also you can appreciate the columns were in spanish so I was translating everything in the process.
Then, I went through an exploratory analysis of every feature to see the unique values contained and to see if any further transformation were needed.

The first one was the column ‘Status;, where the variable we wanted to predict was included (‘Cancelled' status), among other status as ‘Confirmed’ (if the customer finally checked in), ‘No Show’ (not cancelled but not checked in) and 'Rejected'. These las two status have been removed as there were not interesting for this project but I would perfomr another project to predict the possibility of a reservation to be 'No Show' in future improvements of this project.


## Model Training and Evaluation

First of all. I've tried different classification models (Logistic Regression, K-N Neighbors, ...) with different transformers for the data (StandardScaler and RobustScaler mainly) in order to identify the model which best performance.

To achieve this, I've compared the Confusion Matrix g

Evaluating the model, we can observe there is a significant proportion between instances of one class and the other. This is very common when we are trying to predict binary variables, where the difference between instances is usually huge.

I handled this performir an undersampling of the dataset.

Finally, I've checked the Feature importance

## Conclusion

* Summarize your results. What do they mean?
* What can you say about your hypotheses?
* Interpret your findings in terms of the questions you try to answer.

## Future Work

Future steps of this project would be:
Performing timing series analysis with data of previous and posterior years, and investigating the effect of the Covid-19 pandemic in the cancellations of 2020 and 2021.

Following the same procedure, as I've mentioned before, we can predict the possibility of being a ‘No show’ of one reservat


## Workflow

The workflow used in this project was as follows:
1 - Data exploration / Data cleaning.
2 - Pre-processing: 

Then, we were exploring the different features to see the values contained, filling the null values and plotting some charts to display the information contained in each column on a clear way.

 

 I’ve asked 

How did you test the accuracy of your analysis and/or machine learning algorithm?

Perform the Feature Engineering to make new features
Perform the Feature Selection to select only relevant features
Transform the Data (Categorial to Numerical)
Split the data (Train Test Split)
Model the data (Fit the Data)
And finally, Evaluate our model
Data Preprocessing
 


## Organization

For this project, I’ve used a Trello board in order to organize the tasks and the deadlines that you can find in the links section, and also an amazing application named Canva to prepare the slides of the presentation.

Moreover, on this GitHab repository you will find the different Juptyer notebooks used to perform the analysis (one for data cleaning / data preprocessing, a second one for modelling/evaluating the model and a third one just for testing purposes) altogether with the data sets used for the project.






## Links


[Repository](https://github.com/JoseMtnz/Project-Week-8-Final-Project)  
[Slides](https://www.canva.com/design/DAEeRqmhbEw/FD_VNRLcqHL8qYUI3DtQlQ/view?utm_content=DAEeRqmhbEw&utm_campaign=designshare&utm_medium=link&utm_source=sharebutton)  
[Trello](https://trello.com/b/zqJWZqOs/ml-for-hotel-cxls)  


