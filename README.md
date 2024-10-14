# Data 512 Homework 2
## Overview
This repository contains the contents of an analysis into the quality rating of wikepedia articles on politicians from countries across the globe. Specifically, we use an API to scrape articles from wikepedia, and then pass these articles to the ORES ML model called LiftWing, which gives the articles their ratings. After collecting the data, this analysis generates the following 6 tables:
- Table 1: Top 10 countries by coverage
- Table 2: Bottom 10 countries by coverage
- Table 3: Top 10 countries by high quality
- Table 4: Bottom 10 countries by high quality
- Table 5: Geographic regions by total coverage
- Table 6: Geographic region by high quality coverage

## Licenses and API Documentation
To generate the list of politicians by nationality ("politicians_by_country_AUG.csv"), the Wikipedia [Category:Politiciens](https://en.wikipedia.org/wiki/Category:Politicians_by_nationality) by nationality was crawled. The list of population by country ("population_by_country_AUG.2024.csv"), was downloaded from the [world population data sheet](https://www.prb.org/international/indicator/population/table/) published by the Population Reference Bureau.

To access the page info data, we use the [MediaWiki REST API for the EN Wikipedia](https://www.mediawiki.org/wiki/API:Main_page), with API documentation [here](https://www.mediawiki.org/wiki/API:Info).

To score the articles, we use the Wikimedia ML service infrastructure called [LiftWing](https://wikitech.wikimedia.org/wiki/Machine_Learning/LiftWing). Specifically, we use the LiftWing version of [ORES](https://www.mediawiki.org/wiki/ORES). here we additionally link to the [ORES API documentation](https://ores.wikimedia.org) and the [ORES LiftWing documentation](https://wikitech.wikimedia.org/wiki/Machine_Learning/LiftWing/Usage).


Lastly, this assignment, and significant portions of the "access_page_info.ipynb" and "ores_liftwing_scoring.ipnyb" files were developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - September 16, 2024

## Repository Structure
```markdown

├── data_clean/                                           # Folder containing the cleaned data
│   ├── rev_ids.json                                        # JSON with the revision ids for the latest wikipedia pages
│   ├── scores_dict.json                                    # JSON with the ORES LiftWing score associated with each article
│   ├── wp_countries-no_match.txt                           # txt file of all country names not present in BOTH the politician-country and population-country datasets
│   └── wp_politicians_by_country.csv                       # CSV with the final, cleaned and merged data of politician, article score, country, and population
├── data_raw/                                             # Folder containing the raw data
│   ├── politicians_by_country_AUG.2024.csv                 # CSV with the list of politicians and their corresponding countries
│   └── population_by_country_AUG.2024.csv                  # CSV with the list of countries and their populations
├── notebooks/                                            # Source code
│   ├── analysis.ipynb                                      # Notebook to perform the data analysis for generating the 6 tables
│   ├── data_acquisition.ipynb                              # Notebook to perform the API calls to get the revision ID's of the wikipedia articles
│   ├── data_processing.ipynb                               # Notebook to perform the data processing and merging of the scores datasets and population/politician countries
│   └── data_scoring.ipynb                                  # Notebook to perform the ORES LiftWing calls to score the accessed articles
├── LICENSE                                               # License documentation
└── README.md                                             # README for the repo
```

## Data Schema
### rev_ids.json
```json
{
    "type": "object",
    "properties":{
        "politician_name": {
            "type": "array",
            "description": "Name of politician",
            "items":{
                "revision_id": {
                    "type": "int",
                    "description": "Revision ID of wikipedia page"}
            }
        }
    }
}
```

### scores_dict.json

```json
{
    "type": "object",
    "properties":{
        "politician_name": {
            "type": "array",
            "description": "Name of politician",
            "items":{
                "revision_id": {
                    "type": "int",
                    "description": "Revision ID of wikipedia page"
                    },
                "quality_score": {
                    "type": "string",
                    "description": "LiftWing given quality score for the article"
                    }
            }
        }
    }
}
```

### wp_countries-no_match.txt
```markdown

| Column Name | Data Type | Data Description                                 
| ------------------------------------------
| 'Country'   | 'string'  | The name of the country  

```

### wp_politicians_by_country.csv
```markdown

| Column Name       | Data Type | Data Description                                 
| ------------------------------------------
| 'revision_id'     | 'int'     | The revision ID of the wikipedia article
| 'article_quality' | 'string'  | The ORES LiftWing quality rating
| 'article_title'   | 'string'  | The title of the article (the politician's name)  
| 'country'         | 'string'  | The country of the politician  
| 'population'      | 'float'   | The population of the country 
| 'region'          | 'string'  | The region associated with the country
```

## Additional Notes


## Research Implications
### Learning Reflections

### Q1:

### Q2:

### Q3:

