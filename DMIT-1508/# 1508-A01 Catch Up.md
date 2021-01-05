# 1508-A01 Catch Up

> ## Announcements
>
> - Quiz Date - Wed Oct 21
> - Lab 2A Released

## Intro - Where we left off

* Created Tables
* Constraints - PK, FK, DF, first CK
* Test Code

> ### Add
> 
> Constraint Prefixes:
> 
> - PK - Primary Key
> - FK - Foreign Key
> - DF - Default
> - CK - Check
> - IX - Indexes
> - UX - Unique


## Check Constraints and Operators

> **CHECK-Constraints.md**

```markdown
# Operations for CHECK Constraints

- Some kind of **comparison** on our column(s) with "acceptable values"

## Arithmetic Operators

- `+`
- `-`
- `*`
- `/`

## Relational Operators

Relational Operators are "binary" operators because they have an "operand" on either side of the operator. For example, in `Cost > 0` the two operands are `Cost` and `0`. Relational operators result in a "boolean" value: `true` or `false`.

Here's another example that involves arithmetic and relational operators:

>>```sql
CHECK(Total = Subtotal + GST)
>>```

- `>`
- `<`
- `=` - is a "comparison" operator - "are they equal?"
- `>=`
- `<=`
- `<>` NOT Equal To (also `!=`)

>>```
<------------------------------>
      |    |    |    |    |
     -2   -1    0    1    2
                |
                 > 0
             `<=0
>>```

## Logical Operators

Logical operators work with the boolean data types/values of `true` and `false`

- `AND` - Binary operator that requires both sides (operands) to be `true` for the final result to be `true`.
- `OR` - Binary operator that requires only one side (operand) to be `true` for the final result to be `true`.
- `NOT` - Unary operator that preceeds one operand and "inverts" the value. A `NOT` in front of a `true` value produces a `false` value, and vice-versa.

## Additional Operations

- `BETWEEN` - Inclusive comparison of a range of values. For example, in `CHECK(Hours BETWEEN 60 AND 120)` the range is inclusive of 60 and 120.
- `IN` - Checks if the value matches one of the values in a comma-separated list of values. For example, `CHECK(Credits IN (3, 4.5, 6))` is the equivalent of writing

  >>```sql
  CHECK(Credits = 3 OR Credits = 4.5 OR Credits = 6)
  >>```

- `LIKE` - Used for "pattern-matching" comparisons on string. Examples of pattern-matching operators and symbols include
  - `%` - Wildcard for zero or more characters
  - `_` - Wildcard for a single character
  - `[]` - A single character matching in the square brackets
    - `[A-Z]` - Any single character from A through Z inclusive
    - `[0-9]` - Any single character from 0 through 9 inclusive
    - `[ABC]` - Either the character `A`, `B`, or `C`
  - An example of matching a phone number:
    ```sql
    CHECK(PhoneNumber LIKE '[1-9][0-9][0-9]-[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]')`
    ```

    - It will match for `'780-222-1515'`
```

> **SchoolTranscript.sql**

**Demo:**

1. **`Courses.Hours`** 60 or 90 or 120

> ***PRACTICE*** - Add the following CHECK constraints (10 minutes)
> 1. **`Courses.Credits`** - Credits can only be 3, 4.5, or 6; use the `IN` operator.
> 1. **`Courses.Number`** - The `Courses.Number` must follow the pattern of "AAAA-####"
> 1. **`StudentCourses.Year`** - The Year must be greater than 2010
> 1. **`Student.Surname`** - Surname must have at least two characters
> 1. **`Student.GivenName`** - GivenName must have at least two characters
> 1. **`StudentCourses.FinalMark`** - FinalMark must be between 0 and 100
> 1. **`StudentCourses.Status`** - Status must be either 'E' for Enrolled, 'W' for Withdrawn, or 'A' for Audited

**Demo:**

