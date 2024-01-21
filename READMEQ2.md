# ////////////////////////////Aurora a stellar oddesey\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

## Introduction
This project is a part of IIT Dh's Tech fest 'PARSEC'. This project is supposed to predict the solar radiation and goemagnetic storms in the near fututre if past data is given.<br>
We would aim only to provide the techincal details of the project in this README file and explain the scientific terms whenever necessary. If you want to know why we made certain assumptions,choices or if you want to have more details on the project please do check the project report. <br>
According to the problem statement of the project, raw and unprocessed data sets were given and Kp index was used to measure the disturbances in the Earth's magnetic field due to geomagnetic storms.<br>

## Import of necessary modules and files
### We would need the following modules:<br>
1)pandas-for reading and working data frames.<br>
2)numpy-for the math required in data visualization and training.<br>
3)scikit learn-(sklearn.preprocessing and MinMaxScaler)for using scalers and trainging our model.<br>
4)keras- for training a neural network.<br>
5)tensorflow-to support keras in the backend and other uses in model training.<br>
6)matplotlib-for plotting graphs and other mathematical objects.<br>
### We need the following datasets
1)files which have raw data of each year(<i>2015-2023</i>).<br>
2)files which contain the kp index of the corresponding years.<br>

## Data contained in the files
We have the a Datetime , Magnetic field in x,y,z directions and other 50 physically dimensionless columns in the given source files so we name the dimensionless columns which effect flux as "<i>SW_Flux</i>".<br>
A lot of data is missing and needs to be adjusted and replaced with a statistic figure. Data here is provided per mintue.<br>
In the Kp index file is provided on a 3 hourly basis.<br>

## Preprocessing 
This is the most crucial step of the project since the data we have been given is raw and we need to process it to turn it into meaningful features.<br>
->Startoff by replacing all the 0 by NaN values as descirbed in the problem statement.<br>
->Sort the datetime so that we get all the data in the dataframe sorted chronologically.<br>
->We convert all the data from all the files to numerical data.<br>
->For filling in the null values we can use different methods like imputation,interpolation,ffill etc, for such a large data frame we have chosen <i>ffill</i>.<br>
->Extract the kp index values from the given files by dropping all the oother unnecessary columns.<br>
->Resize and sample the shape of the data. Since the kp index is measured every 3 hours we need to adjust our raw feature data accordingly to train a model.<br>
->Concatenate all the files i.e all the feature dataset files from all years and the kp index files of the corresponding years to make a single large data set.<br>
->Use graphs,histograms and scatterplots to understand the target variable(<i>here kp index</i>) and its mathematical relations with the columns of the dataset.<br>
->Plot the graphs and use correlation as a medium to judge and select best columns and features. <br>
->Set a threshold to correlation(<i>for example top 12 features</i>) and scale the features accordingly.<br>
->Normalize the feautres using minmax scaler.<br>

## Splitting the data into training validation and test sets
Analyse the size of the data set and split it accordingly(<i>here 80 percent training, 10 percent validation, 10 percent testing</i>).<br>

## Selection and training of the model
We use a Recurrent neural network called LSTM(<i>Long Short term Memory</i>) model for training because the dataset we have a time variant and for such projects where the signal varies with time LSTMs are best suited.<br>
Analyse the size of features and training data and set the batchsizes,timesteps,epochs and verbose accordingly(<i> here epochs:64 batchsize:32 verbose:1 </i>).<br> 
Leave the model fr training and let it complete the training.<br>

## Results 
Analyse the loss function(<i>here mse:mean squared error</i>) and the how it decreases with the epochs and save the predictions made.<br>
Plot graphs of actual values and predictions and check how the model is performing.You can use scatterplots,confusion matrices and error analysis through statistical functions for checking results. <br>
As mentioned in the problem statement calculate the RMSE value (<i>for example its close to 1.0006289211972983 </i>).<br>

## Conclusion
Here we can conclude the project by saving the model and its training weights for future use. 

# Credits
## Team Leader- Dev Kaushal
## Aniruddh Pandav
## Kaustubh Arjun Jadhav
## Ajitesh Manan Jha
## Maitreyee Kumbhojkar
## Richa Rajshekhar
