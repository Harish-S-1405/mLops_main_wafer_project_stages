### Step 1 : Create a folder in local system

Get inside a folder and clear the path and write CMD and execute it
I will open a command shell

```

code .

```

it will open a visual code 
Note :  Install Visual code before running

### Step 2: Use a Git bash to run a code

### Step 3: Creating Environment

```

Note : install python package in visual code

create conda -n proj_v1 python=3.7 -y
source activate base
conda activate proj_v1

```

### Step 4: cookiecutter datascience Template Install

```

pip install cookiecutter

```

### step 5: Starting a project

```
https://drivendata.github.io/cookiecutter-data-science/   ---For your reference

cookiecutter https://github.com/drivendata/cookiecutter-data-science

Is it okay to delete and re-download it? [yes]: yes

project_name [project_name]: 
repo_name [project_name]:semeiconductor_wafer_project 

author_name [Your name (or your organization/company/team)]: Semiconductor_project

description [A short description of the project.]: it semiconduc
tor wafer mlops project

Select open_source_license:
1 - MIT
2 - BSD-3-Clause
3 - No license file
Choose from 1, 2, 3 [1]: 1

s3_bucket [[OPTIONAL] your-bucket-for-syncing-data (do not include 's3://')]: press enter
aws_profile [default]: press enter

Select python_interpreter:
1 - python3
2 - python
Choose from 1, 2 [1]: 1


Ater this , whatever name ypu given as project name . it will create folder 

Get into that folder

cd semiconductor_wafer_project/

then start the visual code in this repo

code .

```
### step 6

```

wafer_proj
==============================

its a wafer project

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>

```

### step 7: dvc install

```
pip install dvc

```

### step 8: initializing dvc

```

pip install dvc==2.10.2
pip install --force-reinstall -v "fsspec==2022.11.0"
dvc init -f

```

### step 9:  Creating Development branch

```

git chechout -b dev

```

### step 10: add training and testing files


### step 11: push to dev branch


### Step 12 : install DVC for gdrive

```

pip install dvc_gdrive

```

### step 13 : add remote storage

```
dvc remote add -d storage gdrive://<DRIVE ID>

git add .dvc/config && git commit -m "Configure remote storage"

dvc push

```

### Step 14: create a new file in src

```
touch src/pipeline_01_data_preparation.py

```
### step 15 : Enter the code

```

import os
import argparse
import yaml
import logging






if __name__=='__main__':
    args=argparse.ArgumentParser()
    args.add_argument("--config",default="default")
    args.add_argument("--datasource",default=None)

    parsed_args=args.parse_args()
    print(parsed_args)
    print(parsed_args.config,parsed_args.datasource)

```

### Step 16 : creating a config folder 

```
mkdir config

touch config/params.yaml

```

### step 17 :  write the below code in params.yaml

```

base:
  project: Wafer-Quality-Project
  random_state: 42
  target_col: Output

data_source:
  batch_files: Training_Batch_Files


data_preparation:
  training_db: Training.db
  training_db_dir: Training_Database
  schema_training: config/schema_training.json
  good_validated_raw_dir: data/Training_Raw_files_validated/Good_raw
  bad_validated_raw_dir: data/Training_Raw_files_validated/Bad_raw
  TrainingArchiveBadData: data/TrainingArchiveBadData
  Training_FileFromDB: data/Training_FileFromDB
  master_csv: master.csv

pred_data_preparation:
  prediction_db: Prediction.db
  prediction_db_dir: Prediction_Database
  schema_prediction: config/schema_prediction.json
  good_validated_raw_dir: data/Prediction_Raw_files_validated/Good_raw
  bad_validated_raw_dir: data/Prediction_Raw_files_validated/Bad_raw
  PredictionArchiveBadData: data/PredictionArchiveBadData
  Prediction_FileFromDB: data/Prediction_FileFromDB
  master_csv: master.csv
  Prediction_Output_File: Prediction_Output_File/Predictions.csv


saved_models:
  model_dir: models

data_preprocessing:
  preprocessed_data_dir: data/preprocessed_data
  null_values_csv: null_values.csv

  preprocessed_data_dir_pred: data/preprocessed_data_pred


  KNNImputer: 
    n_neighbors: 3 
    weights: uniform
    missing_values: nan

  KMeansClustering:
    init: k-means++
    n_cluster_max: 11
    KneeLocator: 
      curve: convex
      direction: decreasing
    

artifacts_dir: 
  general: general
  mlflow: mlflow_artifacts


training:
  random_forest:
    cv: 5
    verbose: 3
    param_grid:
      n_estimators: 
        - 10
        - 50
        - 100
        - 130 
      criterion: 
        - gini
        - entropy
      max_depth: 
        - 2
        - 4
      max_features: 
        - auto
        - log2
  xg_boost:
    cv: 5
    verbose: 3
    param_grid:
      learning_rate: 
        - 0.5
        - 0.1
        - 0.01
        - 0.001
      max_depth: 
        - 3
        - 5
        - 10
        - 20
      n_estimators: 
        - 10
        - 50
        - 100
        - 200
 

```