1. Test with **BAD** data (to see if check constraints work)
1. **`Courses.Hours`** + **`Courses.Credits`** - Table-level constraint - complex, multi-column checks 

```sql
/* **********************************************/
CREATE TABLE Students -- The default "schema" name is [dbo] - a "schema" is a subset of a database
(
    -- <<<<<<<<<<<>>>>>>>>>>>
    GivenName       varchar(50)
        CONSTRAINT CK_Students_GivenName
            CHECK (GivenName LIKE '[A-Z][A-Z]%') -- Matches 'Dan' or 'Danny'
                                NOT NULL,
    Surname         varchar(50)
        CONSTRAINT CK_Students_Surname
            CHECK (Surname LIKE '__%') -- Not as good as [A-Z][A-Z]%
                                       -- Silly matches: 42
                                NOT NULL,
    DateOfBirth     datetime    NOT NULL,
    Enrolled        bit         NOT NULL
        CONSTRAINT DF_Students_Enrolled DEFAULT (1)
        -- A DEFAULT constraint means that if no data is supplied
        -- for this column, it will automatically use the default value
)

CREATE TABLE Courses
(
    [Number]        varchar(10)
        CONSTRAINT PK_Courses_Number PRIMARY KEY
        CONSTRAINT CK_Courses_Number
            CHECK ([Number] LIKE '[A-Z][A-Z][A-Z][A-Z]-[0-9][0-9][0-9][0-9]')
                                    NOT NULL,
    [Name]          varchar(50)     NOT NULL,
    Credits         decimal(3,1)
        CONSTRAINT CK_Courses_Credits
            CHECK (Credits IN (3, 4.5, 6))
                                    NOT NULL,
    [Hours]         tinyint
        CONSTRAINT CK_Courses_Hours
            CHECK ([Hours] = 60 OR [Hours] = 90 OR [Hours] = 120)
        -- A CHECK constraint will ensure that the value passed in
        -- meets the requirements of the constraint.
                                    NOT NULL,
    Active          bit             NOT NULL,
    Cost            money
        CONSTRAINT CK_Courses_Cost
            CHECK (Cost BETWEEN 400.00 AND 1500.00)
                                    NOT NULL,
    -- Table-level constraints are used for anything involving more than
    -- one column, such as Composite Primary Keys or complex CHECK constraints.
    -- It's a good pattern to put table-level constraints AFTER you have done all the
    -- column definitions.
    CONSTRAINT CK_Courses_Credits_Hours
        CHECK ([Hours] IN (60,90) AND Credits IN (3, 4.5) OR [Hours] = 120 AND Credits = 6)
        --     \       #1       /
        --                            \      #2         /
        --             \          #3           /
        --                                                   \     #4     /
        --                                                                     \    #5    /
        --                                                         \        #6        /
        --                        \                       #7                  /
)

CREATE TABLE StudentCourses
(
    StudentID       int
        CONSTRAINT FK_StudentCourses_Students
            FOREIGN KEY REFERENCES Students(StudentID)
        -- A FOREIGN KEY constraint means that the only values
        -- acceptable for this column must be values that exist
        -- in the referenced table.
                                    NOT NULL,
    CourseNumber    varchar(10)
        CONSTRAINT FK_StudentCourses_Courses -- All constraint names must be unique
            FOREIGN KEY REFERENCES Courses([Number])
                                    NOT NULL,
    [Year]          int
        CONSTRAINT CK_StudentCourses_Year
            CHECK ([Year] > 2010)
            --     NOT [Year] <= 2010
                                    NOT NULL,
    Term            char(3)         NOT NULL,
    FinalMark       tinyint
        CONSTRAINT CK_StudentCourses_FinalMark
            CHECK (FinalMark BETWEEN 0 AND 100)
            --     FinalMark >= 0 AND FinalMark <=100
                                        NULL,
    [Status]        char(1)
        CONSTRAINT CK_StudentCourses_Status
            CHECK ([Status] LIKE '[AWE]')
            --     [Status] = 'A' OR [Status] = 'E' OR [Status] = 'W'
            --     [Status] IN ('A','W','E')
                                    NOT NULL,
    -- Table-Level Constraint - when a constraint involves more than one column
    CONSTRAINT PK_StudentCourses_StudentID_CourseNumber
        PRIMARY KEY (StudentID, CourseNumber)
        -- Composite Primary Key Constraint
)
```

