## L37: Introduction to SQL joins
1. Theory  
1.1. What is left join  
1.2. What is left anti join  
1.3. How inner join works  
2. Practice  
2.1. LEFT JOIN  
2.2. GROUP BY  
2.3. COUNT Pets and GROUP BY Owners.City  
2.4. Doing anti JOIN queries  
2.5. Calculate the amount of sales by Procedure Type  
--------
**JOINS** --> to combine two tables together. 

key - unique (transaction id)
primary/foreign key - client id (common attribute for both tables)

**LEFT JOIN** - add data from first to second table.  

**LEFT ANTI JOIN** - will find transactions that do not match  

**RIGHT JOIN** - Returns all rows from the right table and the matched rows from the left table. If there's no match, the result is NULL on the side of the left table.  

**INNER JOIN** - if client_id is in both, we include this row. New table. Match has to be in both tables.   

E.g food delivery application. After 3 months you want to know all transactions of your client or group transaction amounts together / orders from different cities.

https://www.sqlitetutorial.net/sqlite-join/

![08-22-SQL JOINS](https://github.com/user-attachments/assets/b4ef7963-18da-4d1f-a90a-515da7339e38)

```SQL

SELECT Pets.*, Owners.City
FROM Pets LEFT JOIN Owners ON Pets.OwnerID = Owners.OwnerID;

SELECT Pets.Name, Owners.City
FROM Pets LEFT JOIN Owners ON Pets.OwnerID = Owners.OwnerID;

-- Only pets from city Flint

SELECT Pets.Name AS PetName, Owners.Name AS OwnerName, Owners.City 
FROM Pets 
JOIN Owners ON Pets.OwnerID = Owners.OwnerID 
WHERE Owners.City = 'Flint';

SELECT Pets.*, Owners.City 
FROM Pets 
LEFT JOIN Owners 
ON Pets.OwnerID = Owners.OwnerID 
WHERE Owners.City = 'Flint';

-- Table: two columns: Kind and Count. 

SELECT Pets.Kind, COUNT(Pets.Kind) AS KindCoun
FROM Pets 
LEFT JOIN Owners 
ON Pets.OwnerID = Owners.OwnerID 
GROUP BY Pets.Kind

SELECT kind, COUNT(*) AS Count 
FROM Pets 
GROUP BY Kind
ORDER BY Count DESC; -- descending order by count

SELECT Pets.Kind, COUNT(*) AS count
FROM Pets
GROUP BY Kind;

-- Count of Pets by Owner City
-- AS renames the column

SELECT Owners.City, COUNT(Pets.PetID) AS PetCount -- COUNT(*) 
FROM Pets
JOIN Owners ON Pets.OwnerID = Owners.OwnerID
GROUP BY Owners.City
ORDER BY PetCount DESC;


-- All Pets who do not have OwnerID
-- ANTI JOIN!!!

SELECT Pets.Name
FROM Pets
LEFT JOIN Owners ON Pets.OwnerID = Owners.OwnerID
WHERE Owners.OwnerID IS NULL;


-- Owners who do nto have Pets

SELECT Owners.Name AS OwnerName
FROM Owners
LEFT JOIN Pets ON Owners.OwnerID = Pets.OwnerID
WHERE Pets.PetID IS NULL;
```
------
```SQL

-- TASK: Calculate the amount of sales by Procedure Type

SELECT Procedures.ProcedureType, SUM(Procedures.Price) AS TotalSales
FROM Sales
JOIN Procedures 
ON Sales.ProcedureCode = Procedures.ProcedureCode
GROUP BY Procedures.ProcedureType;

SELECT Sales.*, SUM(Procedures.Price)
FROM Sales
LEFT JOIN Procedures ON Sales.ProcedureCode = Procedures.ProcedureCode
GROUP BY Sales.ProcedureCode;

SELECT Sales.ProcedureCode, SUM(Procedures.Price) AS TotalSales
FROM Sales
LEFT JOIN Procedures ON Sales.ProcedureCode = Procedures.ProcedureCode
GROUP BY Sales.ProcedureCode
ORDER BY TotalSales DESC;

-- other options

SELECT Sales.ProcedureCode, SUM(Procedures.Price) AS TotalSales
FROM Sales
LEFT JOIN Procedures ON Sales.ProcedureCode = Procedures.ProcedureCode
GROUP BY Procedures.ProcedureType
ORDER BY TotalSales DESC;

SELECT Sales.ProcedureCode, SUM(Procedures.Price) AS TotalSales
FROM Sales
LEFT JOIN Procedures ON Sales.ProcedureCode = Procedures.ProcedureCode
GROUP BY Procedures.Description
ORDER BY TotalSales DESC;

SELECT Sales.ProcedureCode, SUM(Procedures.Price) AS TotalSales
FROM Sales LEFT JOIN Procedures ON Sales.ProcedureCode = Procedures.ProcedureCode
GROUP BY Sales.ProcedureCode
ORDER BY TotalSales DESC;
```
![group_by_final_ex](https://github.com/user-attachments/assets/dfde50f5-b2b2-41bc-9306-52b47026ec82)

#### TEAMWORK
-------------

-- Calculate total Sales by City  
-- Calculate total Sales by City  
-- Calculate total Sales by Pet Kind  
-- Calculate total Sales by City and Pet Kind  
-- Calculate Average sales by City  
-- If you have additional time, explore relationships with SQLight  

