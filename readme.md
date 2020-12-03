# 2016-2017 NYC Real Estate Sales Exploration
## by Tatiana Tikhonova


## Dataset

To analyze, I've taken [this dataset](https://www.kaggle.com/new-york-city/nyc-property-sales) that consists of information regarding properties sold in New York City over a 12-month period from September 2016 to September 2017. It contains the location, address, type, sale price, and sale date of building units sold. 

A reference on the trickier fields:

**BOROUGH**: A digit code for the borough the property is located in; in order these are Manhattan (1), Bronx (2), Brooklyn (3), Queens (4), and Staten Island (5).

BLOCK; LOT: The combination of borough, block, and lot forms a unique key for property in New York City. Commonly called a **BBL**.

**BUILDING CLASS AT PRESENT and BUILDING CLASS AT TIME OF SALE**: The type of building at various points in time. 
See the [glossary of terms](https://www1.nyc.gov/assets/finance/downloads/pdf/07pdf/glossary_rsf071607.pdf) for reference.

For the **building classification codes** see the [Building Classifications Glossary](https://www1.nyc.gov/assets/finance/jump/hlpbldgcode.html).

Note that because this is a financial transaction dataset, there are some points that need to be kept in mind:

Many sales occur with a nonsensically **small dollar amount**: $0 most commonly. These sales are actually **transfers of deeds between parties**: for example, parents transferring ownership to their home to a child after moving out for retirement.

This dataset uses the financial definition of a building/building unit, for tax purposes. 
- In case a single entity owns the building in question, a sale covers the value of the entire building. 
- In case a building is owned piecemeal by its residents (a condominium), a sale refers to a single apartment (or group of apartments) owned by some individual.

**Data Wrangling** steps performed:
- Dropping unneeded columns
- Formatting data (e.g. converting DateTime values from string to DateTime)
- Replacing Borough codes with appropriate naming conventions
- Dropping null rows
- Converting upper case to title
- Combining commercial and residential unit values into the separate Units column
- Renaming columns
- Stripping column values of extra text (i.e. k['Class'].str.lstrip('0123456789 ')


## Summary of Findings

In the exploration, I found that there was a strong relationship between the
price of a property and its size and location. Both # of units and square footage affected cost to the same degree. 

I was surprised to find out that Hotels, Office Buildings, and Condo-Rentals were most expensive when looking at the sales by building and by apartment. Naturally, both took place in Manhattan.

I also observed a correlation I wouldn't think of: Lot (aka building location) and Year Built. From the NY Glossary of Terms, we know that a Tax Lot is a subdivision of a Tax Block and represents the property unique location. And while this correlation is not something I would easily think of, it makes perfect sense: they say, Rome wasn't built in one day -- the same goes for New York City. It took time, and it's only natural that some lots and blocks were developed in one time period, with others preceding or following.

When looking at the Sale Price by Year Built matrix, I saw that the Manhattan Office Building built in 60-70s, and also 90s, sold at the highest rates. Rental apartments built in Manhattan around the 70s also scored high as far as Sale Prices go. When I looked at the total number of sales regardless of the price however, it turned out that the majority of properties sold in our given time range was comprised of single family dwellings in Queens built sometime between 1925 and 1960. 


## Key Insights for Presentation

I decided to focus on property sales by borough, quantity and price, eliminating units and square footage as well as year when the property was built. This helps streamling the presentation and avoid confusion. 

I begin by giving the general dataset overview, and introducing the Apt and Bldg distribution by Borough. I then dive into pricing, sales total as well as average per property. I compare the results while drilling sales by class and comment on the results.
