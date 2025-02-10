# median-house-price

## Project introduction
This project is to predict median house prices for different postcodes in the UK.

## Challenge
Since the distribution of median house prices is affected by geographical location and there is a huge gap between house prices in dataset. For example, there may be particularly high house prices in an area with low house prices.  That will cause serious class imbalance problem.

## Dataset
Three `.csv` files, `postcodes_labelled.csv`, `district_data.csv` and `sector_data.csv` deal with information indexed by postcode, or postcode sector.

The fully labelled `postcodes_labelled.csv` data provides a sample of labelled data for postcodes in a region of England. The column headings are:

- `postcode`: The full unit postcode for the row.
- `sector`: The postcode sector for the row.
- `easting`: The OS easting (in m) for the centroid of this postcode.
- `northing`: The OS easting (in m) for the centroid of this postcode.
- `soilType`: The typical soil type for the postcode, as a category.
- `elevation`: The height (in m) above sea level for the centroid of this postcode.`
- `nearestWatercourse`: The name of the nearest river or stream to this postcode.
- `distanceToWatercourse`: The distance (in m) from the centroid of this postcode to the nearest watercourse.
- `localAuthority` The Local Authority governing this postcode
- `riskLabel` The probability class for flood risk (from rivers and seas) for the postcode
- `medianPrice` A typical house price (in £) for this postcode.
- `historicFlooding` A binary flag indicating whether this postcode has experienced major flooding since 1949.

The postcode format in the file uses numbers and capital letters, and has a single space in the middle separating the district from the sector/unit label. This should be treated as the canonical format for postcodes in this exercise (and the one you should output), but it is not guaranteed that all postcodes you may encounter will be in this format. Consider the postcodes "SW7 2AZ" and "SW1A 1AA", a non-exhaustive list of alternative formats include

```
SW7 2AZ, SW1A 1AA
sw7 2az, sw1a 1aa
SW72AZ, SW1A1AA
SW7 2AZ, SW1A1AA
SW7  2AZ, SW1A 1AA  
```

Note that the last two version have a fixed length (of 7 or 8 characters respectively). This makes these a common format in some kinds of database.

The `sector_data.csv` file contains information on the number of people (the headcount) and  households in each postcode at the sector level, as well as the number of postcode units in each sector. This is a component contributing to the impact factors involved in a flooding event.

The `district_data.csv` file contains information on the number of pets in each postcode. Additional similiar data (or similar data at the sector level) can be added if it will improve the quality of your predictions.

## Data preprocessing
This project used geographical & bin splitting to generate datasets. Applying data resampling method to address class imbalance problem.

## Model performance
| **MODEL** | **RMSE** | **R^2** |
| :------------------ | :---: | :---: |
| *XGBoost* | 405653 | 0.8193 |
| *RandomForest* | 402137 | 0.8224 |