## SQLBolt Lessons (continued)

## Lesson 10: Queries with Aggregates (Pt. 1)

**🔹 Find the longest time that an employee has been at the studio**
```sql
SELECT role, name, building, MAX(years_employed) AS maxyears FROM employees;
```

**🔹 Average years employed per role**
```sql
SELECT role, AVG(years_employed) AS avg_yearsemployed
FROM employees
GROUP BY role;
```

**🔹 Total employee years per building**
```sql
SELECT building, SUM(years_employed) AS total_yearsemployed
FROM employees
GROUP BY building;
```

---

## Lesson 11: Queries with Aggregates (Pt. 2)

**🔹 Number of Artists**
```sql
SELECT COUNT(*) AS number_of_artists
FROM employees
WHERE role = 'Artist';
```

**🔹 Number of employees by role**
```sql
SELECT DISTINCT role, COUNT(role) FROM employees
GROUP BY role;
```

**🔹 Total years employed by Engineers**
```sql
SELECT role, SUM(years_employed) FROM employees
GROUP BY role
HAVING role = 'Engineer';
```

---

## Lesson 12: Order of Execution of a Query

**🔹 Number of movies directed per director**
```sql
SELECT DISTINCT director, COUNT(title) FROM movies
GROUP BY director;
```

**🔹 Total domestic and international sales by director**
```sql
SELECT DISTINCT director, SUM(B.domestic_sales + B.international_sales)
FROM movies AS M
JOIN boxoffice AS B
ON M.id = B.movie_id
GROUP BY director;
```

---

## Lesson 13: Inserting Rows

**🔹 Add Toy Story 4 to movies**
```sql
INSERT INTO movies VALUES
(4, 'Toy Story 4', 'John Lasseter', 2000, 91);
```

**🔹 Add Toy Story 4 to boxoffice**
```sql
INSERT INTO boxoffice VALUES
(4, 8.7, 340000000, 270000000);
```

---

## Lesson 14: Updating Rows

**🔹 Update director for A Bug's Life**
```sql
UPDATE movies
SET director = 'John Lasseter'
WHERE title = 'A Bug\'s Life';
```

**🔹 Correct year for Toy Story 2**
```sql
UPDATE movies
SET year = 1999
WHERE title = 'Toy Story 2';
```

**🔹 Correct title and director for Toy Story 8**
```sql
UPDATE movies
SET title = 'Toy Story 2', director = 'Lee Unkrich'
WHERE title = 'Toy Story 8';
```

---

## Lesson 15: Deleting Rows

**🔹 Remove movies released before 2005**
```sql
DELETE FROM movies
WHERE year < 2005;
```

**🔹 Remove movies directed by Andrew Stanton**
```sql
DELETE FROM movies
WHERE director = 'Andrew Stanton';
```

---

## Lesson 16: Creating Tables

**🔹 Create a new table named Database**
```sql
CREATE TABLE Database (
  Name TEXT,
  Version REAL,
  Download_count INTEGER
);
```

---

## Lesson 17: Altering Tables

**🔹 Add column Aspect_ratio (FLOAT)**
```sql
ALTER TABLE Movies
ADD Aspect_ratio FLOAT;
```

**🔹 Add column Language (TEXT) with default 'English'**
```sql
ALTER TABLE Movies
ADD Language TEXT DEFAULT English;
```

---

## Lesson 18: Dropping Tables

**🔹 Drop Movies table**
```sql
DROP TABLE IF EXISTS Movies;
```

**🔹 Drop BoxOffice table**
```sql
DROP TABLE IF EXISTS Boxoffice;
```

---

✅ *All SQLBolt Lessons Completed!*
