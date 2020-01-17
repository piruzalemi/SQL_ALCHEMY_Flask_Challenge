# SQL_ALCHEMY_Flask_Challenge

### STEP 1: Preliminary Steps:

1. This Piruz Alemi Respository uses Python and SQLAlchemy to do basic climate analysis and data exploration of  climate database. All of the following analysis was completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.
   
2. I Used SQLAlchemy to `create_engine` to connect to an sqlite database.
3. I also Used SQLAlchemy `automap_base()` to reflect my tables into classes and saved
   a reference to those classes called `Station` and `Measurement`, for easy access.

### STEP 2: Precipitation Analysis

* I Designed a query to retrieve the last 12 months of precipitation data.

* Selected only the `date` and `prcp` values.

* Loaded the query results into a Pandas DataFrame and set the index to the date column.

* Sorted the DataFrame values by `date`.

* Plotted the results using the DataFrame `plot` method.

  ![precipitation](Images/precipitation.png)

* Used Pandas to print the summary statistics for the precipitation data.

### STEP 3: Station Analysis

* Designed a query to calculate the total number of stations.
* Designed a query to find the most active stations.
  * Listed the stations and observation counts in descending order.
  * Noted: Which station has the highest number of observations?
  * I used functions such as `func.min`, `func.max`, `func.avg`, and `func.count` in my queries.
  * Designed a query to retrieve the last 12 months of temperature observation data (tobs).
  * Filtered by the station with the highest number of observations.
  * Plotted the results as a histogram with `bins=12`. See:
    ![station-histogram](Alemi/Images/station-histogram.png)

- - -

## Step 4 - Climate App

Once I completed my initial analysis, I designed a Flask API based on the queries that I have just developed.
* Most Importantly ! I Used FLASK to create my routes for the latter querris.

### The Routes Created Included:

* `/`
  * Home page.
  * Listed all routes that are available.
* `/api/v1.0/precipitation`
  * Converted the query results to a Dictionary using `date` as the key and `prcp` as the value.
  * Return the JSON representation of my dictionary.
* `/api/v1.0/stations`
  * Returned a JSON list of stations from the dataset.
* `/api/v1.0/tabs`
  * querried for the dates and temperature observations from a year from the last data point.
  * Returned a JSON list of Temperature Observations (tobs) for the previous year.
* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`
  * Return a JSON list of the minimum temperature, the average temperature, and the max temperature 
  *                                                for a given start or start-end range.
  * When given the start only, I calculated `TMIN`, `TAVG`, and `TMAX` for all dates greater 
  * than and equal to the start date.
  * When given the start and the end date, calculated the `TMIN`, `TAVG`, and `TMAX` for
  * dates between the start  and end date inclusive.

## STEP 5: Solutions:

* I joined the station and measurement tables for some of the analysis queries.
* I Used Flask to  `jsonify` to convert MY API data into a valid JSON response object.

Thank you. Piruz Alemi Jan 8th, 2020

