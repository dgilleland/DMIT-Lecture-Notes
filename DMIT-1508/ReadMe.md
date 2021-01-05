Good Morning! You are listening to DMIT-1508, your source for Database Design!
[Music]

Welcome to today's episode, where we learn to document our Normalization proof in Markdown and HTML. Let's return to our Workbook and open up the `ESP-1.md` file.

---


## W04D1 

- **Lab 1 Specs** Updated (review requirements)
- **Merging ERDs**
- **ESP 5/6 Review**
- **Lab Time**

---

## W04D2

- ***Lab Time***

---

## W04D3

- Intro to SQL & Data Types
- Install SQL Server

---

## W05D1

- Physical ERDs
- DDL Intro - Grammar
  - Create Database - `SchoolTranscript`
  - Create Table (columns only)
    - `Students`
    - `Courses`
    - `StudentCourses`

---

## W05D2

- DDL
  - Column Definitions
    - Constraints
      - NULL / NOT NULL
      - IDENTITY
      - PRIMARY KEY, Composite PK
      - FOREIGN KEY
      - DEFAULT - `Students.Enrolled -> 1`
      - CHECK - `Courses.Hours -> BETWEEN 60 AND 120`

---

## W05D3

- DDL
  - More Check Constraints
    - Relational Operators
    - Logical Operators - `AND` `OR` `NOT`
    - `BETWEEN`
    - `IN` - `Credits IN (3, 4.5, 6)`
    - `LIKE` and Pattern Matching - `Courses.Number LIKE '[A-Z][A-Z][A-Z][A-Z]-[0-9][0-9][0-9]'`
    - Table-Level Check Constraints
      - 60/90 hrs = 3/4.5 credits OR 120 hrs = 6 credits
- SELECT Statement (SELECT/FROM clauses only)
- Data Inserts
  - Checking our tables (Good Data)
  - Checking our constraints (Bad Data)

---

## W06D1

> Thanksgiving Monday

---

## W06D2

- ALTER TABLE
  - Students
    - Add email NULL
    - Add Paid NOT NULL Default (0)
    - Add OverDue NULL
    - Add Default (0) for OverDue
    - Add EnrolledDate datetime with Default(GetDate()) **(Practice)**
  - Courses **(Practice)**
    - Add URL for SyllabusURL
    - Add CHECK constraint on SyllabusURL

```sql
/* ALTER TABLE Statements - PRACTICE */

-- A) Add column to the Courses table called "SyllabusURL" that is a variable-length string of up to 70 characters. Determine for yourself if it should be NULL or NOT NULL.
-- B) Add a CHECK constraint to the SyllabusURL that will ensure the value matches a website URL (HTTPS://).
-- C) One of the functions that we can use in SQL is the GETDATE() function that will return the current datetime. Use this GETDATE() function as the default value for new column in Students called "EnrolledDate".
```

- INDEXES
  - Foreign Keys
  - Students.Surname
  - StudentCourses.Year **(Practice)**
  - Courses.Name **(Practice)**

```sql
CREATE NONCLUSTERED INDEX IX_Customers_FirstName
    ON Customers (FirstName)

/* INDEX Statements - Practice */

-- A) Add an index for the Name column in the Courses table.
```

## W07-D1

> Flipped classroom - sick day

- `B - Simple Select Exercise.sql`
- `C - Simple Select Exercise.sql`

Thumbs-up if you have finished the practice questions on "B - Simple Select Exercises.sql"

After reviewing the intro to Aggregates, give a reaction of

Thumbs-up if you are comfortable with those functions

Surprised if you are just "kinda" comfortable with those functions

Sad-Face if you have lingering questions or are uncertain about Aggregate functions

----

Given the following ERD, what will the FROM clause be in the following situations (write out the actual FROM clause that you would use in the SELECT statement)?

- I need the names of the students and the clubs.
- 