# Data Availability Report

## Overview

This notebook creates or updates a data availability report for tables and fields in a Celonis data model. It loops through model tables and columns, queries availability-related information, and stores progress in `table_report.csv` so the report can be resumed or extended.

## What it does

- Connects to a Celonis team, data pool, and data model.
- Loads an existing `table_report.csv` if one exists.
- Creates a new report if no prior CSV is found.
- Iterates through tables and columns in the data model.
- Skips tables listed in `skip_list`.
- Skips event-style tables whose names contain `t_e_`.
- Appends new table/field results to the report.
- Saves results to `table_report.csv`.

## Requirements

- Python/Jupyter Notebook environment.
- Celonis access and API key.
- A Celonis data pool and data model ID.
- Python packages:
  - `pycelonis`
  - `pandas`
  - `tqdm`

## Setup

Fill in the user input variables:

```python
team_url = ''
api_key = ''
key_type = 'USER_KEY'
data_pool_id = ''
data_model_id = ''
```

Optionally configure the skip list:

```python
skip_list = []
```

## Usage

1. Fill in the Celonis connection variables.
2. Add any table names to `skip_list` if they should be excluded.
3. Run the notebook cells in order.
4. Review `table_report.csv`.
5. If the run is interrupted, rerun the notebook; it will attempt to continue from the existing CSV.

## Output

```text
table_report.csv
```

## Important notes

- Existing `table_report.csv` is used to avoid reprocessing table/field combinations already captured.
- The notebook excludes tables with `t_e_` in the table name based on the current logic.
- Do not commit real API keys to source control.
