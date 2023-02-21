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
