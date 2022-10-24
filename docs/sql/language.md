# Structured Query Language

A short overview of most things that you can do in SQL
### Language References

- [SQL Syntax Wiki](https://en.wikipedia.org/wiki/SQL_syntax)
- [W3 School SQL](https://www.w3schools.com/sql/default.asp)
- [Snowflake SQL general reference](https://docs.snowflake.com/en/sql-reference.html)
- [Snowflake SQL command reference](https://docs.snowflake.com/en/sql-reference-commands.html)
- [Snowflake SQL functions reference](https://docs.snowflake.com/en/sql-reference-functions.html)

### Syntax stuff
#### Operators

``` sql title="SQL Operators"
= -- equal to
<> -- not equal to
>, <, <=, >= -- comparisons
BETWEEN -- between a certain range
LIKE --search for a certain pattern
IN -- specify multiple possible values for a col
AND -- and stuff
OR --or stuff
NOT -- not stuff
IS NULL
IS NOT NULL
```

#### Basics

``` sql title="Getting stuff out a table"
SELECT col1, col2, col3, FROM mytab --seleting cols from a table
SELECT DISTINCT ... -- unique values
SELECT ... FROM ... WHERE ... -- has to be in this order

-- filter out stuff based on condition
SELECT ... WHERE mycondition
SELECT ... WHERE cond1 AND  cond2
SELECT ... WHERE cond1 OR  cond2
SELECT ... WHERE NOT cond1

--m combining conditions
SELECT * FROM mytab
WHERE col1="val1" AND (col2="val2" or col2="val3")

-- ordering
SELECT ... ORDER BY col, ASC|DESC
SELECT ... ORDER BY col1 ASC, col2 DESC -- can be done

-- nulls
SELECT ... WHERE col IS NOT NULL
SELECT ... WHERE col IS NULL

-- limit selection: n
SELECT TOP n col1,col2 FROM ... WHERE cond1;
SELECT TOP n PERCENT * FROM col1; --- SQL server syntax

SELECT ... FROM .. WHERE ... LIMIT n; --mysql syntax

```

``` sql title="Adding rows to a table"
INSERT INTO ...

INSERT INTO mytab (co1, col2, col3, ...)
VALUES (val1, val2, val3,...)
```

``` sql title="Changing values in a table"
UPDATE mytab SET col1=val1, col2=val2 WHERE cond1
UPDATE mytab SET col1=val1  -- will change all records, beware
```

``` sql title="Removing values from a table"
DELETE FROM mytab WHERE cond1
DELETE FROM mytab; -- deletes all values but keeps table structure, beware
```

#### Functions 

``` sql title="SQL Functions"
SELECT MIN(col1) FROM ... WHERE ...; --smallest value
SELECT MAX(col1) FROM ... WHERE ...; --biggest value
SELECT COUNT(col1) FROM ... WHERE cond; -- number of rows matching condition
SELECT AVG(col1) FROM ... WHERE ...; -- average value
SELECT SUM(col1) FROM ... WHERE ...; -- sum value
```

#### Pattern matching

```sql title="pattern matching with LIKE"
SELECT ...
FROM ...
WHERE col1 LIKE pattern

-- patterns
LIKE % -- any number of values
LIKE _ -- singular wildcard
LIKE [abc] -- any character in the brackets
LIKE [!abc] -- any character NOT in the brackets
LIKE [a-d] -- any character in this range
LIKE # -- numberic character

LIKE %pa__[!a-c][nm]% -- crazy pattern
```
```sql title="IN and BETWEEN Operator"
SELECT ... FROM ... WHERE col IN (val1, val2)
SELECT ... FROM ... WHERE col IN (SELECT ...)

SELECT ... FROM ... WHERE col BETWEEN val1 AND val2
```

#### Aliases 

```sql title="SQL Aliases - Columns & Tables "
-- Alias Columns
SELECT col1 AS alias1, col2 AS col_alias
FROM mytab

-- Alias Tables
SELECT col1, col2, col3
FROM mytable AS tab_alias

-- check this out
SELECT a.col1, b.col1, c.col1
FROM tab1 AS a, tab2 AS b, tab3 AS c
WHERE a.col=cond AND b.col=cond
```




### Abbreviations
??? abstract "SQL"
    Structured Query Language
??? abstract "RDBMS"
    Relational Database Management System
??? abstract "DQL"
    Data Query Language
??? abstract "DDL"
    Data Definition Language
??? abstract "DCL"
    Data Control Language
??? abstract "DML"
    Data Manipulation Language
??? abstract "ANSI"
    American National Standards Institute
??? abstract "ISO"
    International Organization for Standardization


### Concepts

??? note "Types of SQL statements (sublanguages)?"
    - DQL
    - DDL
    - DCL
    - DML

??? note "Which language elements does SQL have?"
      1. Clause
      2. Expressions
      3. Predicates
      4. Queries
      5. Statements
      6. Insignificant Whitespaces
        <figure markdown>
        ![SQL language elements](../assets/a2de4ab06da2ded13e608b35b6e191b664b05560.svg){ width="500" }
        <figcaption>SQL Language Elements</figcaption>
        </figure>

