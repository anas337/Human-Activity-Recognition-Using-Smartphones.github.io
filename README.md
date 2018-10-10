[//]: # (Image References)

[image1]: ./images/sample_dog_output.png "Sample Output"
[image2]: ./images/vgg16_model.png "VGG-16 Model Keras Layers"
[image3]: ./images/vgg16_model_draw.png "VGG16 Model Figure"

# Human Activity Recognition Using Smartphones:

# Introduction:

Since 1870 a large growth in human life expectancy has been observed in Europe. This growth has expanded in the whole world principally due to the great achievements in health care field. As a result, the proportion of elderly people is rapidly increasing. Aging people in general lives in isolated
conditions. In addition to that some of them are not capable to live normally and take advantages from health care facilities services. Building remote monitoring systems for elderly patients who live alone or without permanent caretaking will improve their quality of life. For better decision making these remote monitoring systems needs some regular and trustful information about patients.

The goal of this project is to build a machine learning model and a signal processing pipeline capable of processing signals collected using smart phone inertial sensors (accelerometer and gyroscope) and producing useful datasets will be used as inputs of a machine learning model capable of recognizing some of human daily activities (sitting, walking …) included in the dataset (see datasets and Inputs section) with a low error rate. The signal processing pipeline and the final model could be used as a good source of information about patient’s daily activities needed by remote monitoring systems mentioned earlier.

# Project Origins:

To fulfil remote monitoring systems’ requirements [Jorge Luis Reyes Ortiz](https://www.icephd.org/wiki/index.php/Jorge_Luis_Reyes_Ortiz) has developed a complete [Human Activity Recognition System](https://en.wikipedia.org/wiki/Activity_recognition) able to detect and recognize 12 different activities performed by humans in their daily living using smartphones. The recognition part of his system is based on an  [SVM model](https://en.wikipedia.org/wiki/Support_vector_machine) already trained, capable of predicting activities performed by users. Necessary datasets of users’ movements were collected from smartphone sensors ([accelerometer](https://en.wikipedia.org/wiki/Accelerometer) and [gyroscope](https://en.wikipedia.org/wiki/Gyroscope) ). The datasets will be processed and fed to the prediction model to recognize performed activities.

# Software Requirements:

This project requires **Python 3.5 ** and the following Python libraries installed:
- [Python 3.5](https://www.python.org/download/releases/3.0/) 
- [NumPy](http://www.numpy.org/)  , [SciPy](https://www.scipy.org/) , [Pandas](https://pandas.pydata.org/) , [matplotlib](http://matplotlib.org/)
- [Statsmodel](http://www.statsmodels.org/stable/index.html)  , [Spectrum](https://pypi.org/project/spectrum/) , [scikit-learn](http://scikit-learn.org/stable/)

We recommend to install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains some of the necessary libraries and software for this project make to install an anconda environment that includes python 3.x . 

You will also need to have software installed to run and execute an [iPython Notebook](http://ipython.org/notebook.html)

## Install:

# Project Architecture:

For this project, you can find the `Human Activity Recognition` repository containing the necessary project files on the [my github profile](https://github.com/anas337/). This repository includes three global directories and 7 files:


### Directories:
	- `\Description-Images\`:
	
	- `\Reports\`:
	
	- `.\Data\`: Under this Directory you will find all Datasets used in this project.
		
		
		- `.\Original Data\`: This directory includes the original Datasets  brought by Jorge Luis Reyes Ortiz
			
			- `.\UCI HAR Dataset\`: This Directory contains Datasets related to The first verion 1.0
			- `.\HAPT Dataset\`: This Directory The second version of his dataset.
		
		
		-`.\ New Data\`: Under this directory you will find the processed datasets generated using 
		                 `Part_I--Signal-Processing-Pipeline.ipynb`. 
		
### Code Files:

	- `Part_I--Signal-Processing-Pipeline.ipynb`:
	- `Part_II--Machine-Learning-Part.ipynb`:
	

	- `UCI_HAR_Dataset_V1.ipynb`:
	- `UCI_HAR_Dataset_V1_Inertial_Signals.ipynb`:
	

	- `HAPT_RawData_statistics_V2.ipynb`
	- `HAPT_ML_V2.ipynb`
	
- `README.md` : It contains a short description of this project and necessary steps to run it successfully.


# Dataset and Inputs:

## Original Datasets:

### 1-The experiment:

The experiments were carried out with a group of 30 volunteers within an age bracket of 19-48 years. They performed a protocol of activities composed of six basic activities: three static postures (standing, sitting, lying) and three dynamic activities (walking, walking downstairs and walking upstairs). The experiment also included postural transitions that occurred between the static postures. These are: stand-to-sit, sit-to-stand, sit-to-lie, lie-to-sit, stand-to-lie, and lie-to-stand. 

![image1]

All the participants were wearing a smartphone (Samsung Galaxy S II) on the waist during the experiment execution. They captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz using the embedded accelerometer and gyroscope of the device. The experiments were video-recorded to label the data manually. The resulted dataset stored in the directory `Raw-Data` could be considered as the original labeled data and from it different subsets will be generated.

![image2]


This `Raw-Data` was randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

### 2- The Reduced Data or [UCI Human Activity Recognition Using smartphones Dataset Version 1.0](https://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones):

From the `Raw-Data` presented in the picture above, they extract data points and activity labels related only to The first six basic activities which are : standing, sitting, lying, walking, walking downstairs and walking upstairs.

#### 2-1. Signal Processing:
The sensor signals (accelerometer and gyroscope) for the training and testing sets of this reduced data were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. These signals were stored in the directory `Inertial Signals`. 

#### 2-2. Data processing and Features Generation:
From each group of windows (lines) having the same line number in all 9 log files, a vector of 561 features (See `features_info.txt` for more details) was obtained by calculating variables from the time and frequency domain. These features were stored in the directory `processed data` which contains train and test files.

#### 2-3. Data Architecture:
This first version located in `/Original-Data/UCI HAR Dataset(V1)/` can be divided into two parts (Two Directories) and they can be used separately.  

##### A. Inertial Signals: Data located in the directory `./Inertial Signals/`:

- `./train/`: 

		- `total_acc_x_train.txt`: The acceleration signal from the smartphone accelerometer X axis in 
					   standard gravity units 'g'. Every row shows a 128 element vector. 
					     The same description applies for the 'total_acc_x_train.txt' and 
					     'total_acc_z_train.txt' files for the Y and Z axis. 

		- `body_acc_x_train.txt`: The body acceleration signal obtained by subtracting the gravity from 
					  the total acceleration.

		- `body_gyro_acc_x_train.txt`:The angular velocity vector measured by the gyroscope for each window 
					      sample. The units are radians/second. 

- `./test/*`: This Directory includes the testing files similarly to the `./train/`.


##### B. The Processed Data verion 1.0:
This Directory contains records of the first six basic activities windows. Each one composed 561-feature vector with time and frequency domain variables. The dataset is located in the directory `./Processed Data V1/` it includes The following files:

	- `X_train.txt`: Train features
	- `X_test.txt`:  Test features
##### C. Other files:

		- `y_train.txt`: train activity labels
		- `y_test.txt`: test activity labels
		- `subject_train.txt`: An identifier of the subject who carried out the experiment
		- `subject_test.txt`:An identifier of the subject who carried out the experiment
		- `features_info.txt`:Shows information about the variables used on the feature vector.
		- `features.txt`:

 





# [Smartphone-Based Recognition of Human Activities and Postural Transitions Data Set Version 2.0]()

This dataset is an extended version of the [UCI Human Activity Recognition Using smartphones Dataset](https://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) mentioned earlier.
This version provides the original signals captured from the smartphone sensors mentioned earlier `Raw-Data`, instead of the ones pre-processed into windows  `Inertial signals` which were provided in version 1. This change was done in order to be able to make online tests with the data. Moreover, the activity labels were updated in order to include postural transitions that were not part of the previous version of the dataset.

#### Signal and Data Processing:
The inertial signals of  `Raw-Data` were preprocessed approximatly the same way to produce preprocessed train and test files.
#### Data Architecture:
This second version can be divided in two parts and they can be used separately.  

##### 1. Inertial sensor data located in the directory `Raw-Data`: 
 
Raw triaxial signals from the accelerometer and gyroscope of all the trials with participants.

- 'RawData/acc_expXX_userYY.txt': The raw triaxial acceleration signal for the experiment number XX and associated to the user number YY. Every row is one acceleration sample (three axis) captured at a frequency of 50Hz. 

- 'RawData/gyro_expXX_userYY.txt': The raw triaxial angular speed signal for the experiment number XX and associated to the user number YY. Every row is one angular velocity sample (three axis) captured at a frequency of 50Hz. 

- The labels of all the performed activities.

- 'RawData/labels.txt': include labels of all the performed activities(1 per row). 
   Column 1: experiment number ID, 
   Column 2: user number ID, 
   Column 3: activity number ID 
   Column 4: Label start point (in number of signal log samples (recorded at 50Hz))
   Column 5: Label end point (in number of signal log samples)
  
##### 2. Records of activity windows. Each one composed of:
A 561-feature vector with time and frequency domain variables, Its associated activity label and An identifier of the subject who carried out the experiment.
	- X_train.txt
	- X_test.txt
	- y_train.txt
	- y_test.txt
