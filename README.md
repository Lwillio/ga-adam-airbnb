# ga-adam-airbnb
General Assembly - Guided Project - AirBnB Amsterdam

## Project Statement

A client wants to invest in an AirBnB property in Amsterdam, Netherlands. Using a provided, scraped dataset, advise your client using at least one of the following prompts:

* How much revenue do successful hosts generate?
* Which property types receive the most positive reviews?
* Which neighborhoods host the most listings?
* Which neighborhoods receive the most positive reviews?

Finally, provide your client a clear investment recommendation for a specific market.

## [Final Project](https://github.com/Lwillio/ga-adam-airbnb/tree/main/final-project)

This sub folder contains all project files for this project as completed for the guided project. Exploratory Data Analysis, Data Cleaning and Feature Engineering were completed [in R](https://github.com/Lwillio/ga-adam-airbnb/blob/main/final-project/a_dam_airbnb.R), and results were visualized in [Tableau Public](https://public.tableau.com/profile/lg1798#!/vizhome/Project1_672/HMAVGREVPTRT).

Which Property Types receive the most positive reviews?

![Average Reviews by Property Type as a function of Review and Count](https://github.com/Lwillio/ga-adam-airbnb/blob/main/final-project/images/avgRev-propType-reviews.png)

Based on the data (and the interpretation at the time of "highest count of high reviews"), **Apartment** listings for the entire apartment received the most positive reviews, followed by **House - Entire** and **Boat - Entire** respectively.

For investment recommendations, Revenue was the primary indicator used to advise the client, both by Property Type and by Neighborhood. 

![Revenue by Property Type](https://github.com/Lwillio/ga-adam-airbnb/blob/main/final-project/images/revenueByPropType.png)

The top three property types to recommend were **Villa**, **Boat**, and **Loft** in that order, based on median revenue. 

![Revenue by Neighborhood](https://github.com/Lwillio/ga-adam-airbnb/blob/main/final-project/images/revenueByNeighborhood.png)

The top three neighborhoods to recommend were, in order; **Center-West**, **Center-East**, and **The Baarsjes** - with Center-West as the clear leader for total revenue. 

Finally, updating the Average Reviews visualization from before to a function of Revenue rather than Count of Reviews, we see **Apartment** as the leader once more, followed by **House - Entire** and **Boat - Entire** more closely tied for second than before.

![Average Revenue by Property Type as function of Revenue](https://github.com/Lwillio/ga-adam-airbnb/blob/main/final-project/images/avgRev-propType-revenue.png)

Combining these data outcomes, a final recommendation was made for investing in a **Boat** in the **Center-West** neighborhood, with the intention of renting the entire property on AirBnB. Revenue was prioritized over reviews to arrive at this recommendation, however, reviews determined the final recommendations from the available options.

_Full Tableau workbook available_ [here](https://public.tableau.com/profile/lg1798#!/vizhome/Project1_672/HMAVGREVPTRT), _please see Metadata at the bottom of the page to navigate between visualizations._

## _TBD - Final Project - Revision_ 

_TBD - this project will be revisited both to complete prompts not approached earlier and to reattempt the original prompt with better and more complete information/analysis_
