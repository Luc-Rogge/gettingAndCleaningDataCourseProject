# Data purpose
The data has been collected from the accelerometers from the Samsung Galaxy S smartphone.
A full description is available at the site where the data was obtained: 
[Human Activity Recognition Using Smartphones](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

# Input data
The input data of run_analysis comes from:
[UCI HAR Dataset.zip](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)
The zip file contains a data dictionary in:
"UCI HAR Dataset\features_info.txt"
A readme file also explains how the data has been collected.

# Transformation steps
The input data is splitted in several ways:

* data rows are splitted accross "train" and "test" data
* data columns are splitted accross:
    * subject id (discrete variable)
    * activity id (discrete variable)
    * measures (named "features" in the input data) (561 continuous variables)
  

Transformations on that data include:

* for each initial data set ("train" or "test"):
    * reading the measure columns, by chunks (*)
    * keeping only the 66 measure columns of interest for our project (means and standard deviations)
    * binding the subject id column
    * binding the activity id column
    * translating the activity id column into a readable activity name column
* then the rows of the two datasets are unioned
* from that unioned dataset, a smaller aggregated dataset is computed, with the averages of the measures by subject, activity

(*) As the data is quite large, features are read by chunks of 500 rows, then useless columns are removed as soon as possible to save memory.
Other transformations are done only after the useless columns have been removed, so that no intermediate stage of the data exceeds 4GB (typical PC memory).


# Variables of the final data frames
Both datasets (the main one and the aggregated one) have the same variables:

* subject.id: numeric between 1 and 30, the id of the volunteer wearing the smartphone.

* activity.name: factor; the activity performed by the volunteer; 6 possible values:

    WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING

* 66 measures: numeric/double; either means or standard deviations,
    using the original names described in "features_info.txt",
    but slighlty transformed to be usable in R:
    
    prefix 't' to denote time or 'f' to denote Fast Fourier Transform (FFT)
    
    infix for the measure properly said: BodyAcc, GravityAcc, BodyAccJerk, BodyGyro, BodyGyroJerk, BodyAccMag, GravityAggMag, BodyAccJerkMag
    
    suffix for the kind of aggregate: .mean or .std (standard deviation)
    
    optional additional suffix for the axis of measurement: .X , .Y, .Z

    leading to the following name combinations for the 66 selected measures:
    * tBodyAcc.mean.X
    * tBodyAcc.mean.Y
    * tBodyAcc.mean.Z
    * tBodyAcc.std.X
    * tBodyAcc.std.Y
    * tBodyAcc.std.Z
    * tGravityAcc.mean.X
    * tGravityAcc.mean.Y
    * tGravityAcc.mean.Z
    * tGravityAcc.std.X
    * tGravityAcc.std.Y
    * tGravityAcc.std.Z
    * tBodyAccJerk.mean.X
    * tBodyAccJerk.mean.Y
    * tBodyAccJerk.mean.Z
    * tBodyAccJerk.std.X
    * tBodyAccJerk.std.Y
    * tBodyAccJerk.std.Z
    * tBodyGyro.mean.X
    * tBodyGyro.mean.Y
    * tBodyGyro.mean.Z
    * tBodyGyro.std.X
    * tBodyGyro.std.Y
    * tBodyGyro.std.Z
    * tBodyGyroJerk.mean.X
    * tBodyGyroJerk.mean.Y
    * tBodyGyroJerk.mean.Z
    * tBodyGyroJerk.std.X
    * tBodyGyroJerk.std.Y
    * tBodyGyroJerk.std.Z
    * tBodyAccMag.mean
    * tBodyAccMag.std
    * tGravityAccMag.mean
    * tGravityAccMag.std
    * tBodyAccJerkMag.mean
    * tBodyAccJerkMag.std
    * tBodyGyroMag.mean
    * tBodyGyroMag.std
    * tBodyGyroJerkMag.mean
    * tBodyGyroJerkMag.std
    * fBodyAcc.mean.X
    * fBodyAcc.mean.Y
    * fBodyAcc.mean.Z
    * fBodyAcc.std.X
    * fBodyAcc.std.Y
    * fBodyAcc.std.Z
    * fBodyAccJerk.mean.X
    * fBodyAccJerk.mean.Y
    * fBodyAccJerk.mean.Z
    * fBodyAccJerk.std.X
    * fBodyAccJerk.std.Y
    * fBodyAccJerk.std.Z
    * fBodyGyro.mean.X
    * fBodyGyro.mean.Y
    * fBodyGyro.mean.Z
    * fBodyGyro.std.X
    * fBodyGyro.std.Y
    * fBodyGyro.std.Z
    * fBodyAccMag.mean
    * fBodyAccMag.std
    * fBodyBodyAccJerkMag.mean
    * fBodyBodyAccJerkMag.std
    * fBodyBodyGyroMag.mean
    * fBodyBodyGyroMag.std
    * fBodyBodyGyroJerkMag.mean
    * fBodyBodyGyroJerkMag.std
