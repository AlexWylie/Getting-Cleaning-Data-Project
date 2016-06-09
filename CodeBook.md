#Introduction

This code book describes the variables, the data, and any transformations or work that were performed
to clean up the data.

#Merging the 2 Data Sets

The initial data was provided in 2 data sets:

1. Test data
2. Train data

The 2 data sets were column-binded using the subject numbers and activities to each data set and then merged together.

#Variables

The features selected for the initial database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

- tBodyAcc-XYZ
- tGravityAcc-XYZ
- tBodyAccJerk-XYZ
- tBodyGyro-XYZ
- tBodyGyroJerk-XYZ
- tBodyAccMag
- tGravityAccMag
- tBodyAccJerkMag
- tBodyGyroMag
- tBodyGyroJerkMag
- fBodyAcc-XYZ
- fBodyAccJerk-XYZ
- fBodyGyro-XYZ
- fBodyAccMag
- fBodyAccJerkMag
- fBodyGyroMag
- fBodyGyroJerkMag

#Variable Transformations

The variables were 'tidied up' by:

1. Making the variable names lower case to help support future debugging.
2. Removing full stops.
3. Removing the number that preceded each variable name.
4. Substituting 't' with 'time' and 'f' with 'freq'

e.g. 'tBodyAcc-XYZ' was transformed into 'timebodyaccxyz'

#Activity Transformations

The activity column which was column-binded previously contained the numbers 1:6. They were subsituted to
match their respective activity labels using the 'qdap' package and the mgsub() function

- 1 = walking
- 2 = walkingUpstairs
- 3 = walkingDownstairs
- 4 = sitting
- 5 = standing
- 6 = laying

#Data Transformations

In the initial data set, the following calculations were made on each variable:

- mean(): Mean value
- std(): Standard deviation
- mad(): Median absolute deviation 
- max(): Largest value in array
- min(): Smallest value in array
- sma(): Signal magnitude area
- energy(): Energy measure. Sum of the squares divided by the number of values. 
- iqr(): Interquartile range 
- entropy(): Signal entropy
- arCoeff(): Autorregresion coefficients with Burg order equal to 4
- correlation(): correlation coefficient between two signals
- maxInds(): index of the frequency component with largest magnitude
- meanFreq(): Weighted average of the frequency components to obtain a mean frequency
- skewness(): skewness of the frequency domain signal 
- kurtosis(): kurtosis of the frequency domain signal 
- bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
- angle(): Angle between to vectors.

run_analysis.R subsetted only the mean() and the std() of the variables.

#Melting & Casting

The data set was melted and casted (using the 'reshape2' package) to produce a data table that showed the mean of 
each variable for each activity and each subject:

mergedDataMelt <- melt(mergedData, (id = c("subject", "activity")))
tidyData <- dcast(mergedDataMelt, subject + activity ~ variable, mean)

#Further Information

A step-by-step guide of the script has been provided in the RScipt, run_analysis.R.
