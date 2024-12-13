# Notebooks folder

These folders contain Jupyter Notebooks that are used to process data, generate figures, and perform analyses. The general workflow is to prototype and document code in a notebook, then create a function in the that can:
    - take import data
    - clean the data
    - explore the data
    - process the data
    - model the data
    - evaluate the models
    - report the results
    - generate figures

These functions are then tested in Jupyter notebooks to ensure they work as expected. The functions are then moved into the `src` folder to be used in the pipeline. And so they can be imported into other notebooks and used in a reproducible set of analyses that can be provided in a repository or a report.

Jupyter notebooks. Naming convention is date YYYYMMDD (for ordering), the creator's initials, and a short `-` delimited description, e.g. `20190601-jqp-initial-data-exploration`.