----

## Alter Table + Indexes

```sql
GO -- Finish the table creation as a batch

-- Modifying Database Table Schemas with ALTER TABLE

-- Consider the fact that there may be data in the table
-- that you are trying to alter.
-- If you don't have a default value to apply when
-- adding your new column, then the new column should
-- allow NULL values.
ALTER TABLE Students
   ADD  Email   varchar(30)     NULL

/* Let's see what our table's data/structure looks like
-- Here's a quick'n'dirty way to see all the data

SELECT  *   -- * means "all columns" in my table
FROM    Students

*/
-- If you include a default with your new column,
-- you can make that column as Required (NOT NULL).
ALTER TABLE StudentCourses
    ADD     Paid    bit     NOT NULL
        CONSTRAINT DF_StudentCourses DEFAULT (0)

-- Comment out line(s) of code[Ctrl] + [k], [Ctrl] + [c]
-- SELECT * FROM StudentCourses

ALTER TABLE StudentCourses
    ADD  OverDue    bit     NULL

-- If I just want to add a constraint, such as a default
-- to an existing column (say, my OverDue column),
-- I can adjust the table for only the constraint
ALTER TABLE StudentCourses
    ADD CONSTRAINT DF_StudentCourses_OverDue
        DEFAULT (0) FOR OverDue
-- Also notice above that I have a slightly different
-- syntax for the default constraint:
--  DEFAULT (value) FOR ColumnName
-- Lastly, note that the new constraint will only apply
-- for new rows of data for my DEFAULT constraint.

/*
-- Testing with inserting some data
INSERT INTO StudentCourses(StudentID, CourseNumber, [Year], Term, [Status])
VALUES  (2015, 'DMIT-1508', 2020, 'SEP', 'E')

SELECT * FROM StudentCourses
*/

/* ALTER TABLE Statements - PRACTICE */

-- A) Add column to the Courses table called "SyllabusURL" that is a variable-length string of up to 70 characters. Determine for yourself if it should be NULL or NOT NULL.
-- B) Add a CHECK constraint to the SyllabusURL that will ensure the value matches a website URL (HTTPS://).
-- C) One of the functions that we can use in SQL is the GETDATE() function that will return the current datetime. Use this GETDATE() function as the default value for new column in Students called "EnrolledDate".

GO -- end the batch of statements that alter the database

/* CREATE INDEX */

-- Indexes improve the performance of the database when retrieving information. They do this by providing an additional "lookup" table that is sorted by the the indexed column(s).

-- When we create a table with a PRIMARY KEY, then that/those column(s) are given "clustered" indexes. In other words, the data in the database will (by default) be "sorted by" the Primary Key column(s).

-- We can add additional columns as indexes for quick lookup, but those have to be as "Non-Clustered" indexes.

CREATE NONCLUSTERED INDEX IX_Students_Surname
    ON Students(Surname) -- lookup by last name

-- What should we index in our tables?
--   - Foreign Key Columns
--   - Anything else that will frequently be used as
--     something we either "lookup by" or "sort by"
CREATE NONCLUSTERED INDEX IX_StudentCourses_StudentID
    ON StudentCourses(StudentID)
CREATE NONCLUSTERED INDEX IX_StudentCourses_CourseNumber
    ON StudentCourses(CourseNumber)


/* INDEX Statements - Practice */

-- A) Add an index for the Name column in the Courses table.
-- B) Add an index for the Year column in the StudentCourses table.
```
