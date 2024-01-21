<html>
<body>
<head>
<h1><b><strong>//////////////Aurora a stellar oddesey\\\\\\\\\\\\\\</strong></b>

<h2>Introduction</h2>
<h3>
  This project is a part of IIT Dh's Tech fest 'PARSEC'. This project is supposed to predict the solar radiation and goemagnetic storms in the near fututre if past data is given.
We would aim only to provide the techincal details of the project [Quest_1] in this README file and explain the scientific terms whenever necessary. If you want to know why we made certain assumptions,choices or if you want to have more details on the project please do check the project report.
According to the problem statement of the project, raw and unprocessed data sets were given and Disturbance Storm Index Values(dst) was used to measure the disturbances in the Earth's magnetic field due to geomagnetic storms.

</h3>

<h2>Importing of necessary Modules and Files</h2><br>
<h3><strong>Modules needed: </strong></h3><br>
<h3>
1)pandas-for reading and working data frames.<br>
2)numpy-for the math required in data visualization and training.<br>
3)scikit learn-(sklearn.preprocessing and MinMaxScaler)for using scalers and trainging our model.<br>
4)keras- for training a neural network.<br>
5)tensorflow-to support keras in the backend and other uses in model training.<br>
6)matplotlib-for plotting graphs and other mathematical objects.<br>
</h3>
<h3>We need the following datasets: </h4><br>
<h3>
1.sunspots_smooth.csv - Smoothed sunspot counts<br>
2.positions_sat.csv - Coordinate positions for ACE and DSCOVR<br>
3.solar_wind.csv - Solar wind data collected from ACE and DSCOVR<br>
  satellites
4.labels(dst).csv - Dst values averaged across the four stations<br>
</h3>

<h2><strong>Preprocessing</strong></h2>
<h3>
This is the most crucial step of the project since the data we have been given is raw and we need to process it to turn it into meaningful features.<br>
->Starting off with the very basic step of 'Reading and Loading files' for data analysis.<br>
->After reading in each csv, convert the timedelta columns to an actual timedelta object using pd.to_timdelta.<br>
   Then,we adjusted the indices of each dataframe comprising of period and timedelta so as to merge the dataframes easily.<br>
->Analysing the data helps to preprocess the data more efficiently.<br>
   1. Period columns were grouped, their max-min values,mean and standard deviations observed.<br>
   2. used the describe() feature to check the statistical features of solar_wind data.<br>
->Null values were checked for each feature: It is good to regularly check the count of null values so that we choose are imputing method accordingly.<br>
   1. Though the propotion of null values in each feature varied, but overall a huge Null count was recieved.<br>
   2. For filling in the null values we can use different methods like imputation,interpolation,ffill etc, for such a large data frame we have chosen ffill.<br> 
</h3>
<h3><strong>Data Analysis through Visualisation</strong>
->A couple of parameters were visualised through line plot: <br>
  1. "bx_gse"<br>
  2. "bx_gsm"<br>
  3. "bt"<br>
  4. "density"<br>
  4. "speed"<br>
  5. "temperature"<br>
  -Here, the temperature data was analysed specially as it had a wide range of data value due to which we might have to use feautue scaling.<br>
  
->We infered the following from the line charts: <br>
  1. The features 'bx_gse' and bx_gsm are closely related due to the stark resemblance in their respective line plots.<br>
  2. The source column was dropped to find the correlation of other data.<br>

  <h3><strong>Correlation & Data Visualisation[Contd.]</strong></h3>
  <h3>
  -> A correlation matrix was plotted against all the features.<br>
     1. Speed and temp. were highly anti-correlated with correlation values ranging from [-0.6,-0.4].<br>
     2. On the other hand, other features showed their correlation ranging from [-0.2,0.4].<br>
  -> Then we plotted the graphs of datas which had the highest correlation with dst for better visualisation of data<br>


<h2><strong>Feature Scaling </strong></h2>
  <h3>
  -> Highly correlated features were shortlisted for festure scaling and next procedures...<br>
        1. "bt"<br>
        2. "temperature"<br>
        3. "bx_gse"<br>
        4. "by_gse"<br>
        5. "bz_gse"<br>
        6. "speed"<br>
        7. "density"<br>
        8. "sunspots numbers"<br>

-> Subsets of these data were made and monthly/daily data was made hourly so as to aggregate with other features<br>
    1.  Missing values when made hourly were filled using 'mean'.<br>
    2. 'smoothed_ssn' was imputed using forward fill.<br>
    3. 'solar_wind' was imputed through interpolation.<br>

-> Standard Scaler was used for Feature Scaling: to merged and fitted the solar_wind and sunspots data <br>

-> Modifying the shape of labels dst by data shifting as we want to predict dst of 1 hour ahead also by creating variables t0 and t1<br>(we are basically creating two columns t0 and t1 which will predict the dst values with 1 hour gap)<br>
   Hence we can do multi-step prediction by providing it both steps.<br>
    -List of column names for the labels joining the t0 and t1 columns with the dst dataframe <br>
    
<h2>Splitting the data into training validation and test sets</h2>
<h3>

-> The given data is large in size. So, the data is splitted in three different periods namely, train, test and validation<br>
   we have created a new dataframe interim which includes all the rows from the original dataframe "data" except for those whose index values matches with the index of the dataframe "test".

-> Data splits: 3 parts(width=0.75)--> "train_a", "train_b" and "train_c" were created from the existing preprocessed dataset so as to monitor the train, validation and test split counts over hourly timesteps.
    using plots.<br>
  </h3>

<h2><strong>Selection and training of the model</strong></h2>
<h3>
We use a Recurrent neural network called LSTM(Long Short term Memory) model for training because the dataset we have a time variant and for such projects where the signal varies with time LSTMs are best suited.<br>
Analyse the size of features and training data and set the batchsizes,timesteps,epochs and verbose accordingly( here epochs:16, batchsize:32, timesteps:32, verbose:1, neurons:512 ).<br>
Leave the model for training and let it complete the training.<br>
</h3>
<h2><strong>Results</strong></h2>
<h3>
Analyse the loss function(here mse:mean squared error) and the how it decreases with the epochs and save the predictions made.<br>
Plot graphs of actual values and predictions and check how the model is performing.You can use scatterplots,confusion matrices and error analysis through statistical functions for checking results.<br>
As mentioned in the problem statement calculate the RMSE value (for example its close to 1.0006289211972983 ).<br>
</h3>

<h2><strong>Conclusion</strong></h2>
<h3>
Here we can conclude the project by saving the model and its training weights for future use.
</h3>

<h2><strong>Credits</strong></h2>
<h3>
Team Leader- Dev Kaushal<br>
Aniruddh Pandav<br>
Kaustubh Arjun Jadhav<br>
Ajitesh Manan Jha<br>
Maitreyee Kumbhojkar<br>
Richa Rajshekhar<br>
</h3>
