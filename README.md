```sql
-- Create Country table
CREATE TABLE Country (
    Id INT PRIMARY KEY AUTO_INCREMENT,
    Country_name VARCHAR(100),
    Population INT,
    Area FLOAT
);

-- Create Persons table
CREATE TABLE Persons (
    Id INT PRIMARY KEY AUTO_INCREMENT,
    Fname VARCHAR(100),
    Lname VARCHAR(100),
    Population INT,
    Rating FLOAT,
    Country_Id INT,
    Country_name VARCHAR(100),
    FOREIGN KEY (Country_Id) REFERENCES Country(Id)
);
```
```sql
-- Insert 10 rows into Country table
INSERT INTO Country (Country_name, Population, Area)
VALUES 
    ('USA', 328200000, 9833520),
    ('China', 1439323776, 9596961),
    ('India', 1380004385, 3287263),
    ('Brazil', 212559417, 8515767),
    ('Russia', 145912025, 17098242),
    ('Japan', 126476461, 377975),
    ('Germany', 83124418, 357022),
    ('Egypt', 102334404, 1002450),
    ('Nigeria', 206139589, 923768),
    ('Mexico', 128932753, 1964375);

-- Insert 10 rows into Persons table
INSERT INTO Persons (Fname, Lname, Population, Rating, Country_Id, Country_name)
VALUES 
    ('John', 'Doe', 1000000, 4.5, 1, 'USA'),
    ('Jane', 'Smith', 800000, 4.2, 2, 'China'),
    ('Michael', 'Johnson', 1200000, 4.7, 3, 'India'),
    ('Maria', 'Garcia', 900000, 4.0, 4, 'Brazil'),
    ('Ivan', 'Ivanov', 600000, 3.8, 5, 'Russia'),
    ('Yuki', 'Tanaka', 500000, 4.5, 6, 'Japan'),
    ('Hans', 'Müller', 700000, 4.2, 7, 'Germany'),
    ('Ahmed', 'Ali', 800000, 4.0, 8, 'Egypt'),
    ('Chinedu', 'Okafor', 600000, 4.3, 9, 'Nigeria'),
    ('Luis', 'González', 700000, 4.1, 10, 'Mexico');
```

1. **Print the first three characters of Country_name from the Country table:**
   
   SELECT SUBSTRING(Country_name, 1, 3) AS First_Three_Characters
   FROM Country;
   
2. **Concatenate first name and last name from Persons table:**
   
   SELECT CONCAT(Fname, ' ', Lname) AS Full_Name
   FROM Persons;
   
3. **Count the number of unique country names from Persons table:**
   
   SELECT COUNT(DISTINCT Country_name) AS Unique_Country_Count
   FROM Persons;
   
4. **Print the maximum population from the Country table:**
   
   SELECT MAX(Population) AS Max_Population
   FROM Country;
   
5. **Print the minimum population from Persons table:**
   
   SELECT MIN(Population) AS Min_Population
   FROM Persons;
   
6. **Count occurrences of NULL in Lname after inserting 2 rows with NULL Lname:**
   ```sql
   -- Inserting new rows with NULL Lname
   INSERT INTO Persons (Fname, Lname, Population, Rating, Country_Id, Country_name)
   VALUES ('Anna', NULL, 500000, 4.4, 5, 'Russia'),
          ('Pedro', NULL, 600000, 4.3, 10, 'Mexico');
   
   -- Counting occurrences of NULL in Lname
   SELECT COUNT(*) AS Null_Lname_Count
   FROM Persons
   WHERE Lname IS NULL;
   ```

7. **Find the number of rows in the Persons table:**
   
   SELECT COUNT(*) AS Total_Rows
   FROM Persons;
   
8. **Return the current date and time:**
   
   SELECT NOW() AS Current_DateTime;
   
9. **Show the population of the Country table for the first 3 rows:**
   
   SELECT Id, Country_name, Population
   FROM Country
   LIMIT 3;

10. **Print 3 random rows of countries:**

    SELECT Id, Country_name, Population
    FROM Country
    ORDER BY RAND()
    LIMIT 3;
