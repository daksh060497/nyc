# NYC - Taxi Duration Data Set
The goal is to devise a regression model to predict the Taxi Trip duration using historic NYC taxi trip data for a time frame of 7 months.

### Description:
Train Data Set Size: 1.5M
Test Data Set Size: 630K

The data set contains features like:
    'id' - A unique identifier for each trip (Irrelevent Feature, Hence dropped it)
    'vendor_id' - A code indicating the provider associated with the trip record (Irrelevent Feature, Hence dropped it)
    'pickup_datetime': Time and Date of pick up
    'dropoff_datetime': Time and Date of drop off(Not in Test Dataset, Hence dropped it)
    'passenger_count': No. of passengers for the trip
    'pickup_longitude','pickup_latitude': Pick up Co-ordinates
    'dropoff_longitude','dropoff_latitude': Drop off Co-ordinates
    'store_and_fwd_flag': Whether the trip record was held in vehicle memory before sending to the vendor because the vehicle did not have a connection to the server (Irrelevent Feature, Hence dropped it)
    'trip_duration': duration of the trip in seconds (Target Variable)
    
# Our Approach:
### Data Processing
We carried out the standard data pre-processing which includes:

    Checking for duplicates and missing values
    Removing outliers as per target variable since the proportion was negligible.
    Splitting the data into train, test and validation using stratified sampling to maintain the target proportion.

### Feature Engineering and EDA: 
    Extracted Date and Time related Features such as pickup_weekday, pickup_weekofyear, pickup_hour, pickup_week_hour
    Calucated distance between pickup and dropoff using location co-ordiantes and Haversine distance metrics since the Earth is sperical.
    Devised a simple linear regression using partial features to generate a new feature that can be used as input for our final model.
    Clustering: The co-ordinates were clustered into 100 groups identifying different areas of the city.
    Created holiday/seasonal flags to capture days with more/less traffic.

### EDA
    There is a 60% co-relation between distance and duration. The rest of the variation lies due to traffic which can be estimated by historic data of date-time varialbes and holiday flags.
    Using k-means clustering, we can see that the Manhatthan area has more clusters which suggests mojority of the taxi trips happening in this area.

### Machine Learning Algorithms:
    Approach: 
    
        Used Linear Regression, KNN, Decison Tree as Base learnes.
        Stacked the base learner models with XGBoost as the final model.
    
    Accuracy Metric:
    
        RMSLE (Root Mean Squared Log Error)
        Also used RMSE on log of trip duration as it is the same
    
### RMSLE scores:
    Base Model: 0.57
    Final Model: 0.40
    Kaggle: 0.40

### Kaggle Link for data set:
    https://www.kaggle.com/c/nyc-taxi-trip-duration
    
