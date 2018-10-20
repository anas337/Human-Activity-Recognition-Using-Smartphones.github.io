[//]: # (Image References)
[image1]: ./Description-Images/online-har-system-1.bmp "image1"
[image2]: ./Description-Images/Raw-Data.bmp "image2"
[image3]: ./Description-Images/raw-data-files.bmp "image3"
[image4]: ./Description-Images/exp01_user01-signals.PNG "image4"
[image5]: ./Description-Images/activity01.PNG "image5"
[image6]: ./Description-Images/Standing.PNG "image6"
[image7]: ./Description-Images/sitting.PNG "image7"
[image8]: ./Description-Images/Lying.PNG "image8"
[image9]: ./Description-Images/med-filtered.PNG "image9"
[image10]: ./Description-Images/original-signal-processing.bmp "image10"
[image11]: ./Description-Images/rows-per-exp.PNG "image11"
[image12]: ./Description-Images/rows-per-activity.PNG "image12"
[image13]: ./Description-Images/useful-rows-per-exp.PNG "image13"
[image14]: ./Description-Images/mean-time-per-activity.PNG "image14"

____________________________________________________
# Human Activity Recognition Using Smartphones:

# I.  Introduction:

Since 1870 a large growth in human life expectancy has been observed in Europe. This growth has expanded in the whole world principally due to the great achievements in health care field. As a result, the proportion of elderly people is rapidly increasing. Aging people in general lives in isolated conditions. In addition to that some of them are not capable to live normally and take advantages from health care facilities services. Building remote monitoring systems for elderly patients who live alone or without permanent caretaking will improve their quality of life. For better decision making these remote monitoring systems needs some regular and trustful information about patients.

#### Project Origins:
To fulfil remote monitoring systems’ requirements [Jorge Luis Reyes Ortiz](https://www.icephd.org/wiki/index.php/Jorge_Luis_Reyes_Ortiz) has developed a complete [Human Activity Recognition System](https://en.wikipedia.org/wiki/Activity_recognition) able to detect and recognize 12 different activities performed by humans in their daily living in online mode using smartphones. The recognition part of his system is based on an [SVM model](https://en.wikipedia.org/wiki/Support_vector_machine) already trained, capable of predicting activities performed by users. Necessary datasets of users’ movements will be collected from smartphone sensors ([accelerometer](https://en.wikipedia.org/wiki/Accelerometer) and [gyroscope](https://en.wikipedia.org/wiki/Gyroscope)), processed and then fed to the prediction model to recognize performed activities.


![image1]


To build the final model embedded in this HAR system. An offline version of this system needs to be created for two reasons:
##### 1. To construct the `signal processing pipeline` and process the original data collected.
##### 2. To build the train-test pipelines and test different state of art ML alogrithms to choose the optimal one.


#### Project Overview:
The goal of this project is to build a `machine learning model` and a `signal processing pipeline` in offline mode capable of processing signals collected using smart phone inertial sensors and producing useful datasets will be used as inputs of a machine learning model capable of recognizing some of human daily activities (sitting, walking …) included in the dataset (see datasets and Inputs section) with a low error rate. The signal processing pipeline and the final model could be used as a good source of information about patient’s daily activities needed by remote monitoring systems mentioned earlier

# II. Software Requirements:
This project requires **Python 3.5** and the following Python libraries installed:
- [Python 3.5](https://www.python.org/download/releases/3.0/) 
- [NumPy](http://www.numpy.org/)  , [SciPy](https://www.scipy.org/) , [Pandas](https://pandas.pydata.org/) , [matplotlib](http://matplotlib.org/)
- [Statsmodel](http://www.statsmodels.org/stable/index.html)  , [Spectrum](https://pypi.org/project/spectrum/) , [scikit-learn](http://scikit-learn.org/stable/)

#### Install:
We recommend to install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains some of the necessary libraries and software for this project (Be sure to install an Anaconda environment that includes python 3.x). 
You will also need to have software installed to run and execute an [iPython Notebook](http://ipython.org/notebook.html)

Here is an YAML File that includes environement dependencies used in this project [requirements]() you shoud use it to generate the anaconda enviroment.

# III. Project Architecture:

This repository [Human-Activity-Recognition-Using-Smartphones](https://github.com/anas337/Human-Activity-Recognition-Using-Smartphones) includes three main directories and 3 files:

### III-1. Directories:

	- `\Description-Images\`: This folder includes images used for aesthetic purposes.
	
	- `\Reports\`: Contains an HTML version of each notebook + 2 reports
	
	- `.\Data\`: Under this Directory you will find all Datasets used in this project.
		- `.\Original-Data\`: contains the original Datasets brought by Jorge Luis Reyes Ortiz.	
			- `. \UCI-HAR-Dataset\`:  The first version of this Dataset V 1.0.
			- `. \HAPT-Dataset\`: The second version V 2.1.
		
		
		-`.\ New Data\`: Under this directory you will find the processed datasets generated from the original 
		                 ones using: `Part_I--Signal-Processing-Pipeline.ipynb`. 
		
### III-2. Notebooks:

	- `Part_I--Signal-Processing-Pipeline.ipynb`: This notebook file contains the signal processing 
	                                              pipeline, visualizations and detailed analysis of each step 
						      performed.	
	
	- `Part_II--Machine-Learning-Part.ipynb`:  This is the notebook file which  related to machine learning, 
	                                           visualizations and detailed analysis of each step performed 
						   to build the final model.                    
	
	
	- `README.md` : It contains a short description of this project and necessary steps to 
	                run it successfully.


# IV. Datasets and Inputs:
## IV-1. Original Datasets
### . The general process:

### A. The Experiment:
The experiments were carried out with a group of 30 volunteers within an age bracket of 19-48 years. They performed a protocol of activities composed of six basic activities: three static postures (`standing`, `sitting`, `lying`) and three dynamic activities (`walking`, `walking downstairs` and `walking upstairs`). The experiment also included postural transitions that occurred between the static postures. These are: `stand-to-sit`, `sit-to-stand`, `sit-to-lie`, `lie-to-sit`, `stand-to-lie`, and `lie-to-stand`. 
All the participants were wearing a smartphone (Samsung Galaxy S II) on the waist during the experiment execution. They captured `3-axial linear acceleration` and `3-axial angular velocity `at a constant rate of `50Hz` using the embedded accelerometer and gyroscope of the device. The experiments were video-recorded to label the data manually. The resulted dataset stored in the directory `Raw-Data` could be considered as the original labelled dataset and from it different subsets would be generated.


![image2]


|  User 01 inertial signals|
| :--------: |
| ![image4]  |


| Walking| Standing | 
| :--------:  |:------:	|
| ![image5]  	|  ![image6] |


| Sitting| Lying| 
| :--------:  |:------:	|
|  ![image7]  |![image8] |



### B. Data Splitting:
This `Raw-Data` was randomly partitioned into two sets, where `70%` of the volunteers was selected for generating the training data and `30%` for the test data.


![image10]


### C. Signal Processing:

**Noise filtering:**
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals `t_Acc-XYZ` and `t_Gyro-XYZ`. These time domain signals (**prefix 't' to denote time**) were captured at a constant rate of `50 Hz`. Then they were filtered using a median filter and a `3rd order low pass Butterworth filter` with a corner frequency of `20 Hz` to remove noise. 

**1- Median Filter:**  was applied to reduce background noise.


![image9]


**2- 3rd order Low pass Butterworth filter** with a cut-off, `frequency = 20hz` was applied to remove high frequency noise.

Resulted Signals are:  `total_acc_XYZ` and `Gyro_XYZ`.

##### Gravity filtering:
Similarly, the acceleration signal `total-acc-XYZ` was then separated into body and gravity acceleration signals `(tBodyAcc-XYZ and tGravityAcc-XYZ)` using another `low pass Butterworth filter` with a corner frequency of `0.3 Hz`. Since the gravitational force is assumed to have only low frequency components.


Resulted components are:  `total_acc-XYZ` ==> `tBody_acc-XYZ` + `tGravity_acc-XYZ`

### D. Activity Selection:
From the processed signals presented in the picture above, they extract data points and activity labels related only to the first six activities which are: `standing`, `sitting`, `lying`, `walking`, `walking downstairs` and `walking upstairs` called Basic Activites(BA) to build the first version of this dataset.
**The second version of this datasets includes all the `12 activities` : Basic Activities (BA) and Postural Transitions (PT).

### E. Feature Selection:
Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (`tBodyAccJerk-XYZ` and `tBodyGyroJerk-XYZ`). Also, the magnitude of these three-dimensional signals was calculated using the Euclidean norm (`tBodyAccMag`, `tGravityAccMag`, `tBodyAccJerkMag`, `tBodyGyroMag`, `tBodyGyroJerkMag`). 
Finally, a Fast Fourier Transform `(FFT)` was applied to some of these signals producing `fBodyAcc-XYZ`, `fBodyAccJerk-XYZ`, `fBodyGyro-XYZ`, `fBodyAccJerkMag`, `fBodyGyroMag`, `fBodyGyroJerkMag`.
**The `f` to indicate frequency domain signals.** 

### F. Windowing:
These Signals were then sampled in fixed-width sliding windows of `2.56` sec and `50%` overlap `(128 readings/window)`.

### G. Features Generation:
From each sampled window, a vector of 561 features was obtained by calculating variables from the time and frequency domain.

-------------------------------------------------------------------------------------------------
### [Human Activity Recognition Using Smartphones Dataset Version 1.0](https://archive.ics.uci.edu/ml/datasets/human+activity+recognition+using+smartphones#)
**Jorge L. Reyes-Ortiz(1,2), Davide Anguita(1), Alessandro Ghio(1), Luca Oneto(1) and Xavier Parra(2):**

**[1] -** `Smartlab - Non-Linear Complex Systems Laboratory DITEN - Università  degli Studi di Genova, Genoa (I-16145), Italy.` 

**[2] -** `CETpD - Technical Research Centre for Dependency Care and Autonomous Living Universitat Politècnica de Catalunya (BarcelonaTech). Vilanova i la Geltrú (08800), Spain.`

**@mail:** `activityrecognition@smartlab.ws`

This first version is located in `./Data/Original-Data/UCI-HAR-Dataset/`. As mentioned earlier this dataset concerns only **Basic Activities** performed by the users during the experiments. It includes two main directories and they can be used separately.

**Dataset Architecture:** 

Under The `UCI-HAR-Dataset` Directory we have:
 
 1. ` ./Inertial Signals/`: This directory includes the **Semi-processed features** of this version.


		- ` ./Inertial-Signals/train/`:  The train folder includes 11 files.

			- `total_acc_x_train.txt`: The acceleration signal from the smartphone accelerometer X axis 
			                           in standard gravity unit 'g'. Every row shows a 128-element vector.
						   The same description applies for the `total_acc_y_train.txt` and                    
						   `total_acc_z_train.txt` files for the Y and Z axis. 

			- `body_acc_x_train.txt`: The body acceleration signal obtained by subtracting the gravity 
			                           from the total acceleration. The same description applies for the
						   `body_acc_y_train.txt` and `body_acc_z_train.txt` files for the Y 
						   and Z axis.

			- `body_gyro_acc_x_train.txt`: The angular velocity vector measured by the gyroscope for each
			                               window sample. The units are radians/second. The same description 
						       applies for the `body_gyro_y_train.txt` and `body_gyro_z_train.txt`
						       files for the Y and Z axis. 


		- ` ./Inertial-Signals/test/*`: This folder includes necessary testing files of inertial signals 
		                                following the same analogy as in `./Inertial Signals/train/`.



2. `./Processed-Data/` : This directory includes the **fully processed features** which concerns the same six activities. 


		- `X_train.txt`: Train features, each line is composed 561-feature vector with time and 
		                 frequency domain variables.

		- `X_test.txt`: Test features, each line is composed 561-feature vector with time and 
		                frequency domain variables.
				
		- `features_info.txt`: Shows information about the variables used on the feature vector.

		- `features.txt`: includes list of all 561 features


- `y_train.txt`: train activity labels, Its range is from 1 to 6

- `y_test.txt`: test activity labels, Its range is from 1 to 6

- `subject_train.txt`: training subject identifiers, Its range is from 1 to 30

- `subject_test.txt`: testing subject identifiers, Its range is from 1 to 30

- `activity_labels.txt`:

- `README.md`:

**Licence:**

Use of this dataset in publications must be acknowledged by referencing the following publication [1]:  

[1]- `Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. A Public Domain Dataset for Human Activity Recognition Using Smartphones. 21th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013.` 


**Note:** This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

----------------------------------------------------------------------------------------------------------
### [Smartphone-Based Recognition of Human Activities and Postural Transitions Data Set Version 2.1]( https://archive.ics.uci.edu/ml/datasets/Smartphone-Based+Recognition+of+Human+Activities+and+Postural+Transitions)

**Jorge L. Reyes-Ortiz(1,2), Davide Anguita(1), Luca Oneto(1) and Xavier Parra(2)**

[1] - `Smartlab, DIBRIS - Università  degli Studi di Genova, Genoa (16145), Italy.` 

[2] - `CETpD - Universitat Politècnica de Catalunya. Vilanova i la Geltrú (08800), Spain.`

@mail: **`har@smartlab.ws`**

Website: **`www.smartlab.ws`**

This dataset is an extended version of the [UCI Human Activity Recognition Using smartphones Dataset V 1.0](https://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) mentioned earlier.
This version provides the original signals captured from the smartphone sensors mentioned earlier `Raw-Data`, instead of the ones semi-processed and sampled into windows located in `Inertial-signals` directory which were provided in version 1.0. This change was done in order to be able to make online tests with the data. Moreover, the activity labels were updated in order to include postural transitions that were not part of the previous version of the dataset. This Dataset includes two main directories and they can be used separately.

**Dataset Architecture:**

Under The `HAPT-Dataset` Directory we have: 

1. `./Raw-Data/`:  This the original data (unprocessed data) obtained directly from the set of experiments after activity labelling . It includes Raw triaxial signals from the accelerometer and gyroscope of all trials with participants. This Directory includes 123 files:
		
		- **61 acc files are**: `Raw-Data/acc_expXX_userYY.txt`: The raw triaxial acceleration signal
		                         for the experiment number XX and associated to the user number YY.
				         Every row is one acceleration sample (three axis)[X,Y,Z] captured 
				         at a frequency of 50Hz. 
		
		- **61 gyro files are**: `Raw-Data/gyro_expXX_userYY.txt`: The raw triaxial angular
		                          speed signal for the experiment number XX and associated to 
					  the user number YY. Every row is one angular velocity sample 
					  (three axis)[X,Y,Z] captured at a frequency of 50Hz. 
		
		- **One last file is** :`RawData/labels.txt`: includes labels of all the performed 
		                         activities (1 per row). 
			- Column 1: experiment number ID, 
			- Column 2: user number ID,
			- Column 3: activity number ID 
			- Column 4: Label start point (in number of signal log samples (recorded at 50Hz))
			- Column 5: Label end point (in number of signal log samples)



| Raw Data Samples| 
| :--------:  |
|![image3] |

| Number of rows per Experience|Number of rows per activity  | 
| :--------:  |:------:	|
| ![image11]  	|  ![image12] |

| Number of useful rows per Experience| Mean time in seconds per Activity | 
| :--------:  |:------:	|
| ![image13]  	|  ![image14] |



2. `./ Processed-Data/`: This Directory includes the **fully processed dataset** which concerns all The twelve activities performed by users in the experiment.
		
		- `X_train.txt` : Train features, each line is composed 561-feature vector with time and 
		                  frequency domain variables.
		
		- `X_test.txt` : Test features, each line is composed 561-feature vector with time and 
		                 frequency domain variables.
		
		- `y_train.txt`: train activity labels, its range is from 1 to 12
		
		- `y_test.txt`: test activity labels, its range is from 1 to 12
		
		- `subject_id_train.txt`: training subject identifiers, Its range is from 1 to 30
		
		- `subject_id_test.txt`: testing subject identifiers, Its range is from 1 to 30
		
		- `features_info.txt`: Shows information about the variables used on the feature vector.
		
		- `features.txt`: includes list of all 561 features

- `activity_labels.txt`:
- `README.md`:

**License:**

Use of this dataset in publications must be acknowledged by referencing the following publications **[1]**:

**[1]** - `Jorge-L. Reyes-Ortiz, Luca Oneto, Albert Samà, Xavier Parra, Davide Anguita. Transition-Aware Human Activity Recognition Using Smartphones. Neurocomputing. Springer 2015.`

**Note:** This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.


## IV-2. New Datasets:

The New Datasets are the results of applying my own signal processing pipeline to Raw-Data. This directory includes one main folder ` full_Datasets_type_I_and_II `:

**`Type I `:** to denote V 1.0 which includes Basic activities only.

**`Type II `:** to denote V 2.1 which includes Both Basic Activities and Postural Transitions.

- ` ./New-Data/full_Datasets_type_I_and_II/ `: includes Datasets produced by the signal processing pipeline using ` Raw-Data ` only. All parts are fully processed. Each line(observation) includes XXX features + the **subject_Id** and the **activity label** related the observation.
		
		- ` Dataset_I_part1.csv `: The first 5000 rows of Dataset type I 
		
		- ` Dataset_I_part2.csv `: The rest of rows of Dataset type I 
		
		- ` Dataset_II_part1.csv `: The first 6000 rows of Dataset type II
		
		- ` Dataset_II_part2.csv `: The rest of rows of Dataset type II 

	- `new features info.txt `: Includes info about features(columns) in both Datasets type I and type II
	
	- `new_features.txt `: the full list of features (column names) of Dataset type I and II

# V. Running the code:

In the Terminal or Command Prompt, navigate to the folder containing the project files which contains this `README.md` and then use the command `jupyter notebook file_name.ipynb` to open up a browser window or tab to work with your notebook. Alternatively, you can use the command `jupyter notebook` or `ipython notebook` and navigate to the notebook file in the browser window that opens.

If you want to generate RawData statistics and overwrite the new datasets type I and II you should run the `Part_I--Signal-Processing-Pipeline.ipynb`. 

If you want to generate new datasets type I and II statistics and its machine learning results you should run the second notebook `Part_II--Machine-Learning-Part.ipynb`.

**Notes:**
- Please before running any notebook pay attention to running durations first (durations were computed on a laptop core i5 8Gbs of RAM).

- The Data owners didn't provide the signal processing code. The signal processing pipeline was developed using only explanations provided in both original datasets (Version 1.O and 2.1). As a result The General Process mentioned earlier is a little bit different from the one coded in the signal processing pipeline.

- The windowing methods used in the signal processing pipeline differs depending on the type of the data generated. Reports included in this reporsitery provides detailed information about these differences.

Please If you have any ambiguity about any part of this project or just want to have more info about this subject don't hestitate to contact me at: `abdessamad.anass@gmail.com` 
