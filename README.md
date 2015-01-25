# Getting and Cleaning Data - calss project

This script reads train and test files from a wearable database, 
merges into one big data set the measurment values, the subject data, the activity data
and the columns names.
It then shrinks the data set to include only the mean and std measurments (df), replaces the activity numbers 
index with descriptive values and labels the data set with appropriate descriptive variable names.
Lastly it creates a seperate data set (tidyds) that summarizes the average of each measurment by activity 
and by subject.

To run the script simply save it and submit()

## It starts with read the files for the train and test sets - measurments (x), acttivity (y), subject (sbj), variable names (features)

## Part 1 - Merge the training and the test sets to one data set
1st step - combining seperately the test & train columns into combined tables (combined_test, combined_train) 
            It combines Subject in the 1st column, Activity and then the measurements
2nd step - combining test & train combined tables into one big table by rows (cmbntable)
3rd step - Assigning coulmn headers - it subsets column #2 of the feature table to get a vector of the variable original names (cnames)
Then uses the unique=TRUE feature of the make.names() function to avoid a situation where R views two column names the same given the special characters in the original names (i.e. avoiding the error: found duplicated column name)
Then it assign the names to the combined table by order c("Subject", "Activity", uniqcnames)

## Part 2- Extract only mean and stDev for each measurement
Using the select function it subsets the big combined table to one (df) that includes the subject and activity columns and only "mean" and "std" measurements.
I didn't include "meanFreq" as I read it as mean frequency which is different than mean.
The select function looks like that:
  select(Subject,Activity,contains("mean"), contains("std"), -contains("meanFreq"))

## 3 - Use descriptive activity names to name the activities in the data set
Using the activity_labels.txt file it replaces the index activity in the data set with the activity names - each number corresponds to a different activity name in the txt file

## 4 - Label the data set with descriptive variable names
Using function from the stringr package the script goes through a few steps to make create a proper descriptive variable names:
BodyBody --> Body;
Deletes any dot (the unique function used before created the multiple dots);

### replacing first letter with discriptive name: t --> Time, f--> Freq;
Using the (sub("t", "time",df) function is too risky since it might recognize the letter t in another location of a name and might create a totally unreasonable name. Therefore I frist seperated the 1st letter of each name using substr() function, then replaced the "t" and "f" with sub(), then paste the new name initial that I created with the rest of the name in the original vector with paste0() function.

## 5 - Create independent tidy data set (tidyds) with the average of each variable for each activity and subject
The script first group the new data set by Activity and the by Subject;
Then it calculatet the mean of each measurement (each column) by these groups using the summarise_each() function
