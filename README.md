_Project Overview_
This project explores the relationship between Formula 1 pit-stop time and a car’s final race position using historical race data. The goal is to answer a simple but important question:

Does having the fastest pit stop in a race correlate with a better final position?

The analysis was completed as a final project for DATA 506 and focuses on building a clean, well-documented pipeline: from raw CSVs, to a merged and cleaned dataset, to statistical analysis and
visualization of the correlation between variables.




_Data Source_

The data comes from a Kaggle Formula 1 World Championship dataset (1950–2020), specifically using the following tables:

  results.csv – contains race results (raceId, driverId, constructorId, finishing position, points, etc.)
  pit_stops.csv – contains pit stop information (raceId, driverId, lap, pit stop duration, pit_stop_time, pitstop_milliseconds, etc.)

These tables are joined so that, for each car in each race, we can connect how long their pit stops took with how they finished.




_Methodology_

1. Loading and Merging the Data

The analysis is implemented in a Jupyter notebook using Python and pandas:

  1) Read both CSVs using pd.read_csv().
  
  2) Merge the two datasets into a single DataFrame using shared keys (such as raceId and driver/result identifiers), so that each row contains:

           1) A race identifier

           2) Pit-stop information

           3) Final position information

  3) This merged table is the basis for all subsequent analysis.


2. Exploratory Data Inspection

To understand the raw data structure, several basic EDA steps are performed:
  Shape & structure

  df.shape to see the number of rows and columns

  df.head() to preview a few example rows

  df.info() and df.dtypes to inspect column types and non-null counts

  Descriptive statistics

  df.describe() for numerical columns (count, mean, std, min, max, quartiles)

  df.describe(include=['object']) for basic stats on categorical columns

  This step reveals which columns are IDs, which are categorical (e.g., status), and which are continuous (e.g., pit-stop times in milliseconds).




_Key Findings:_

  1) There is a weak to moderate negative correlation between pit-stop time and final race position.

  2) Cars that record the fastest pit stop in a race tend, on average, to finish higher (closer to 1st place).

  3) Even though pit-stop time is not the only factor influencing race results, it is a meaningful and statistically significant factor.

Practical implication:
Teams can likely improve race outcomes by investing in more efficient pit crews and better pit-stop strategies, as saving even a small amount of time in the pits can contribute to better final positions.




_Challenges_

During the project, a few challenges had to be addressed:

Deciding how to handle NaN values and '\N' placeholders in key columns.

Correctly merging multiple datasets without creating duplicate or inconsistent rows.

Reducing a complex, multi-table dataset down to just the columns necessary to answer the research question.

Implementing the split–apply–combine pattern to correctly extract a single “fastest” pit stop per race.




_Possible Extensions / Future Work_

This project focuses only on pit-stop time vs. final position. Future extensions could include:

Adding driver and team (constructor) information to see which teams are consistently strong in pit stops.

Incorporating number of pit stops, starting grid position, safety car periods, or weather conditions.

Fitting multiple regression models or machine learning models to predict final position using a richer set of race features.

Comparing different eras of Formula 1 (e.g., pre-2000 vs. modern hybrid era) to see whether pit-stop impact has changed over time.
