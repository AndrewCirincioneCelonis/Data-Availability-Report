# Data Availability Report

## Overview

This notebook creates or updates a data availability report for tables and fields in a Celonis data model. It loops through model tables and columns, queries availability-related information, and stores progress in `table_report.csv` so the report can be resumed or extended.

## What it does

- Connects to a Celonis team, data pool, and data model.
- Iterates through tables and columns in the data model.
- Skips tables listed in `skip_list` as well as OCPM event tables
- Appends new table/field results to the report, including data types and 
- Saves results to `table_report.csv`.

## Requirements

- Celonis access and API key.
- A Celonis data pool and data model ID.

## Setup

Fill in the user input variables:

```python
team_url = ''
api_key = ''
key_type = 'USER_KEY'
data_pool_id = ''
data_model_id = ''
```

Optionally configure the skip list for tables you want to skip:

```python
skip_list = []
```

## Output

```text
table_report.csv
```

## Important notes

- Existing `table_report.csv` is used to avoid reprocessing table/field combinations already captured.
- The notebook excludes tables with `t_e_` in the table name based on the current logic.
