
# INFO 7374 Data Analysis Using Python - Final Project

## Yelp Fusion API Data Analysis

<img src="yelp.jpg">

Data that has been taken from the **Yelp API** has been analyzed.
Two other datasets have been used. 
Population data for each of the cities has been obtained from **FullContact API** and temperature data for cities in the US has been obtained from **National Centres for Environmental Information**. The websites for the datasets have been listed below.


*Data Formats*

1.Yelp - https://www.yelp.com/developers/documentation/v3 - API Request

2.FullContact API - https://www.fullcontact.com/developer/docs/ - API Requests

3.Weather data - https://www.ncdc.noaa.gov/ - ZIP Files of temperature data


Data processing from Yelp API has been done based on three categories
1.	Restaurants
2.	Hotels
3.	Attractions


### Data Collection and Processing

**Running the file**

Command : **python 'Data Collection and Processing.py' "City Name" "category name"**

Yelp Data categories have been specified above

**__Fetching the Data__**

* The API requests are placed to the Yelp API based on user search term to get related businesses
* The population data for these cities are fetched by placing a request to FullContact API.

**Storing the Data**

Yelp Data

 * Click [here](Yelp Data) to view the data downloaded from Yelp
 * Files are segregated based on country and state.
 * Files are stored in json format.
    
Population Data
 * Click [here](Population Data) to view the data downloaded from FullContact API
 * Files are segregated based by country.
 * Files are stored in json format.

**Post Process of data**


Yelp Data - Post Processing

* Storing the restaurant or hotel category and timings in separate CSV files.

Location: [Restaurant Category and Timings](Other Files)

Population Data - Post Processing
* Joining population data and country abbreviations to form a consolidated data.

Location: [Consolidated Population Data](Other Files)

**Creating the input file for performing analysis**

* The yelp data is merged with the population data (joining operations) based on location to get the final data to be analyzed

## Analysis Performed

**Running the file**

Command : **python Analysis.py**

The user is prompted to select what analysis he wants to perform. Based on the analysis selected, the user is prompted for inputs. Once the user enters all inputs, the necessary python file is called.

## Analysis 1

### Places(restaurants,hotels,attractions) per capita value for a city

Input parameters prompted:

1. City 
2. Country

**Steps:**

1. The [Processed Data](Other Files) file containing the Yelp and population data is read.

2. The city and country names are passed using argparse to the python file.

3. The data is filtered based on city and country value inputs

4. The per capita value is calculated for the city is calculated (Number of places/population per 1000)

5. The data is stored in the first row of the data frame

6. The per capita value for other cities in that country is also calculated for comparison.

7. CSV Files and plots are generated for top ten cities

## Outputs

CSV Files: [Restauarant Per Capita](Output Files/Analysis 1/CSV Files)

Plot Files: [Restaurant Per Capita Plot](Output Files/Analysis 1/Plot)

<img src="Readme- data/Analysis 1.jpg">

## Places per capita plot

<img src="Output Files/Analysis 1/Plot/Restaurant-Per-Capita.jpg">

## Analysis 2


### Restaurants currently open at this time in your city

Input parameters prompted:

1. City 
2. Country

**Steps:**

1. The processed csv file containing the Yelp and population data is read
2. The restaurant timing data is used to get the timing of the restaurant
3. The time at which the user enters the query is fetched and compared with each of the restaurant timings available [here](Other Files)
4. Column splitting is done here to ensure that the hours of operation can be compared.
5. The restaurants that are currently open are displayed

## Outputs

CSV Files: [Restaurants Open Now](Output Files/Analysis 2/CSV Files)

Plot Files: [Restaurant Open Now - Top 10 based on rating ](Output Files/Analysis 2/Plot)

<img src="Readme- data/Analysis 2.jpg">

## Restaurants open with rating plot

<img src="Output Files/Analysis 2/Plot/Restaurants-Open.jpg">

## Analysis 3


### Top Cuisines

Input parameters:
    
1. Country

Steps:

1. The processed csv file containing the Yelp and population data is read
2. Top categories of restaurants are analyzed from the data available [here](Other Files)

## Outputs

CSV Files: [Top Cuisines in the Country](Output Files/Analysis 3/CSV Files)

Plot Files: [Top 3 Restaurants in each Cuisine](Output Files/Analysis 3/Plot)

<img src="Readme- data/Analysis 3.jpg">

## Restaurants cuisine distribution

<img src="Output Files/Analysis 3/Plot/Top-Cuisines.jpg">

## Top 3 Restaurants in each of top cuisines

<img src="Output Files/Analysis 3/Plot/Top-Cuisines-Restaurants.jpg">

## Analysis 4

### Temperature and attractions relations

**Steps:**

1. The processed csv file containing the Yelp and Temperature is read for US - [Data Source](Other Files)
2. The Yelp data is joined with the temperature data.
3. For each city the number of attractions and average temperature is calculated
4. Temperature data is already preprocessed and obtained as average for each state in US

**Weather Data Prepocessing**
* Weather data obtained as zip files are extracted and monthly data is aggregated for each state. (Data available only for US)
* This data is used as the source to join with the Yelp data

**Inference**

Scatter plots are drawn to find positive or negative correlation between number of attractions in each place and average temperature of the place



## Outputs


CSV Files:  [Relation between number of attractions and temperature](Output Files/Analysis 4/CSV Files)

Plot Files: [Relation between number of attractions and temperature](Output Files/Analysis 4/Plot)

<img src="Readme- data/Analysis 4.jpg">

## Number of attractions in each state Vs temperature

<img src="Output Files/Analysis 4/Plot/Attractions-Temperature-relation.jpg">

## Analysis 5


### Rating of place and Review Vs Price Rating

Steps:

1. The processed csv file containing the Yelp is read
2. The relationship between the rating of the place and the price is anaylzed

**Inference**
* Scatter plots are drawn between the rating of a place and the price rating and review count for a place and price rating

* We observe different results for each country

## Outputs

Plot Files: [Rating of place and review count Vs Price Rating](Output Files/Analysis 5/Plot)

## Place Rating Vs Price Rating

<img src="Output Files/Analysis 5/Plot/Rating of place Vs Place Rating.jpg">

## Review Count Vs Price Rating

<img src="Output Files/Analysis 5/Plot/Review Count Vs Place Rating.jpg">

## Analysis 6

### Country wise distribution of total businesses (Map plot)

Input parameters
1. Business name to aggregata (eg. hotels)

**Steps:**
1. We fetch the processed Yelp data from the csv [here](Other Files)
2. Based on user input (hotels,attractions,restaurants) we calculate number of businesses per country.
2. [countries.geojson](Other Files) file contains the geographic data of the countries.
3. The Yelp Data country code is altered since the datasets have different country codes.
4. These two files are joined to help us plot a heat map.

## Output

CSV Files: [Country_Aggregated_Category](Output Files/Analysis 6/CSV Files)

Plot Files: [Top 3 Restaurants in each Cuisine](Output Files/Analysis 6/Plot)

<img src="Readme- data/Analysis 6.jpg">

## Country wise heat map of business

<img src="Output Files/Analysis 6/Plot/country_distribution_category.jpg">
