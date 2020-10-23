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

All data was cleaned in R. The additional provided Translations files were also used to clean and normalize the data.


1. Impute or omit NULL values

The dataset was subsetted to only include rows with NA values (NULLs in R). This allowed manual review to determine best steps to resolve these values.

  Missing values exist for state, beds, bedrooms, bathrooms, zipcode, host response rate, and each of the review scores
  - neighborhood column translated using additional file provided, no NULLS existed
  - city column used translated value, effectively imputing all values to Amsterdam
  - state column NULLs (0.1%) imputed to North Holland per State Translation file, all other rows translated to North Holland
  - zip column NULLs (2.22%) imputed to mode of zip by neighborhood
  - bedrooms (0.18%), beds (0.17%), and bathrooms (0.88%) NULL rows were omitted from the data set, they comprised less than 1% of rows and could not be reasonably imputed - 49 rows affected
  - host response rate (HRR) column NULLs (9.35%) imputed to zero
  - review scores rows removed if all values zero
  - review scores rows containing NaN values also removed, due to effect on dataset; relative low effect of removal on dataset - 14 rows affected, all with 2 or fewer reviews
  - review scores NULLs imputed to mean value of scores if at least one rating existed to retain the mean rating while also giving a more reasonable approximation of the value of these ratings had they been provided
 
 Review scores NULLs existed for over 20% of rows, but not all rows contained NULLs for all review values. Rows with zero reviews were removed from the data set per the given instructions.


2. Remove duplicates

Using the dplyr package in R, duplicate rows were identified. These were manually checked against the dataset in Excel. Once the duplicates were checked and verified, these were eliminated from the dataset. Approximately 20 rows were affected.

Once cleaning was complete, another EDA report was run on the new data. See [clean data EDA report](final-project/edaReport_cleandata.html)


### Feature Engineering - in R

1. A zip_no column was created, containing only the numerical portion of the provided zip code. The analysis did not require more granularity than "neighborhood" so specificity here was not needed.
2. host_since_anniversary was split into month and day, with day imputed to the first of the month if null, then combined with existing host_since_year column to generate a single column host_since date in date format. Two null host_since rows were ignored after identification here.
3. Additional columns added to be able to calculate revenue: number of people accommodated, number of guests included, cost per night for max number accomodated, cost to book, estimated number of stays, and estimated total revenue

### Recommendations based on Prompt 2

notes:

demand is key - number of bookings normalized against number of listings per neighborhood

overlay zipcode and neighborhood maps to see if specific subsections are correlated to anything
