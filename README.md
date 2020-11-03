# Investing in an AirBnB Property in Amsterdam
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

![Average Reviews by Property Type as a function of Review and Count](/final-project/images/avgRev-propType-reviews.png)

Based on the data (and the interpretation at the time of "highest count of high reviews"), **Apartment** listings for the entire apartment received the most positive reviews, followed by **House - Entire** and **Boat - Entire** respectively.

For investment recommendations, Revenue was the primary indicator used to advise the client, both by Property Type and by Neighborhood. 

![Revenue by Property Type](/final-project/images/revenueByPropType.png)

The top three property types to recommend were **Villa**, **Boat**, and **Loft** in that order, based on median revenue. 

![Revenue by Neighborhood](/final-project/images/revenueByNeighborhood.png)

The top three neighborhoods to recommend were, in order; **Center-West**, **Center-East**, and **The Baarsjes** - with Center-West as the clear leader for total revenue. 

Finally, updating the Average Reviews visualization from before to a function of Revenue rather than Count of Reviews, we see **Apartment** as the leader once more, followed by **House - Entire** and **Boat - Entire** more closely tied for second than before.

![Average Revenue by Property Type as function of Revenue](/final-project/images/avgRev-propType-revenue.png)

Combining these data outcomes, a final recommendation was made for investing in a **Boat** in the **Center-West** neighborhood, with the intention of renting the entire property on AirBnB. Revenue was prioritized over reviews to arrive at this recommendation, however, reviews determined the final recommendations from the available options.

_Full Tableau workbook available_ [here](https://public.tableau.com/profile/lg1798#!/vizhome/Project1_672/HMAVGREVPTRT), _please see Metadata at the bottom of the page to navigate between visualizations._

## _TBD - Final Project - Revision_ 

_TBD - this project will be revisited both to complete prompts not approached earlier and to reattempt the original prompt with better and more complete information/analysis_

In assembling this repo for this project after the fact, I noticed several aspects I would approach differently on a redo of the project. Many of these are down to putting more focus on learning and exploring the tools used - both R and Tableau were new to me - or to a lack of version control.

I would like to:

- clean up the R code, removing zombie code and adding more complete documentation; possibly moving most of the initial-pass exploration to a separate script. 
- focus on properly normalizing the data i.e. accounting for number of properties when answering the question
- include data on home purchase prices if possible, as the initial outlay for the investment should be taken into consideration
- ensure the data visualizations tell the correct story
- address additional prompts and effect on initial location and property type suggestions
- look at zipcode in addition to neighborhood in case a more specific recommendation can be made
- incorporate some of the explanations/generalizations for categories like "number of beds" and "accomodates" to better present the data
- incorporate a dataset of bus stop locations to determine effect of accessiblity to number of bookings and overall rating
- determine effect of density of bookings per area code to see if competition for guests is something to be considered (good use for a Tableau visualization using a neighborhood overlay)
- incorporate data on tourist attractions and sights to determine any effect on ratings and/or bookings


Overall, I would like to more carefully curate a response to all questions posed by the project, particularly now that I have a better understanding of the tools used and potential approaches.


