# SQLBolt Solutions by Jaya Laxmi

---

## Lesson 1: SELECT Queries 101

**🔹 Find the title of each film**
```sql
SELECT title FROM movies;
```

**🔹 Find the director of each film**
```sql
SELECT director FROM movies;
```

**🔹 Find the title and director of each film**
```sql
SELECT title, director FROM movies;
```

**🔹 Find the title and year of each film**
```sql
SELECT title, year FROM movies;
```

**🔹 Find all the information about each film**
```sql
SELECT * FROM movies;
```

---

## Lesson 2: Queries with Constraints (Pt. 1)

**🔹 Find the movie with a row id of 6**
```sql
SELECT * FROM movies
WHERE Id=6;
```

**🔹 Find the movies released in the years between 2000 and 2010**
```sql
SELECT * FROM movies
WHERE year BETWEEN 2000 AND 2010;
```

**🔹 Find the movies not released in the years between 2000 and 2010**
```sql
SELECT * FROM movies
WHERE year NOT BETWEEN 2000 AND 2010;
```

**🔹 Find the first 5 Pixar movies and their release year**
```sql
SELECT * FROM movies
ORDER BY year
LIMIT 5;
```

---

## Lesson 3: Queries with Constraints (Pt. 2)

**🔹 Find all the Toy Story movies**
```sql
SELECT * FROM movies
WHERE title LIKE '%Toy%';
```

**🔹 Find all the movies directed by John Lasseter**
```sql
SELECT * FROM movies
WHERE director = 'John Lasseter';
```

**🔹 Find all the movies (and director) not directed by John Lasseter**
```sql
SELECT title, director FROM movies
WHERE director != 'John Lasseter';
```

**🔹 Find all the WALL-* movies**
```sql
SELECT * FROM movies
WHERE title LIKE 'WALL-_';
```

---

## Lesson 4: Filtering and Sorting Query Results

**🔹 List all directors of Pixar movies (alphabetically), without duplicates**
```sql
SELECT DISTINCT director FROM movies
ORDER BY director;
```

**🔹 List the last four Pixar movies released (most recent to least)**
```sql
SELECT * FROM movies
ORDER BY year DESC
LIMIT 4;
```

**🔹 List the first five Pixar movies sorted alphabetically**
```sql
SELECT * FROM movies
ORDER BY title ASC
LIMIT 5;
```

**🔹 List the next five Pixar movies sorted alphabetically**
```sql
SELECT * FROM movies
ORDER BY title ASC
LIMIT 5 OFFSET 5;
```

---

## Review 1: Simple SELECT Queries

**🔹 List all the Canadian cities and their populations**
```sql
SELECT city, population FROM north_american_cities
WHERE country = 'Canada';
```

**🔹 Order all U.S. cities by latitude (north to south)**
```sql
SELECT * FROM north_american_cities
WHERE country = 'United States'
ORDER BY latitude DESC;
```

**🔹 List all cities west of Chicago, ordered west to east**
```sql
SELECT * FROM north_american_cities
WHERE longitude < -87.6298
ORDER BY longitude;
```

**🔹 List the two largest cities in Mexico (by population)**
```sql
SELECT * FROM north_american_cities
WHERE country = 'Mexico'
ORDER BY population DESC
LIMIT 2;
```

**🔹 List the third and fourth largest U.S. cities (by population)**
```sql
SELECT * FROM north_american_cities
WHERE country = 'United States'
ORDER BY population DESC
LIMIT 2 OFFSET 2;
```

---

## Lesson 6: Multi-table Queries with JOINs

**🔹 Find domestic and international sales for each movie**
```sql
SELECT * FROM movies AS M
JOIN boxoffice AS B
WHERE B.movie_id = M.id;
```

**🔹 Show movies that did better internationally than domestically**
```sql
SELECT title, domestic_sales, international_sales
FROM movies AS M
INNER JOIN boxoffice AS B
ON B.movie_id = M.id
WHERE B.domestic_sales < B.international_sales;
```

**🔹 List all movies by their ratings in descending order**
```sql
SELECT *
FROM movies AS M
INNER JOIN boxoffice AS B
ON B.movie_id = M.id
ORDER BY B.rating DESC;
```

---

## Lesson 7: OUTER JOINs

**🔹 List all buildings that have employees**
```sql
SELECT DISTINCT building FROM employees;
```

**🔹 List all buildings and their capacity**
```sql
SELECT * FROM buildings;
```

**🔹 List all buildings and roles of employees (including empty buildings)**
```sql
SELECT DISTINCT building_name, E.role FROM buildings AS B
LEFT JOIN employees AS E 
ON B.building_name = E.building;
```

---

## Lesson 8: A Short Note on NULLs

**🔹 Find employees without building assignments**
```sql
SELECT role, name FROM employees
WHERE building IS NULL;
```

**🔹 Find buildings that have no employees**
```sql
SELECT building_name FROM buildings AS B
LEFT JOIN employees AS E
ON B.building_name = E.building
WHERE E.building IS NULL;
```

---

## Lesson 9: Queries with Expressions

**🔹 List all movies and their combined sales (in millions)**
```sql
SELECT M.title, (B.domestic_sales + B.international_sales)/1000000 AS total_sales
FROM movies AS M
INNER JOIN boxoffice AS B
ON B.movie_id = M.id;
```

**🔹 List all movies and their ratings in percent**
```sql
SELECT M.title, B.rating * 10 AS ratinginper
FROM movies AS M
INNER JOIN boxoffice AS B
ON B.movie_id = M.id;
```

**🔹 List all movies released in even-numbered years**
```sql
SELECT * 
FROM movies
WHERE year % 2 = 0;
```

---

✅ *End of Solutions – More Lessons Coming Soon!*
