# DL4ML
Machine Learning Using Declarative Language
# Dependency requirements: (will be packaged together in future)
1. Tensorflow 1.2+
2. Python 3.6
3. Python Ply package
4. sci-kit learn package
5. Pandas package
6. Dill package


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


## Choose Database
USE '**database_name**';

example: USE salarydb;

## Create Model
CREATE MODEL **model_name** MODEL_TYPE **model_type**;

example: CREATE MODEL knn_model MODEL_TYPE KNN;
## Predicting
PREDICT **target_variable** FOR **feature_1,feature2,....**" by **model_name** with **table_name_of_DB**;

example: PREDICT Species FOR SepalLengthCm by KNN_model with Iris;

## Pre-requisite:
- First choose the source database 
- Make sure the model is trained




# Available ML tools:
1. Linear Regresstion (LR)
2. K nearest neighbour (KNN)



