# Data 512 Homework 2
## Overview
This repository contains the contents of an analysis....

## Licenses and API Documentation


## Repository Structure
```markdown

├── data_clean/                                           # Folder containing the cleaned data
│   ├── rare-disease_monthly_combined_201507_202409.json  # JSON with the page view counts for both access types (mobile and desktop)
│   ├── rare-disease_monthly_desktop_201507_202409.json   # JSON with the page view counts for mobile
│   └── rare-disease_monthly_mobile_201507_202409.json    # JSON with the page view counts for desktop
├── data_raw/                                             # Folder containing the raw data
│   └── rare-disease_cleaned.AUG.2024.csv                 # CSV with the article names
├── results/                                              # Folder containing the generated figures
│   ├── figure1.png                                       # PNG with the Maximum Average and Minimum Average figure
│   ├── figure2.png                                       # PNG with the Top 10 Peak Page Views figure
│   └── figure3.png                                       # PNG with the Fewest Months of Data figure
├── notebooks/                                            # Source code
│   ├── analysis.ipynb                                    # Notebook to perform the data processing and graphing of the three figures
│   └── data_acquisition.ipynb                            # Notebook to perform the API calls and generate the cleaned data for the different access types
├── LICENSE                                               # License documentation
└── README.md                                             # README for the repo
```

## Data Schema
The output json files generated and stored in the "data_clean" folder have the following schema:

```json
{
    "type": "object",
    "properties":{
        "article": {
            "type": "array",
            "items":{
                "project": {
                    "type": "string",
                    "description": "Project Name (e.g. en.wikipedia)"
                },
                "article": {
                    "type": "string",
                    "description": "Article Name"
                },
                "granularity": {
                    "type": "string",
                    "description": "Range of API Call (e.g. monthly)"
                },
                "timestamp": {
                    "type": "string",
                    "description": "Year and month"
                },
                "agent": {
                    "type": "string",
                    "description": "Type of agent (e.g. user)"
                },
                "views": {
                    "type": "int",
                    "description": "Number of page views for the given timestamp and article"
                },                
            }

        }
    }
}

```
## Additional Notes

