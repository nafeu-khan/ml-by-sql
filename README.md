# DL4ML
Machine Learning Using Declarative Language



## Run the application
for frontend:
```
    cd client
    npm install
    npm  run dev
```
for backend: 
```
    cd server 
    pip install -r requirements.txt
    python manage.py runserver
```
for database setup:
```
    1. install postgresql and login
    2. give postgresql credential to python root file .env as like 
       DATABASE_URL = postgresql://myuser:mypassword@localhost:5432/mydatabase
    3. keep running database connection

## Example query
    ##construct 
    ```
        CONSTRUCT KMeans_Boston AS UNSUPERVISED FOR CLUSTERING  FEATURES age,rad ALGORITHM KMeans WITH CLASS 5 FROM Boston;

        CONSTRUCT LR_Boston AS SUPERVISED FOR PREDICTION on TARGET medv FEATURES age,rad ALGORITHM LR  TEST ON .3 FROM Boston; 

        CONSTRUCT KNN_Combined AS SUPERVISED FOR CLASSIFICATION on TARGET Class FEATURES CAtomCount,TotalAtomCount,HAtomCount ALGORITHM KNN  TEST ON .3 FROM combined;

        CONSTRUCT LR_Combined AS SUPERVISED FOR PREDICTION on TARGET Epsilon FEATURES CAtomCount,TotalAtomCount,HAtomCount ALGORITHM LR  TEST ON .3 FROM combined;

        CONSTRUCT LR_retail AS SUPERVISED FOR PREDICTION on TARGET MonthlySales FEATURES Age,Price,StockLevel ALGORITHM LR  TEST ON .3 FROM retail;
```
    ##Generate
    #cluster
    ```
        GENERATE DISPLAY OF CLUSTERING ALGORITHM KMeans FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;
        GENERATE DISPLAY OF CLUSTERING WITH CLUSTER OF 3 ALGORITHM KMeans FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;

        GENERATE DISPLAY OF CLUSTERING WITH CLUSTER OF 3 USING MODEL KMeans_Boston FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;
```
        #classificaarion
        ```
        GENERATE  CLASSIFICATION Class ALGORITHM KNN WITH ACCURACY 0 LABEL ProductID FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;
        GENERATE  DISPLAY OF CLASSIFICATION Class ALGORITHM KNN WITH ACCURACY 0 LABEL ProductID FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;

        GENERATE  CLASSIFICATION Class USING MODEL KNN_Combined WITH ACCURACY 0 LABEL ProductID FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;

```

        #prediction
        ```
        GENERATE DISPLAY OF PREDICTION Epsilon ALGORITHM LR WITH R-SQUARED 0 LABEL serialNo FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;
        GENERATE DISPLAY OF PREDICTION Epsilon USING MODEL LR_Combined  WITH R-SQUARED 0 LABEL serialNo FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;

        GENERATE DISPLAY OF PREDICTION MonthlySales ALGORITHM LR WITH R-SQUARED 0 LABEL serialNo FEATURES Age,Price,StockLevel FROM retail OVER retailTestData ;
        GENERATE DISPLAY OF PREDICTION MonthlySales USING MODEL  LR_retail WITH R-SQUARED  -10 LABEL serialNo FEATURES Age,Price,StockLevel FROM retail OVER retailTestData ; 

        GENERATE DISPLAY OF PREDICTION medv ALGORITHM LR WITH ACCURACY 0 LABEL serialNo FEATURES age,rad FROM  Boston ;
        GENERATE DISPLAY OF PREDICTION medv USING MODEL LR_Boston WITH R-SQUARED 0 LABEL serialNo FEATURES age,rad FROM  Boston ;

```
        #auto ml
        ```
        GENERATE DISPLAY OF PREDICTION medv  LABEL serialNo FEATURES age,rad FROM  Boston ;

        CONSTRUCT LR_retail AS SUPERVISED FOR PREDICTION on TARGET MonthlySales FEATURES Age,Price,StockLevel TEST ON .3 FROM retail;

        GENERATE  CLASSIFICATION Class  WITH ACCURACY 0 LABEL ProductID FEATURES CAtomCount,TotalAtomCount,HAtomCount FROM combined ;
```

        ## Inspect 

        #CHECKNULL
```
        INSPECT medv CHECKNULL  FROM Boston;
        ```
        #ENCODING
        ```

        INSPECT Species ENCODING METHOD Ordinal FROM Iris;
        INSPECT Species ENCODING METHOD One-Hot FROM Iris;
        INSPECT Species ENCODING METHOD Label   FROM Iris;
        INSPECT Species  ENCODING METHOD TARGET TARGET-FEATURE SepalLengthCm FROM Iris;
```
        #DEDUPLICATE
        ```
        INSPECT * DEDUPLICATE FROM Boston;
        INSPECT medv DEDUPLICATE FROM Boston;
```
        #CATEGORIZE
        ```
        INSPECT age CATEGORIZE INTO L1,L2,L3,L4 FROM Boston;

```
        #IMPUTE
        ```
        IMPUTE *  FROM USING STRATEGY mean BostonMiss;
        IMPUTE indus FROM BostonMiss;
```
#SQL query 
``` 
        SELECT * FROM "Iris";
```



# Available ML tools:
```
        prediction_algorithms = {
            LinearRegression
            RandomForestRegressor
            SVR
            KNeighborsRegressor
            GradientBoostingRegressor
        }
        classification_algorithms = {
            LogisticRegression
            RandomForestClassifier
            SVC
            KNeighborsClassifier
            GradientBoostingClassifier
        }
        clustering_algorithms = {
            KMeans
            AgglomerativeClustering
            DBSCAN
        }
    &
    Best algorthm selection using AutoML
```


