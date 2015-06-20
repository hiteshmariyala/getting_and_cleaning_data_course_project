Course Project Code Book
==================================================================

The dataset includes the following files:
=========================================

- 'features_info.txt': Shows information about the variables used on the feature vector.

- 'features.txt': List of all features.

- 'activity_labels.txt': Links the class labels with their activity name.

- 'train/X_train.txt': Training set.

- 'train/y_train.txt': Training labels.

- 'test/X_test.txt': Test set.

- 'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent. 

- 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 

- 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 

- 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration. 

- 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

Notes: 
======
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.

===========================================================================================
The script run_analysis.R performs the 5 steps described in the course project's definition.
    - First, the training and test data is merged using the rbind() function.
    - Then, only those columns with the mean and standard deviation measures are taken from the whole dataset. After extracting these columns, they are given proper names which are taken from features.txt
    - We take the activity names and IDs from activity_labels.txt and they are substituted in the dataset.
    - The columns with vague column names are corrected.
    - Finally, we generate a new tidy dataset with all the average measures for each subject and activity type (30 subjects * 6 activities = 180 rows). 
    - The output file is names as averages_data.txt.

Variables

    - x_train, y_train, x_test, y_test, subject_train and subject_test contain the data from the downloaded files.
    - x_data, y_data and subject_data merge the previous datasets to further analysis.
    - features contains the correct names for the x_data dataset, which are applied to the column names stored in mean_and_std_features, a numeric vector used to extract the desired data.
    - A similar approach is taken with activity names through the activities variable.
    - all_data merges x_data, y_data and subject_data in a big dataset.
    - Finally, averages_data contains the relevant averages which will be later stored in a .txt file. ddply() from the plyr package is used to apply colMeans() and ease the development.

