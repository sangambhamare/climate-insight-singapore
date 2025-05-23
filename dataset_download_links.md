# Climate Change Datasets for Singapore

This document provides direct download links for climate change datasets relevant to Singapore. These datasets can be used for the ClimateInsight Singapore project.

## World Bank Climate Change Data

### 1. World Bank Climate Change Knowledge Portal - Singapore

- **Description**: Comprehensive climate data for Singapore including historical observations and future projections
- **Download Link**: [https://climateknowledgeportal.worldbank.org/country/singapore/climate-data-historical](https://climateknowledgeportal.worldbank.org/country/singapore/climate-data-historical)
- **Data Format**: CSV, Excel
- **Variables**: Temperature, Precipitation, Climate Indices

### 2. World Development Indicators - Climate Change

- **Description**: World Bank indicators related to climate change, including data for Singapore
- **Download Link**: [https://databank.worldbank.org/source/world-development-indicators](https://databank.worldbank.org/source/world-development-indicators)
- **Data Format**: CSV, Excel, XML
- **Variables**: CO2 emissions, Energy use, Forest area, Renewable energy

## Humanitarian Data Exchange (HDX)

### 3. Singapore Climate Change Indicators

- **Description**: Climate change indicators for Singapore from the World Bank
- **Download Link**: [https://data.humdata.org/dataset/world-bank-climate-change-indicators-for-singapore](https://data.humdata.org/dataset/world-bank-climate-change-indicators-for-singapore)
- **Data Format**: CSV
- **Variables**: Various climate indicators

## Singapore Government Data

### 4. Data.gov.sg - Environment

- **Description**: Singapore government's open data portal with environmental datasets
- **Download Link**: [https://data.gov.sg/group/environment](https://data.gov.sg/group/environment)
- **Data Format**: CSV, JSON
- **Variables**: Weather, Air quality, Rainfall, Temperature

### 5. Meteorological Service Singapore

- **Description**: Historical weather data and climate reports for Singapore
- **Download Link**: [http://www.weather.gov.sg/climate-historical-daily/](http://www.weather.gov.sg/climate-historical-daily/)
- **Data Format**: CSV, PDF
- **Variables**: Temperature, Rainfall, Humidity, Wind

## International Datasets

### 6. NASA GISS Surface Temperature Analysis

- **Description**: Global temperature data including Singapore
- **Download Link**: [https://data.giss.nasa.gov/gistemp/](https://data.giss.nasa.gov/gistemp/)
- **Data Format**: CSV, NetCDF
- **Variables**: Temperature anomalies

### 7. NOAA Global Historical Climatology Network

- **Description**: Historical climate data including Singapore stations
- **Download Link**: [https://www.ncdc.noaa.gov/data-access/land-based-station-data/land-based-datasets/global-historical-climatology-network-ghcn](https://www.ncdc.noaa.gov/data-access/land-based-station-data/land-based-datasets/global-historical-climatology-network-ghcn)
- **Data Format**: CSV
- **Variables**: Temperature, Precipitation

## Sea Level Data

### 8. Permanent Service for Mean Sea Level

- **Description**: Sea level data including Singapore tide gauge
- **Download Link**: [https://www.psmsl.org/data/obtaining/stations/180.php](https://www.psmsl.org/data/obtaining/stations/180.php)
- **Data Format**: CSV, Text
- **Variables**: Sea level measurements

## Emissions Data

### 9. Global Carbon Atlas - Singapore

- **Description**: CO2 emissions data for Singapore
- **Download Link**: [http://www.globalcarbonatlas.org/en/CO2-emissions](http://www.globalcarbonatlas.org/en/CO2-emissions)
- **Data Format**: CSV, Excel
- **Variables**: CO2 emissions

## Downloading Instructions

1. For direct CSV downloads:
   - Click on the download link
   - Look for "Download" or "CSV" buttons
   - Save the file to your local machine

2. For data portals (like World Bank DataBank):
   - Select "Singapore" as the country
   - Choose relevant climate indicators
   - Select the time period (e.g., 1960-present)
   - Click "Download" and choose CSV format

3. For API access (advanced):
   - Many of these sources provide API access
   - Documentation is typically available on their websites
   - Example for data.gov.sg: [https://data.gov.sg/developer](https://data.gov.sg/developer)

## Using the Data in Databricks

1. Upload the downloaded CSV files to Databricks DBFS:
   ```python
   # In a Databricks notebook
   dbutils.fs.mkdirs("dbfs:/FileStore/climate_resilience/datasets")
   
   # Then use the UI to upload files to this location
   # Or use dbutils.fs.put to upload programmatically
   ```

2. Read the data in your notebooks:
   ```python
   # Example for reading CSV
   df = spark.read.csv("dbfs:/FileStore/climate_resilience/datasets/your_file.csv", 
                      header=True, inferSchema=True)
   
   # Convert to pandas if needed
   pdf = df.toPandas()
   ```

These datasets provide a comprehensive foundation for analyzing climate change impacts on Singapore and developing the ClimateInsight Singapore solution.
