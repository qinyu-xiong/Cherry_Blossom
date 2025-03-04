# Cherry_Blossom
request_station_id.ipynb and request_weather.ipynb to get the original data from NOAA. data_cleaning_preprocessing.ipynb is used to do data cleaning. This would get the csv file "qyx_final_data_1.csv".

Then, the CherryBlossomCode.ipynb is the code to create selected features, train the model, and make predictions.


Abstract: 
This study used time series–based LSTM classification model to predict cherry blossom date in 5 regions. I obtained daily weather data from NOAA, including key variables like daily maximum (TMAX), minimum (TMIN) temperatures, and average temperature (TAVG). Accumulated Growing Degree Days (GDD_cumsum) and daily GDD estimates (GDD) were calculated to capture accumulated heat units above a specified threshold. Additional rolling features, such as a 7-day average temperature (TAVG_7d) and 7-day cumulative precipitation (PRCP_7d_cumsum), were included to reflect short-term climatic patterns. Winter extremes—Tmax_Winter and Tmin_Winter—were computed as location-year–specific metrics to represent the extreme conditions.

Then, I combined those features into a sliding window of 10 consecutive days, creating time series segments suitable for modeling. Data preprocessing steps included imputation of missing dates through reindexing and interpolation, thereby preserving the chronological integrity of the time series. All features were standardized to stabilize training and improve convergence. I calculated the date until cherry blossom for each timeseries, using it as the target variable for the model.

The chosen model architecture was a stacked Long Short-Term Memory (LSTM) neural network, designed to capture temporal dependencies. The LSTM layers were followed by fully connected layers to output a categorical probability distribution over all possible remaining days until bloom. The model was trained using a categorical cross-entropy loss function, with accuracy tracked during training and validation. 

Finally, the trained model was applied to prospective data from early 2025 to generate real-time bloom predictions. The resulting forecast indicated how many days remained until cherry blossom bloom, and by adding this value to the last day of available observations, a predicted calendar date was produced.
