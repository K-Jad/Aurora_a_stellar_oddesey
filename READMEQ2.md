# Aurora a stellar oddesey

## Introduction
This project is a part of IIT Dh's Tech fest 'PARSEC'. This project is supposed to predict the solar radiation and goemagnetic storms in the near fututre if past data is given.<br>
We would aim only to provide the techincal details of the project in this README file and explain the scientific terms whenever necessary. If you want to know why we made certain assumptions,choices or if you want to have more details on the project please do check the project report. <br>
According to the problem statement of the project, raw and unprocessed data sets were given and Kp index was used to measure the disturbances in the Earth's magnetic field due to geomagnetic storms.<br>

## Import of necessary modules and files
### We would need the following modules:<br>
1)pandas-for reading and working data frames<br>
2)numpy-for the math required in data visualization and training<br>
3)
### We need the following datasets
1)files which have raw data of each year<br>
2)files which contain the kp index of the corresponding years<br>

## Data contained in the files
We have the a Datetime , Magnetic field in x,y,z directions and other 50 physically dimensionless columns in the given source files so we name the dimensionless columns which effect flux as "SW_Flux".<br>
A lot of data is missing and needs to be adjusted and replaced with a statistic figure. Data here is provided per mintue.<br>
In the Kp index file too we have a lot of missing data and it is provided on a 3 hourly basis.<br>

## Preprocessing 
This is the most crucial step of the project since the data we have been given is raw and we need to process it to turn it into meaningful features.<br>
->Startoff by replacing all the 0 by NaN values as descirbed in the problem statement.<br>
->Sort the datetime so that we get all the data in the dataframe sorted chronologically<br>
->We convert all the data from all the files to numerical data.<br>
->For filling in the null values we can use different methods like imputation,interpolation,ffill etc, for such a large data frame we have chosen ffill.<br>
->Extract the kp index values from the given files by dropping all the oother unnecessary columns.<br>
->Resize and sample the shape of the data. Since the kp index is measured every 3 hours we need to adjust our raw feature data accordingly to train a model.
