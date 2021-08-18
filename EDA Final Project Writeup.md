# Outreach about Composting at Select MTA Stations in NYC

Chloe Bergsma-Safar

## Abstract

The purpose of this project was to identify an NYC subway station in each borough at which to conduct outreach to promote community composting. My criteria for selecting stations were 1) moderate traffic flow and 2) close proximity to food scrap drop-off locations. For my analysis, I used [turnstile](http://web.mta.info/developers/turnstile.html) and [station location data](http://web.mta.info/developers/developer-data-terms.html#data) provided by the Metropolitan Transit Authority as well as [food scrap drop-off site location data](https://data.cityofnewyork.us/Environment/Food-Scrap-Drop-Off-Locations-in-NYC/if26-z6xq) provided by the City of New York. In the end, I identified four stations, one in each borough except Staten Island (which didn't have a station that met criterion #1), that were all less than 0.1 miles from a food scrap drop-off site.

## Design

During the COVID-19 pandemic, NYC suspended its residential compost pick-up service. To promote composting in general and, specifically, community composting at food scrap drop-off sites across the city (which did not all close during the pandemic), the Department of Sanitation sought advice about selecting several stations at which to conduct outreach on this topic. 

## Data

The MTA turnstile dataset contains cumulative counts of the number of people who entered or exited a given station turnstile every four hours. The specific data pulled covers late April through July 2021 (the most recent data available when I began this project). Originally, there were 2,930,792 rows of turnstile data representing 379 stations. However, after merging the turnstile data with the MTA station location data, the number of stations dropped to 256.

To calculate the first criterion for station selection (moderate station traffic flow), I used columns with the station's name, date, cumulative entries and cumulative exits. I calculated each station's average number of daily entries/exits. Then, I filtered the stations down to those with median average daily entry/exit amounts (2500-3000). This resulted in a subset of 24 potential stations at which to conduct outreach.

Using latitudes and longitudes of these stations and the food scrap drop-off sites (there were 166 non-duplicated drop-off sites in the dataset), I created geospatial visualizations. I also calculated distances between them to first, find the nearest food scrap drop-off site to each of the 24 stations and second, select a station from each borough with the shortest distance between it and the nearest food scrap drop-off site.

## Analysis

#### Data Cleaning and Manipulation

- MTA turnstiles data - I adjusted for faulty/reverse data in the cumulative entries and exits columns before calculating average daily entries and average daily exits per station. After calculating these averages, I took a weighted average of both.

- MTA station location data - Before merging this dataset with the cleaned and manipulated turnstiles data, I modified the dataset so there was only one latitude and longitude per station (i.e., only one location per station). I also fixed some inconsistencies in the spelling of station names, the column on which I merged the datsets.

- Food scrap drop-off site location data - Before mapping these sites and calculating distances between them and the potential stations at which to conduct outreach (i.e., those with moderate traffic flow), I removed rows with duplicate site names.

#### Maps

Using the longitudes and latitudes of stations and food scrap drop-off sites, I created two maps. The first is of the 24 potential outreach stations and all of the food scrap drop-off sites across the city. The second is of the four stations that met both selection criteria and the nearest food scrap drop-off sites to each of them. I got assistance from [this article](https://medium.com/@ianforrest11/graphing-latitudes-and-longitudes-on-a-map-bf64d5fca391) to write the code to create these maps.

#### Distance Calculations

I used the Haversine distance equation in a function that calculated the distance between each of the 24 potential outreach stations and the food scrap drop-off sites and returned the nearest food scrap drop-off site to each station. Next, I used the Haversine distance equation again to calculate what each distance was between each station and its nearest food scrap drop-off site. I got assistance from [this article](https://medium.com/analytics-vidhya/finding-nearest-pair-of-latitude-and-longitude-match-using-python-ce50d62af546) to write the code to do these calculations.

## Tools

- Numpy, Pandas and SQLAlchemy for data manipulation
- Matplotlib and Seaborn for plotting
- Geopandas, Math and Shapely for distance calculations and geospatial analyses

## Communication

My complete code and presentation slides are available in this project's repo.

# ![map%20of%20outreach%20stations%20and%20nearest%20food%20scrap%20drop-off%20sites.png](attachment:map%20of%20outreach%20stations%20and%20nearest%20food%20scrap%20drop-off%20sites.png)

# ![outreach%20stations%20and%20distance%20to%20nearest%20food%20scrap%20drop-off%20sites.png](attachment:outreach%20stations%20and%20distance%20to%20nearest%20food%20scrap%20drop-off%20sites.png)


```python

```
