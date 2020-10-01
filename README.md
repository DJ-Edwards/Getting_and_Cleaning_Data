# Getting_and_Cleaning_Data
Coursera Week 4 Peer Project 

# Context

This is a peer graded assignent for the John Hopkins University R Foundations Course on Coursera.  It represents a demonstration of the R programming skills discussed focused on getting and cleaning data using **R**.

For this assingment I will: 

1) create a tidy data set 

2) create a Github repository to store/share my R scripts used for the analysis 

3) create a code book (using markdon) and a README file(this file) that describes the variables, the data, and any transformations.

# Data
For this assignent we will use data from a 2012 experiment concerning wearable technology.  Specifically, we will look at data collected from the accelerometers of the Samsung Galaxy S2 smartphone of 30 (19-48 yr old) humans during daily activities.

A full description is available at the site where the data was obtained:
<http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones>

The README.txt file inside of the UCI HAR Datset provides the information for how the user,activity and features information relates to the test and training set data. We will have to bring in the labels,features and user ids and bind this information with the test and training set information to make a tidy data frame.

# Explanation of run_analysis.R
This R script performs the following basic tasks.  Pulls the data from the provided website, and unzips the files to a directory called UCI HAR Dataset.  This script assumes you will perform your analysis by pulling from this directory.  After reading all the various data files of features, user activities, and observations, the script builds a data frame of the smart phone information.  Specifically ittakes the 10299 rows and adds the user information and the model prediction (activity-(X) based on the recorded variable( feature-(y)).  The initial data frame is 10299 rows and 563 columns.

Next the script updates the data labels into a more readable format, by taking the documented shorthand from the human trials and spells them out.  For example t denotes time, f denotes Frequency in experiment.  Similary the terms gyroscope, acclerometer, and magnitude replace the shorthand captured in the raw data.

A subset of the initial data frame is developed using dplyr and selecting on the column names which include the mean and standard deviation.  It also replaces activityId with the activity name (label).  These labels are the six activities sitting, standing, laying, walking, walking upstairs, or walking downstairs.  The subset has 10299 rows, but only 88 columns

Finally a Tidy_Result is developed and output as a txt file.  This Tidy_Result groups the subset data frame by userID (subject) and activity name (label) and summarizes the mean and standard deviation outputs for the experiment.  The Tidy_Result is 180 rows and 88 columns. This output represents the average of the 88 columns with mean or standard deviation in them for all 30 userID(subjects) and 6 activity names (label).

# CodeBook.md
This markdown file walks step by step through run_analysis.R providing amplyfying comments and provides the necessary detail to explain the modifications to the original data set so that the results can be reproduced by others and the modfications to make the dataset tidy are explicit.

# Tidy_Result.txt
This is the output of run_analysis.R script and result submitted for this peer graded assingment.
