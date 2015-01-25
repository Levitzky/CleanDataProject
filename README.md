# Getting and Cleaning Data - calss project

This script reads train and test files from a wearable database, 
merges into one big data set the measurment values, the subject data, the activity data
and the columns names.
It then shrinks the data set to include only the mean and std measurments (df), replaces the activity numbers 
index with descriptive values and labels the data set with appropriate descriptive variable names.
Lastly it creates a seperate data set (tidyds) that summarizes the average of each measurment by activity 
and by subject.

To run the script simply save it and submit()

# Read files - measurments (x), acttivity (y), subject (sbj), variable names (features)
## train files 
x_train <- read.table("./train/X_train.txt", header=FALSE)
y_train <- read.table("./train/Y_train.txt", header=FALSE)
sbj_train <- read.table("./train/subject_train.txt", header=FALSE)
## test files
x_test <- read.table("./test/X_test.txt", header=FALSE)
y_test <- read.table("./test/Y_test.txt", header=FALSE) 
sbj_test <- read.table("./test/subject_test.txt", header=FALSE)
## features file (table header)
features <- read.table("./features.txt", header=FALSE)

# Part 1 - Merge the training and the test sets to one data set
## 1st step - combining test & train columns
combined_test <-cbind(sbj_test, y_test, x_test)
combined_train <-cbind(sbj_train, y_train, x_train)
# 2nd step - combining test & train rows
cmbntable <-rbind(combined_train, combined_test)
# 3rd step - Assigning coulmn headers 
cnames <- as.character(features[,2]) 
uniqcnames<-make.names(cnames, unique=TRUE)
names(cmbntable) <- c("Subject", "Activity", uniqcnames)

## 2- Extract only mean and stDev for each measurement
df<-cmbntable %>% 
  select(Subject,Activity,contains("mean"), contains("std"), -contains("meanFreq"))

## 3 - Use descriptive activity names to name the activities in the data set
activitylabels <- read.table("./activity_labels.txt", header=FALSE)
df[,2] <- activitylabels[df[,2], 2]

## 4 - Label the data set with descriptive variable names
library(stringr)
names(df) <- sub("BodyBody", "Body", names(df), fixed = TRUE)
names(df) <- gsub(".", "", names(df), fixed = TRUE)
names(df) <- sub("Mean", "mean", names(df), fixed = TRUE)

# replacing first letter with discriptive name
discriptdfNames <- names(df)
firstletter<- substr(discriptdfNames,1,1)
firstletter<- sub("t","time",firstletter)
firstletter<- sub("f","freq",firstletter)
discriptdfNames<- substr(discriptdfNames,2,nchar(discriptdfNames))
discriptdfNames<- paste0(firstletter,discriptdfNames)
names(df)<- discriptdfNames
names(df) <- sub("f", "", names(df), fixed = TRUE)

## 5 - Create independent tidy data set with the average 
##    of each variable for each activity and subject
tidyds <- df
meanbygroupds <- tidyds %>% 
            group_by(Activity,Subject) %>%
            summarise_each(funs(mean))

## Save tidy data set to txt file
# write.table(meanbygroupds, file = "ProjectDataSet.txt",row.name=FALSE)

