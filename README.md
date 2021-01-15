# Description

This software is an ETL pipeline that extracts aircraft registry data from disparate remote sources, transforms the extracted data into a standardized format, and loads the transformed data into tabular stores used to seed or update components of a data warehouse.

### Official Sources

Official sources are generally federal government websites where a civilian aviation department makes available a registry cataloging all of the aircraft registered in that particular country. Because each government body manages their aircraft registry differently than the next, each official source requires a tailored approach to properly transform the data.

Under the registries directory there are sub-directories labeled with an ISO 3166-1 alpha-3 code for each country whose federal government hosts a public aircraft registry. Within each registries sub-directory there are two documents.

The first document is a README.md file that details which data features are captured from the remote registry ("Source Attribute") and where they are mapped to in the standardized output ("Target Attribute"). The second document is a Python script implementing the extraction and transformation steps specifically tailored to that country's aircraft registry.

### Unofficial Sources

There are no unofficial sources of aircraft registry data used at this time.

# Setup

1. Install the necessary application dependencies via `apt install ghostscript python3-tk`
2. Install the necessary Python package dependencies listed in *requirements.txt* via `pip3 install -r requirements.txt`

*Note: software developed with Python 3.8.5 on Windows-10-10.0.18362 win32*

# Usage

* Trigger the data pipeline for updating aircraft registry data from all remote sources at once via `python update_all_registries.py`
    * to receive progress updates, pass `verbose` as an argument by running `python update_all_registries.py verbose`

<br/>

* Trigger the data pipeline for updating aircraft registry data from a specific remote source via `python update_single_registry.py x`, where "x" is the (*not case-sensitive*) registry-code for the remote source of interest
    * example: run `python update_single_registry.py USA` to update aircraft registry data for the United States of America
    * to receive progress updates, pass `verbose` as an argument by running `python update_single_registry.py x verbose`

<br/>

* Access the aircraft registry data output from the *data* directory
