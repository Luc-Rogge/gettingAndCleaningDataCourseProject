The project contains:

* the script: run_analysis.R
* the data dictionary: CodeBook.md

The source data files must be in the current working directory before running the script.
The expected input files are:

* activity_labels.txt
* features.txt
* test/
    * subject_test.txt
    * X_test.txt
    * y_test.txt
* train/
    * subject_train.txt
    * X_train.txt
    * y_train.txt

The script may be ran through the R commands:

* source("run_analysis.R")
* tidy_dataset <- run_analysis()

The returned data frame is averaged by activity, subject
(as submitted on Coursera).

The script may take some time to execute, as the data is quite large.