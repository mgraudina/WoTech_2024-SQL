## L36: Introduction to SQL

1. Theory  
1.1. Differences between front-end and back-end  
1.2. Popular databases and their types  
1.3. SQL vs Document database  
2. Practice  
2.1. Importing data  
2.2. First SQL query  
2.3. Selecting data using SQL queries
----------
BE - Back End (Database part of the BE)  
FE - Front End  
APIs - Transfers data back and force btw BE and FE. Connection btw those.  

![08-21-561zhyyucky71](https://github.com/user-attachments/assets/b2e3af42-34f8-40b6-beac-b54c3d9b4983)

#### TOP DATABASES (STATS) -->>

https://survey.stackoverflow.co/2024/technology/

![image](https://github.com/user-attachments/assets/56759541-09d9-4cb8-86da-e3c53173a95b)

## SQL
-------
**SQL** - is a standard, with different providers.  
**SQL = Structured Query Language**

Thre are many SQL databases because different databases are optimized for different use cases, architectures, and workloads etc.

There are **3 main types of databases**

![08-21-SQL-MongoDB-1rI2Y9wih_6Znc-1dtyz7YQ](https://github.com/user-attachments/assets/260452b1-e315-4a5c-b119-9a965f36e986)

**SQL** - data is organised in tables, tabular format  
**No SQL** (e.g MongoDB) - like JSON, document database

--> Difference: Connections, relationships, flexibility

**ADVANTAGE OF DOCUMENT DATABASE** -->

In SQL, to add new data, we have to create new COLUMN  
In document, we can add just value: "Phone": "12345"  

We want to add new Company (nr of employees, year of reg).  
For SQL we have to create new table in database, connect it to William.  
In document, just create a new object with several data levels.  
If it is embedded data, it is better to go with document.   

Used instead of xls --> Tabloo, PowerBI, AutomatedQueries.   
Avoid xls for automatic calculations, big data, tabulars. Phyton or BI tools are used.

--------
#### SQLite
https://sqliteonline.com/

--> Slightly lighter

*Important when importing data --> Column name == First line*

```SQL

SELECT * FROM Owners; -- * --> all

SELECT Name, Surname FROM Owners; -- selects those columns only

DROP TABLE demo; -- --> deletes fail

```
not good to have spaces  
faster, handle more data

```SQL
SELECT * FROM Pets WHERE Age=11; -- select all data from pets where age is 11

SELECT * FROM Pets WHERE Kind='Dog';

SELECT * FROM Pets WHERE Kind='Dog' AND Age<5;

SELECT PetId, Name FROM Pets WHERE Kind='Dog' AND Age<5;

SELECT * FROM Pets WHERE Name Like '%S%'; -- Name contains S.

SELECT * FROM Pets WHERE Kind = 'Dog' AND Name GLOB '*S*'; -- GLOB - case sensitive

```
#### TEAMWORK
------
Explore different filters and their combinations with SQL  
    Use our Pet clinics files  
    Use online free SQLight platform https://sqliteonline.com/  


