This presents an answer the second prompt: Which property types receive the most positive reviews. This was interpreted as "the highest count of positive reviews" at the time of presentation. A further analysis should compare this outcome to "the highest rated property types" irrespective of property count. 

Additionally, further analysis should include responses to the other three guided project prompts.

### Business Needs (per interpretation of scenario)


## How to use this repo

The original project files are located in the top level folder, all cleaned/working files are within this folder, to be used to run the analyses. 

Both Excel and RStudio were used, Excel primarily for initial data exploration; RStudio for data cleaning, feature engineering, data profiling.

### Initial EDA
Original data was loaded in Excel to gather initial data insights, including:
* Duplicate host_id associated with unique id (property ID) - multiple properties?
* City is not consistent, has Neighborhoods in city column
* Inconsistent naming scheme in state column
* Blanks noted in state column
* Additional insights provided in DataExplorer output, including data types, etc.

Data uploaded to data.world to run against R (using a SQL hook to import), DataExplorer package used to visualize data characteristics (as shown in [this initial EDA](final-project/edaReport_initialdata.html). An initial R code was provided to guide this:

```
{
  library(tidyverse)
  library(data.world)
  library(DataExplorer)
  library(Hmisc)
  sql_stmt <- qry_sql('
  select * from unit_1_project_dataset
  ')
  df <- data.world::query(sql_stmt, "ga-data-analytics/project-1-dataset")
  names(df)

  dplyr::filter(df, duplicated(df)) %>% View() # View duplicate rows.
  config <- list("introduce" = list(), "plot_str" = list("type" = "diagonal", "fontSize" = 35, "width" = 1000, "margin" = list("left" = 350, "right" = 250)),
  "plot_missing" = list(),
  "plot_histogram" = list(),
  "plot_qq" = list(sampled_rows = 1000L),
  "plot_bar" = list(),
  "plot_correlation" = list("cor_args" = list("use" = "pairwise.complete.obs")),
  # "plot_prcomp" = list(),
  "plot_boxplot" = list(),
  "plot_scatterplot" = list(sampled_rows = 1000L)
  )
  DataExplorer::create_report(df %>% dplyr::select(1:9, 11:34), y = "price", config=config)
}
```

This exploratory analysis will be used to guide data cleaning.

### Cleaning Methods Used

All data was cleaned in R

1. Impute or omit NULL values
  Missing values exist for state, beds, bedrooms, bathrooms, zipcode, host response rate, and each of the review scores


2. Remove duplicates
- check that they're actually duplicates

### Feature Engineering - in RStudio
### Recommendations based on Prompt 2

notes:
demand is key - number of bookings normalized against number of listings per neighborhood
