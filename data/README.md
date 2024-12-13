# Data Folders

These contain the data and data outputs after modeling. Note files in the RAW folder should not be modified once acquired.

This folder is organiszed based on the Data Pipeline described in [Hitchhikers Guide to Data Science - Data pipeline](https://github.com/dssg/hitchhikers-guide/blob/master/sources/curriculum/0_before_you_start/pipelines-and-project-workflow/README.md#data-pipelines) section as transcribed below

## Data pipelines

It is helpful to structure the data into multiple layers. In data bases, a layer is expressed as schema. In most other formats, they are expressed through a directory structure.

### Raw

The data we receive from the partners and external sources is the raw data. Raw data is immutable. Quoting from the popular workflow package Data Science Cookiecutter:

Don't ever edit your raw data, especially not manually, and especially not in Excel. Don't overwrite your raw data. Don't save multiple versions of the raw data. Treat the data (and its format) as immutable. The code you write should move the raw data through a pipeline to your final analysis. You shouldn't have to run all of the steps every time you want to make a new figure (see Analysis is a DAG), but anyone should be able to reproduce the final products with only the code in src and the data in data/raw.

### Intermediate

If the raw data is messy, it is advisable to create an intermediate layer that consists of tidy copies of the raw data. Typical situations where this is useful are:

Data is received in multiple different file types
Data fields are not typed (e.g. csv files, excel) or poorly typed (dates as strings, inconsistent date formats)
Column names are unclear, have spaces, special characters, or there are no column names
The transformations from raw to intermediate should be limited to fix the issues mentioned above. We should not combine different data sets or create calculated fields. This is reserved for the next layer.

Typical storage formats for the intermediate layer are a data base (e.g. postgres) or parquet files.

### Processed

To perform the modelling work, the input data needs to be combined and enriched, for example by creating features. The data sets that are created in this process are stored in the processed layer. Sometimes it can be useful to split this layer out into a domain data model, a feature layer and a master layer but the exact layering will depend on the project context.

### Models

The processed data is used to train predictive models, explanatory models, recommender engines and optimisation algorithms. The trained models are stored in the model layer. In contrast to the previous layers, models are usually stored in pickle because they are not in tabular format.

### Model output

Model performance metrics, model selection information and predictions are kept in the model output layer.

### Reporting

Reporting can be performed across the pipeline. For example, there might be data quality reports on the inputs, distribution analysis on the processed data, predictions, explanations, recommendations that are provided to the user, and performance evaluation and tracking. If a front-end is constructed, it will access the reporting layer to display information to the users and developers. For example, a Tableau dashboard, power BI, a jupyter notebook or an excel output will read from the reporting layer. Accordingly, the format of the data in the reporting layer will be adjusted to the front end of choice.
