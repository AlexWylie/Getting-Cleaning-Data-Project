# Getting-Cleaning-Data-Project
==================================================================
Human Activity Recognition Using Smartphones Dataset
Version 1.0
==================================================================
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Universit‡ degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws
==================================================================
Within this repository is an RScript named run_analysis.R, which receives data from the below experiments.
It then tidies the data set and returns a smaller data set with the averages of each variable for each activity and each subject.

#Experiment:

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. 
Each person performed six activities (walking, walkingUpstairs, walkingDownstairs, sitting, standing, laying) 
wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, 
we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz.
The experiments have been video-recorded to label the data manually.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then
sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window).
The sensor acceleration signal, which has gravitational and body motion components,
was separated using a Butterworth low-pass filter into body acceleration and gravity.
The gravitational force is assumed to have only low frequency components,
therefore a filter with 0.3 Hz cutoff frequency was used. 
From each window, a vector of features was obtained by calculating variables from the time and frequency domain.
See 'features_info.txt' for more details. 

For each record it is provided:
======================================

- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

The dataset includes the following files:
=========================================

- 'README.txt'

- 'CodeBook.md': Provides further information on the variables, the data, and any transformations or work that I performed to clean up the data 

- 'run_analysis.R': RScript that reads and tidies the data set. It then returns a table with the averages of each
mean/standard deviation variable for each activity and each subject. The data set can be found here: https://www.coursera.org/learn/data-cleaning/peer/FIZtT/getting-and-cleaning-data-course-project.

#run_analysis.R Step-by-Step

1. Load the test and train data with the features as the column names.
2. Load the subjects numbers.
3. Load the activity numbers that we will use to merge the test and train datasets.
4. Column bind the subject numbers to their respective data set.
5. Column bind the activity numbers to their respective data set.
6. Merge the 2 data sets.
7. Subset columns that calculate mean or standard deviation for each column. Also subset the activity and subject columns.
8. Substitute the activity numbers with descriptive activity names using mgsub() in dqap package.
9. Tidy up variable names by making column names lower case, removing full stops, removing the numbers at the beginning and replacing "t"/"f" with "time"/"freq".
10. Using the reshape2 package, melt the data set and then cast the melted data set to summarise the averages of each variable.
11. Write the tidy data set as a text file in the working directory.

Notes: 
======
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.

For more information about this dataset contact: activityrecognition@smartlab.ws

License:
========
Use of this dataset in publications must be acknowledged by referencing the following publication [1] 

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita. November 2012.
