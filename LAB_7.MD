## 7.1 LAB - Alter Movie table

	CREATE TABLE Movie (
	 ID INT UNSIGNED,
	 Title VARCHAR(50),
	 Genre VARCHAR(50),
	 RatingCode VARCHAR(5),
	 Year INTEGER 
	);

	/*1*/
	ALTER TABLE Movie
	ADD Producer VARCHAR(50);
	/*2*/
	ALTER TABLE Movie DROP Genre;
	/*3*/
	ALTER TABLE Movie CHANGE Year ReleaseYear SMALLINT;
	
	
## 	7.2 LAB - Insert rows into Horse table

	INSERT INTO Horse (RegisteredName, Breed, Height, BirthDate) 
	VALUES ('Babe','Quarter Horse', 15.3 ,'2015-02-10'),
		   ('Independence','Holsteiner', 16.0,'2017-03-13'),
		   ('Ellie','Saddlebred', 15.0, '2016-12-22'),
		   (NULL,'Egyptian Arab'


## 7.3 LAB - Update rows in Horse table

	UPDATE horse
	SET Height=15.6
	WHERE ID=2;

	UPDATE horse
	SET RegisteredName = 'Lady Luck', BirthDate = '2015-05-01'
	WHERE ID=4;

	UPDATE horse
	SET Breed=NULL
	WHERE BirthDate>="2016-12-22"
	
## 7.4 LAB - Delete rows from Horse table

	DELETE FROM horse
	WHERE ID = 5;

	DELETE FROM horse
	WHERE Breed IN ('Holsteiner','Paint');

	DELETE FROM Horse
	WHERE BirthDate < '2013-03-13';
	
## 7.5 LAB - Select horses with logical operators

	SELECT RegisteredName, Height, BirthDate
	FROM Horse
	WHERE (Height BETWEEN 15.0 AND 16.0) OR
	   (BirthDate>='2020-01-01' );
	   
## 	   7.6 LAB - Create Movie table

	CREATE TABLE movie (
		ID SMALLINT UNSIGNED,
		Title VARCHAR(50),
		Rating CHAR(4),
		ReleaseDate DATE,
		Budget DECIMAL (8,2)
	);
	
## 7.7 LAB - Create Student table with constraints

	CREATE TABLE Student (
		ID SMALLINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
		FirstName VARCHAR (20 ) NOT NULL,
		LastName VARCHAR (30) NOT NULL,
		Street VARCHAR(50) NOT NULL,
		City VARCHAR (20) NOT NULL,
		State CHAR(2) NOT NULl DEFAULT "TX",
		Zip MEDIUMINT UNSIGNED NOT NULL,
		Phone CHAR (10) NOT NULL,
		Email VARCHAR(30) UNIQUE
	); 
	
## 7.8 LAB - Create Horse table with constraints

	CREATE TABLE Horse (
		ID SMALLINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
		RegisteredName VARCHAR (15) NOT NULL,
		Breed VARCHAR(20) CHECK ( Breed IN ('Egyptian Arab','Holsteiner','Quarter Horse','Paint', 'Saddlebred')),
		Height DECIMAL (3,1) CHECK  ( Height BETWEEN 10.0 AND 20.0),
		BirthDate DATE CHECK ( BirthDate >='2015-01-01')
	);
	
## 7.9 LAB - Create LessonSchedule table with FK constraints

	CREATE TABLE LessonSchedule (
	   HorseID SMALLINT UNSIGNED NOT NULL,
	   StudentID SMALLINT UNSIGNED,
	   LessonDateTime DATETIME NOT NULL,
	   PRIMARY KEY (HorseID, LessonDateTime),   
	   FOREIGN KEY (HorseID) REFERENCES Horse(ID)
	   ON DELETE CASCADE,
	   FOREIGN KEY (StudentID) REFERENCES Student(ID)
	   ON DELETE SET NULL
	);
	


