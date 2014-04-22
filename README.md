<h1>Running the script</h1>
<ul>
<li>Clone this repository</li>
<li>Download the <a href="https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip">data set</a> and extract. It should result in a UCI HAR Dataset folder that has all the files in the required structure.</li>
<li>Change current directory to the UCI HAR Dataset folder.</li>
<li>Run Rscript <path to>run_analysis.R</path to></li>
<li>The tidy dataset should get created in the current directory as tidy.txt</li>
</ul>
<h1>Assumptions</h1>

The training and test data are available in folders named train and test respectively.
For each of these data sets:
Measurements are present in X_<dataset>.txt file
Subject information is present in subject_<dataset>.txt file
Activity codes are present in y_<dataset>.txt file
All activity codes and their labels are in a file named activity_labels.txt.
Names of all measurements taken are present in file features.txt ordered and indexed as they appear in the X_<dataset>.txt files.
All columns representing means contain ...mean() in them.
All columns representing standard deviations contain ...std() in them.

<h1>Data Preparation Steps</h1>

For each of the training and test datasets,
Read the X values
Take a subset of the columns representing only the mean and standard deviation values. Subsetting is done early on to conserve memory.
Associate additional columns to represent activity IDs and subject IDs read from y_<dataset>.txt and subject_<dataset>.txt files respectively.
Assign column names by manipulating the measurement names in features.txt to remove spaces and convert them to camel case.
Merge the training and the test sets, read as in step 1 to create one data set.
Associate an additional column with descriptive activity names as specified in activity_labels.txt.
Melt the dataset by specifying activity ID, name and subject ID as the only ID variables.
Re cast the melted dataset with activity name and subject id as the only IDs and mean as the aggregator function.
Save the resultin re-casted dataset as tidy.txt