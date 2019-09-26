# Surfs Up!

## Climate Analysis and Exploration

To begin, I used Python and SQLAlchemy to do basic climate analysis and data exploration of the climate database. All of the following analysis was completed using SQLAlchemy ORM queries, Pandas, and Matplotlib

* Choose a start date and end date

* Use SQLAlchemy `create_engine` to connect to sqlite database

* Use SQLAlchemy `automap_base()` to reflect tables into classes and save a reference to those classes called `Station` and `Measurement`

### Precipitation Analysis

* Designed a query to retrieve the last 12 months of precipitation data

* Selected only the `date` and `prcp` values

* Loaded the query results into a Pandas DataFrame and set the index to the date column

* Sorted the DataFrame values by `date`

* Ploted the results using the DataFrame `plot` method

* Used Pandas to print the summary statistics for the precipitation data

### Station Analysis

* Designed a query to calculate the total number of stations

* Designed a query to find the most active stations

  * Listed the stations and observation counts in descending order

* Designed a query to retrieve the last 12 months of temperature observation data (tobs)

  * Filtered by the station with the highest number of observations

  * Ploted the results as a histogram with `bins=12`

### Temperature Analysis

* Used the `calc_temps` function to calculate the min, avg, and max temperatures for trip using the matching dates from the previous year (i.e., use "2017-01-01" if your trip start date was "2018-01-01")

* Ploted the min, avg, and max temperature from previous query as a bar chart

### Daily Rainfall Average

* Calculated the rainfall per weather station using the previous year's matching dates

* Calculated the daily normals. Normals are the averages for the min, avg, and max temperatures

* Created a list of dates for trip in the format `%m-%d`. Used the `daily_normals` function to calculate the normals for each date string and append the results to a list

* Loaded the list of daily normals into a Pandas DataFrame and set the index equal to the date

* Used Pandas to plot an area plot (`stacked=False`) for the daily normals

- - -

## Climate App

Designed a Flask API based on the queries

* Used FLASK to create routes

### Routes

* `/`

  * Home page

  * Lists all routes that are available

* `/api/v1.0/precipitation`

  * Converts the query results to a Dictionary using `date` as the key and `prcp` as the value

  * Returns the JSON representation of the dictionary

* `/api/v1.0/stations`

  * Returns a JSON list of stations from the dataset

* `/api/v1.0/tobs`
  * Queries for the dates and temperature observations from a year from the last data point
  * Returns a JSON list of Temperature Observations (tobs) for the previous year

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

  * Returns a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range

  * When given the start only, calculates `TMIN`, `TAVG`, and `TMAX` for all dates greater than and equal to the start date

  * When given the start and the end date, calculates the `TMIN`, `TAVG`, and `TMAX` for dates between the start and end date inclusive


