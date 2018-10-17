Feature Selection 
=================
-   '_[X,Y,Z]' is used to denote 3-axial signals in the X, Y and Z directions.

-   prefix 't_' to denote time domain

-   prefix 'f_' to denote frequency domain 

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals total_Acc_[X,Y,Z] and total_Gyro-[X,Y,Z]. 
These time domain signals  were captured at a constant rate of 50 Hz. 
Then they were filtered using a 3rd order median filter. 

The acceleration signal was then separated into body and gravity acceleration signals; (t_Body_Acc_[X,Y,Z] and t_Gravity_Acc_[X,Y,Z] ).

	Using Fast Fourrier transform and its inverse :I selected Signal components having frequencies between :

		1) [-0.3hz,0.3hz]  as gravity components

		2) [-20hz,-0.3hz[ U ]0.3hz,20hz] as body components

For angular velocity signals only body components were selected using the previous method to produce t_Body_Gyro_[X,Y,Z].


Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals:
		
		 (t_Body_Acc_Jerk_[X,Y,Z] and t_Body_Gyro_Jerk_[X,Y,Z]). 


Also the magnitude of all these three-dimensional signals were calculated using the Euclidean norm :

	t_Body_Acc_Mag, t_Gravity_Acc_Mag, t_Body_Acc_Jerk_Mag, t_Body_Gyro_Mag, t_Body_Gyro_Jerk_Mag : 5 time domain magnitude signals



Finally a Fast Fourier Transform (FFT) was applied to 16 time domain signals:


	t_Body_Acc_[X,Y,Z],t_Body_Acc_Jerk_[X,Y,Z],t_Body_Gyro_[X,Y,Z],t_Body_Gyro_Jerk_[X,Y,Z]: 12 time Axial signals
   
  	t_Body_Acc_Mag,    t_Body_Acc_Jerk_Mag,    t_Body_Gyro_Mag,    t_Body_Gyro_Jerk_Mag : 4 time magnitude signals

producing:


	f_Body_Acc_[X,Y,Z], f_Body_Acc_Jerk_[X,Y,Z], f_Body_Gyro_[X,Y,Z], f_Body_Gyro_Jerk[X,Y,Z],: 12 frequency Axial signals

  	f_Body_Acc_Mag,    f_Body_Acc_Jerk_Mag,      f_Body_Gyro_Mag,     f_Body_Gyro_Jerk_Mag :   4 frequency magnitude signals


These signals were used to estimate variables of the feature vector for each pattern:  


		t_Body_Acc_[X,Y,Z],t_Gravity_Acc[X,Y,Z],t_Body_Acc_Jerk_[X,Y,Z],t_Body_Gyro_[X,Y,Z],t_Body_Gyro_Jerk_[X,Y,Z]
		t_Body_Acc_Mag,	    t_Gravity_Acc_Mag,	  t_Body_Acc_Jerk_Mag,	t_Body_Gyro_Mag, t_Body_Gyro_Jerk_Mag

		===========================================================================================================
		
		f_Body_Acc_[X,Y,Z],    f_Body_Acc_Jerk_[X,Y,Z],	f_Body_Gyro_[X,Y,Z],   f_Body_Gyro_Jerk_[X,Y,Z]
		f_Body_Acc_Mag,		f_Body_Acc_Jerk_Mag   ,  f_Body_Gyro_Mag,	f_Body_Gyro_Jerk_Mag








The set of variables that were estimated from these signals are: 


Comon Features will applied to all signals:
==========================================
_mean(): Mean value
_std(): Standard deviation
_mad(): Median absolute deviation 
_max(): Largest value in array
_min(): Smallest value in array
_iqr(): Interquartile range 
_entropy(): Signal entropy
==========================================



These features has diffrent math formula depending on the signal's domain
they will be applied to all signals(36 signals)
=======================================================================
_sma(): Signal magnitude area
_energy(): Energy measure. Sum of the squares divided by the number of values. 
==============================================================================


This feature will be applied to All time domain signals(20signals)
=======================================================================
_AR1(),_AR2(),_AR3(),_AR4(): Autorregresion coefficients with Burg order equal to 4
===========================================================================



This feature will be applied to Axial time domain signals only (15 signals)
===================================================================
_corr(): correlation coefficient between two signals
======================================================================




These features will be applied to all frequency domain signals(16 signals)
==========================================================================
_maxInd(): index of the frequency component with largest magnitude
_meanFreq(): Weighted average of the frequency components to obtain a mean frequency
_skewness(): skewness of the frequency domain signal 
_kurtosis(): kurtosis of the frequency domain signal 
======================================================================================



This feature will be applied to Axial frequency domain signals (12 signals)
============================================================================================
_BE[m,n]: bandsEnergy of a frequency interval within the 64 bins of the FFT of each window. 

(n-m+1) data points per band
==============================================================================================



This feature will be applied to some time domain signals
========================================================
_angle(): Angle between to vectors.
=========================================================
The complete list of variables of each feature vector is available in 'new_features.txt'
