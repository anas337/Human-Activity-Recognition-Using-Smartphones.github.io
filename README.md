# Human Activity Recognition Using Smartphones:

# I.  Introduction:

Since 1870 a large growth in human life expectancy has been observed in Europe. This growth has expanded in the whole world principally due to the great achievements in health care field. As a result, the proportion of elderly people is rapidly increasing. Aging people in general lives in isolated conditions. In addition to that some of them are not capable to live normally and take advantages from health care facilities services. Building remote monitoring systems for elderly patients who live alone or without permanent caretaking will improve their quality of life. For better decision making these remote monitoring systems needs some regular and trustful information about patients.

#### Project Origins:
To fulfil remote monitoring systems’ requirements [Jorge Luis Reyes Ortiz](https://www.icephd.org/wiki/index.php/Jorge_Luis_Reyes_Ortiz) has developed a complete [Human Activity Recognition System](https://en.wikipedia.org/wiki/Activity_recognition) able to detect and recognize 12 different activities performed by humans in their daily living in online mode using smartphones. The recognition part of his system is based on an [SVM model](https://en.wikipedia.org/wiki/Support_vector_machine) already trained, capable of predicting activities performed by users. Necessary datasets of users’ movements will be collected from smartphone sensors ([accelerometer](https://en.wikipedia.org/wiki/Accelerometer) and [gyroscope](https://en.wikipedia.org/wiki/Gyroscope)). The datasets will be processed and fed to the prediction model to recognize performed activities.

To build the final model embedded in this HAR system. An offline version of this system needs to be created for two reasons:
##### 1. To construct the signal processing pipeline and process the original data collected.
##### 2. To build the train-test pipelines and test different state of art ML alogrithms to choose the optimal one.


#### Project Overview:
The goal of this project is to build a machine learning model and a signal processing pipeline in offline mode capable of processing signals collected using smart phone inertial sensors (accelerometer and gyroscope) and producing useful datasets will be used as inputs of a machine learning model capable of recognizing some of human daily activities (sitting, walking …) included in the dataset (see datasets and Inputs section) with a low error rate. The signal processing pipeline and the final model could be used as a good source of information about patient’s daily activities needed by remote monitoring systems mentioned earlier

# II. Software Requirements:
This project requires **Python 3.5 ** and the following Python libraries installed:
- [Python 3.5](https://www.python.org/download/releases/3.0/) 
- [NumPy](http://www.numpy.org/)  , [SciPy](https://www.scipy.org/) , [Pandas](https://pandas.pydata.org/) , [matplotlib](http://matplotlib.org/)
- [Statsmodel](http://www.statsmodels.org/stable/index.html)  , [Spectrum](https://pypi.org/project/spectrum/) , [scikit-learn](http://scikit-learn.org/stable/)
#### Install:
We recommend to install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains some of the necessary libraries and software for this project make to install an Anaconda environment that includes python 3.x . 
You will also need to have software installed to run and execute an [iPython Notebook](http://ipython.org/notebook.html)

You could import the used environment via the YAML file.

# III. Project Architecture:

This repository includes three main directories and 7 files:

### III-1. Directories:

	- `\Description-Images\`: This folder includes images used for aesthetic purposes
	
	- `\Reports\`: Contains an HTML version of each notebook + 2 reports
	
	- `.\Data\`: Under this Directory you will find all Datasets used in this project.
		- `.\Original-Data\`: contains the original Datasets brought by Jorge Luis Reyes Ortiz.	
			- `. \UCI-HAR-Dataset\`:  The first version of this Dataset V 1.0
			- `. \HAPT-Dataset\`: The second version V 2.0
		
		
		-`.\ New Data\`: Under this directory you will find the processed datasets generated from the original 
		                 ones using: `Part_I--Signal-Processing-Pipeline.ipynb`. 
		
### III-2. Notebooks:

	- `Part_I--Signal-Processing-Pipeline.ipynb`: This is jupyter notebook file which contains the signal processing 
	                                              pipeline, visualizations and detailed analysis of each step 
						      performed in this part.	
	
	- `Part_II--Machine-Learning-Part.ipynb`:  This is jupyter notebook file which contains  python code related to 
	                                           machine learning, visualizations and detailed analysis of each step 
						   performed to build the final model.
	

	- `UCI_HAR_Dataset_V1.ipynb`:
	- `UCI_HAR_Dataset_V1_Inertial_Signals.ipynb`:
	

	- `HAPT_RawData_statistics_V2.ipynb`
	- `HAPT_ML_V2.ipynb`
	
	- `README.md` : It contains a short description of this project and necessary steps to 
	                run it successfully.


# IV. Dataset and Inputs:

## IV-1. Original Datasets:

### A. The Experiment:

The experiments were carried out with a group of 30 volunteers within an age bracket of 19-48 years. They performed a protocol of activities composed of six basic activities: three static postures (standing, sitting, lying) and three dynamic activities (walking, walking downstairs and walking upstairs). The experiment also included postural transitions that occurred between the static postures. These are: stand-to-sit, sit-to-stand, sit-to-lie, lie-to-sit, stand-to-lie, and lie-to-stand. 



All the participants were wearing a smartphone (Samsung Galaxy S II) on the waist during the experiment execution. They captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz using the embedded accelerometer and gyroscope of the device. The experiments were video-recorded to label the data manually. The resulted dataset stored in the directory `Raw-Data` could be considered as the original labeled data and from it different subsets will be generated.


### B. Data Splitting:

### C. Signal Processing:

##### Noise filtering:

##### Gravity filtering:

### D. Activity Selection:

### E. Data Processing:

### F. Windowing:
 
### G. Features Generation:  



