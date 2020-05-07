# NYC - Taxi Duration Data Set
    I have a sample data set of Taxi Trip Duration in the NY City.
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
        
    The goal is to produce a regression model to predict the Trip duration.
    
    Methods used:
        Feature Engineering and EDA.
        Clustering: The co-ordinates were clustered in order to get relevant features.
        Model:
            Linear Regression, KNN, Decison Tree used as Base learnes.
            Stacked the base learner models with XGBoost as the final model.
        Accuracy Metric:
            RMSLE (Root Mean Squared Log Error)
            Also used RMSE on log of trip duration as it is the same
    
    RMSLE scores:
        Base Model: 0.57
        Final Model: 0.40
