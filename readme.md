The project contains
- the script: run_analysis.R
- the data dictionary: CodeBook.md

The Samsung data must be in the current working directory before running the script.
The expected files are:
- activity_labels.txt
- features.txt
- test\subject_test.txt
- test\X_test.txt
- test\y_test.txt
- train\subject_train.txt
- train\X_train.txt
- train\y_train.txt

The script may be ran through the R command:
source("run_analysis.R")

The script may take some time to execute, as the data is quite large.

On exit, 2 variables are added to the R environment:
- full_dataset
  which is the detailed data frame merging the "train" and "test" data

- summarized_dataset
  which is the aggregated data frame averaged by activity, subject
  (as submitted on Coursera)
