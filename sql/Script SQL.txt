CREATE DATABASE datawarehouse;
use datawarehouse;

CREATE TABLE dimAwayTeam (
  TeamID INT auto_increment PRIMARY KEY,
  TeamName VARCHAR(255) NOT NULL,
  AwayTeamShotsOnTarget INT,
  AwayTeamShots INT,
  AwayTeamCorners INT,
  AwayTeamFouls INT,
  AwayTeamYellowCards INT,
  AwayTeamRedCards INT,
  HalfTimeAwayTeamGoals INT,
  FullTimeAwayTeamGoals INT
);


CREATE TABLE dimHomeTeam (
  TeamID INT auto_increment PRIMARY KEY,
  TeamName VARCHAR(255) NOT NULL,
  HomeTeamShotsOnTarget INT,
  HomeTeamShots INT,
  HomeTeamCorners INT,
  HomeTeamFouls INT,
  HomeTeamYellowCards INT,
  HomeTeamRedCards INT,
  HalfTimeHomeTeamGoals INT,
  FullTimeHomeTeamGoals INT
);


CREATE TABLE dimReferee (
  RefereelD INT PRIMARY KEY,
  RefereeName VARCHAR(255) NOT NULL
);

CREATE TABLE dimContinent (
  ContinentID INT PRIMARY KEY,
  ContinentName VARCHAR(255) NOT NULL
);

CREATE TABLE dimCountry (
  CountryID INT PRIMARY KEY,
  CountryCode VARCHAR(255) NOT NULL,
  CountryName VARCHAR(255) NOT NULL,
  ContinentID INT,
  CountryCapital VARCHAR(255),
  FOREIGN KEY (ContinentID) REFERENCES dimContinent(ContinentID)
);

CREATE TABLE dimCity (
  CityID INT PRIMARY KEY,
  CityName VARCHAR(255) NOT NULL,
  CountryID INT,
  FOREIGN KEY (CountryID) REFERENCES dimCountry(CountryID)
);

CREATE TABLE dimStadium (
  StadiumiD INT PRIMARY KEY,
  StadiumName VARCHAR(255) NOT NULL,
  CityID INT,
  FOREIGN KEY (CityID) REFERENCES dimCity(CityID)
);

CREATE TABLE dimMatchDate (
  MatchDateID INT PRIMARY KEY,
  FullDate DATE NOT NULL,
  MacthDay INT NOT NULL,
  MatchMonth INT NOT NULL,
  MatchYear INT NOT NULL
);


CREATE TABLE dimFullTimeResult (
  ResultID INT PRIMARY KEY,
  FullTimeResult VARCHAR(250) NOT NULL,
  Descript VARCHAR(255) NOT NULL
);


CREATE TABLE dimWeather (
  WeatherID INT PRIMARY KEY,
  Temperature INT,
  WinSpeed FLOAT,
  Humidity INT
);

CREATE TABLE dimSeason (
  SeasonID INT PRIMARY KEY,
  SeasonName VARCHAR(255) NOT NULL
);

CREATE TABLE dimMatchTime (
  MatchTimeID INT PRIMARY KEY,
  MatchTime VARCHAR(255) NOT NULL
);

CREATE TABLE factMatch (
  MatchID INT PRIMARY KEY,
  SeasonID INT,
  MatchDateID INT,
  MatchTimeID INT,
  HomeTeamID INT,
  AwayTeamID INT,
  RefereelD INT,
  StadiumiD INT,
  MatchResultID INT,
  MatchDuration INT,
  MactchResultDesc NVARCHAR(255),
  Attendance INT,
  WeatherID INT,
  FOREIGN KEY (SeasonID) REFERENCES dimSeason(SeasonID),
  FOREIGN KEY (MatchDateID) REFERENCES dimMatchDate(MatchDateID),
  FOREIGN KEY (MatchTimeID) REFERENCES dimMatchTime(MatchTimeID),
  FOREIGN KEY (HomeTeamID) REFERENCES dimHomeTeam(TeamID),
  FOREIGN KEY (AwayTeamID) REFERENCES dimAwayTeam(TeamID),
  FOREIGN KEY (RefereelD) REFERENCES dimReferee(RefereelD),
  FOREIGN KEY (StadiumiD) REFERENCES dimStadium(StadiumiD),
  FOREIGN KEY (MatchResultID) REFERENCES dimFullTimeResult(ResultID),
  FOREIGN KEY (WeatherID) REFERENCES dimWeather(WeatherID)
);