<h1 style="color:green">This is a green heading</h1>
<p style="color:blue">This is a blue paragraph</p>


## there is no doubt you are a movie enthusiast .and some times you face the problem of deciding which movie you would to watch at a given time ,my database is going to put that to an end.because you will be able to check the ratings, directors,reviews etc, of any movie and decide on which to watch.

## TABLE CREATION

* ### codes to create table movies
  
  CREATE TABLE movies (
    movie_id NUMBER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
    title VARCHAR2(255) NOT NULL,
    director VARCHAR2(255),
    release_year NUMBER,
    genre VARCHAR2(100),
    rating NUMBER CHECK (rating BETWEEN 0 AND 10),
    description VARCHAR2(4000)
);

* ### codes to create table directors

  CREATE TABLE Directors (
    DirectorID INT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL,
    BirthYear INT
);

* ### codes to create  table genres

  CREATE TABLE Genres (
    GenreID INT PRIMARY KEY,
    GenreName VARCHAR(100) NOT NULL
);

* ### codes to create  table reviews

  CREATE TABLE Reviews (
    ReviewID INT PRIMARY KEY,
    MovieID INT,
    ReviewerName VARCHAR(255) NOT NULL,
    ReviewText VARCHAR(4000),  -- Specify a length for VARCHAR
    Rating FLOAT CHECK (Rating >= 0 AND Rating <= 10),
    ReviewDate DATE,
    FOREIGN KEY (MovieID) REFERENCES Movies(MovieID)
);

* ### adding foreign keys

ALTER TABLE MOVIES ADD FOREIGN KEY (DirectorID)REFERENCES Directors(DirectorID);

ALTER TABLE MOVIES ADD FOREIGN KEY (GenreID)REFERENCES Genres(GenreID);



## INSERTION OF DATA IN TABLES


* ### inserting data in table movies

INSERT INTO movies values(1,'freinds',1,1,1990);

INSERT INTO movies values(2,'young sheldon',2,2,1995);

INSERT INTO movies values(3,'stranger things',3,3,1998);

INSERT INTO movies values(4,'the notebook',4,4,1999);


* ### inserting data in table directors
  

INSERT into directors values(1,'delphine',1950);

INSERT into directors values(2,'ezra',1948);

INSERT into directors values(3,'jean valentin',1943);

INSERT into directors values(4,'magnfique',1930);


* ### inserting data in table genres
  

INSERT into Genres values(1,'comedy');

INSERT INTO genres values(2,'comedy');

INSERT into genres values(3,'thriller');

INSERT INTO genres values(4,'romantic');


* ### inserting data into table reviews
  

INSERT INTO reviews values(1,3,'chazzy','marvelous',9.0,TO_DATE('10-28-1998','MM-DD-YYYY'));

INSERT INTO reviews values(2,1,'gashumba','sooo good',9.3, TO_DATE('11-30-1991','MM-DD-YYYY')); 

INSERT INTO reviews values(3,2,'egide','lots of laughter',10,TO_DATE('09-05-1996','MM-DD-YYYY'));

INSERT INTO reviews values(4,4,'brian','crying rn',9,TO_DATE('08-05-2000','MM-DD-YYYY'));


## QUERIES

* ### the below query retrieves all the data from any table 

select*from movies;

select*from reviews;

select*from genres;

select*from directors;


* ### the below  query can update a certain record

update reviews
set rating=9.7
where movieid=2;

* ### the An INNER JOIN in SQL is used to combine rows from two or more tables based on a related column between them. It returns only the rows where there is a match in both tables.

SELECT Movies.Title, Directors.Name AS Director
FROM Movies
JOIN Directors ON Movies.DirectorID = Directors.DirectorID;

* ### A LEFT JOIN (or LEFT OUTER JOIN) in SQL is used to combine rows from two tables, returning all rows from the left table and the matched rows from the right table. If there are no matches, the result will still include the rows from the left table, but with NULL values for columns from the right table.

SELECT Movies.Title, Reviews.ReviewerName, Reviews.Rating
FROM Movies
LEFT JOIN Reviews ON Movies.MovieID = Reviews.MovieID;;


* ### the below query is used to  retrieve data on a certain condition 

select*from reviews 
where rating<=10;


* ## conceptual diagram

<img width="699" alt="conceptual diagram" src="https://github.com/user-attachments/assets/dd45ac19-c844-4bc8-942e-e210938c97a0">













  

