# Premier League Data Warehouse (1993-2024)

This repository contains a comprehensive data warehouse of Premier League matches from 1993 to 2024. The data warehouse is designed to provide a centralized repository for match information, including details such as match date, stadium, weather, referee, and more.

## Project Overview

The project aims to create a robust data warehouse that stores extensive data on Premier League matches over a period of more than three decades. The data warehouse is implemented using SQL scripts, ETL processes, and other supporting files.

## Project Structure

- **SQL Scripts**: Contains scripts for creating the database schema, tables, and relationships.
- **ETL/ELT Scripts**: Scripts for extracting, transforming, and loading data into the data warehouse.
- **Excel Files**: Source data files with match information, including date, stadium, weather conditions, referees, and other details.
- **Visual Studio Solution**: The project is set up in Microsoft Visual Studio, which includes all necessary configurations for the data warehouse.

## Repository Contents

- **SQL Scripts**
  - `Script SQL.txt`: This script contains the SQL commands to create the database schema, including dimension and fact tables that structure the data warehouse.
  - `SQL Script (script).sql`: Another script file containing SQL commands related to the data warehouse.
  - `SQL Script (EER diagram).mwb`: MySQL Workbench model file for the EER diagram of the database schema.
  
- **Visual Studio Project**
  - `DataWarehouse.sln`: Visual Studio solution file for the project.
  - `DataWarehouse.dtproj`: Visual Studio project file for ETL operations.
  - `DataWarehouse.dtproj.user`: Contains user-specific configurations for the Visual Studio project.

![Logical Schema of the Data Warehouse](https://github.com/user-attachments/assets/6aaea544-476e-4a6e-8eb8-070e11456619)
*Logical Schema of the Data Warehouse*

![ETL Overview](https://github.com/user-attachments/assets/9d242ed6-7c85-47a5-9972-02bf250b458b)
*ETL Overview*

![Control Flow](https://github.com/user-attachments/assets/02ea1cfd-787d-47ab-9a9c-43200fcb5e0e)
*Control Flow*

## Data Warehouse Schema

The data warehouse consists of several dimension tables and a central fact table:

### Dimension Tables:
- **dimAwayTeam**: Stores information about the away team including shots, corners, fouls, and cards.
- **dimHomeTeam**: Stores information about the home team including shots, corners, fouls, and cards.
- **dimReferee**: Contains information about the referees.
- **dimContinent**: Stores continent names.
- **dimCountry**: Stores country information with a reference to the continent.
- **dimCity**: Stores city information with a reference to the country.
- **dimStadium**: Stores stadium information with a reference to the city.
- **dimMatchDate**: Contains details about the match date.
- **dimFullTimeResult**: Stores information about the full-time results of matches.
- **dimWeather**: Stores weather-related data like temperature, wind speed, and humidity.
- **dimSeason**: Contains season information.
- **dimMatchTime**: Stores the match time.

### Fact Table:
- **factMatch**: The central table containing the core match details, linking to the various dimension tables.

## Getting Started

### Prerequisites

- [MySQL](https://www.mysql.com/) - Required to set up the database.
- [Microsoft Visual Studio](https://visualstudio.microsoft.com/) - Used to manage and deploy the project.

### Setting Up the Data Warehouse

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Crowz102/Data_PremierLeague.git
