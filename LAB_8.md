## 8.1 Practice Lab 1

	CREATE TABLE member (
	ID INT UNSIGNED,
	FirstName VARCHAR(100),
	MiddleInitial CHAR(1),
	LastName VARCHAR(100),
	DateOfBirth DATE,
	AnnualPledge DECIMAL(8,2) UNSIGNED
	)
	
## 8.2 Practice Lab 2

	CREATE TABLE movie (
	   Title VARCHAR (30),
	   RatingCode VARCHAR(5),
	   FOREIGN KEY (RatingCode) REFERENCES Rating(RatingCode)
	);
	
	
## 8.3 Practice Lab 3

	ALTER TABLE Movie
	ADD Score DECIMAL(3,1);

## 8.4 Practice Lab 4

	CREATE VIEW MyMovies
	AS SELECT Title, Genre, Year
	FROM Movie;
	
## 8.5 Practice Lab 5

	DROP VIEW MovieView;
	
## 8.6 Practice Lab 6

	ALTER TABLE Movie
	CHANGE ID ID INTEGER PRIMARY KEY;
	
## 8.7 Practice Lab 7

	ALTER TABLE Movie
	ADD FOREIGN KEY(Year) REFERENCES YearStats(Year);
	
## 8.8 Practice Lab 8

	CREATE INDEX idx_year ON Movie (Year);
	
## 8.9 Practice Lab 9

	INSERT INTO Movie (Title,Genre,RatingCode, Year) VALUES ('Pride and Prejudice','Romance','G',2005);
	
## 	8.10 Practice Lab 10

	DELETE FROM Movie
	WHERE ID = 3;
	
## 8.11 Practice Lab 11

	UPDATE Movie
	SET Year = 2022
	WHERE Year = 2020;

## 8.12 Practice Lab 12

	SELECT * FROM Movie;
	
## 8.13 Practice Lab 13

	SELECT Title, Genre
	FROM Movie
	WHERE Year = 2020;
	

## 8.14 Practice Lab 14

	SELECT Title
	FROM Movie
	ORDER BY Title;
	
## 8.15 Practice Lab 15

	SELECT RatingCode, COUNT(RatingCode) AS RatingCodeCount
	FROM Movie
	GROUP BY RatingCode
	ORDER BY RatingCode;
	
## 8.16.1: Practice Lab 16

	SELECT Title, TotalGross
	From Movie
	LEFT JOIN YearStats
	ON Movie.Year = YearStats.Year;
	
## 8.17 Practice Lab 17

	SELECT COUNT(*) Movies_in_2019
	FROM Movie
	WHERE Year=2019;