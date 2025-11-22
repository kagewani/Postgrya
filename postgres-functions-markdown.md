# PostgreSQL Functions Guide

## What is a Function?

A **function** in PostgreSQL is a reusable block of code that performs a specific task and returns a value. Functions accept input parameters (called arguments), process them according to their defined logic, and return a result. They are fundamental building blocks in SQL that allow you to:

- Perform calculations and transformations on data
- Manipulate strings, dates, numbers, and other data types
- Aggregate multiple rows of data into summary values
- Apply conditional logic within queries
- Convert between different data types

Functions can be **built-in** (provided by PostgreSQL) or **user-defined** (created by developers). Built-in functions are optimized, well-tested operations that handle common database tasks efficiently. You use functions in SELECT statements, WHERE clauses, JOIN conditions, and virtually any part of a SQL query where you need to transform or evaluate data.

**Syntax Example:**
```sql
SELECT UPPER(first_name), LENGTH(last_name), NOW()
FROM users
WHERE AGE(birth_date) > INTERVAL '18 years';
```

---

## Aggregate Functions

Aggregate functions perform calculations on a set of values and return a single result. They're commonly used with GROUP BY clauses.

- **COUNT()** - Returns the number of rows that match a specified condition
- **SUM()** - Calculates the sum of a set of numeric values
- **AVG()** - Calculates the average value of a numeric column
- **MIN()** - Returns the minimum value in a set of values
- **MAX()** - Returns the maximum value in a set of values
- **STRING_AGG()** - Concatenates values from multiple rows into a single string with a delimiter
- **ARRAY_AGG()** - Collects all input values into an array
- **JSON_AGG()** - Aggregates values as a JSON array
- **JSONB_AGG()** - Aggregates values as a JSONB array (binary JSON, more efficient)

---

## String Functions

String functions manipulate and analyze text data.

- **CONCAT()** - Concatenates two or more strings together
- **CONCAT_WS()** - Concatenates strings with a separator
- **SUBSTRING()** - Extracts a substring from a string (also SUBSTR)
- **LENGTH()** - Returns the number of characters in a string
- **CHAR_LENGTH()** - Returns the number of characters (alternative to LENGTH)
- **UPPER()** - Converts a string to uppercase
- **LOWER()** - Converts a string to lowercase
- **INITCAP()** - Capitalizes the first letter of each word
- **TRIM()** - Removes leading and trailing spaces (or specified characters)
- **LTRIM()** - Removes leading spaces
- **RTRIM()** - Removes trailing spaces
- **REPLACE()** - Replaces all occurrences of a substring within a string
- **SPLIT_PART()** - Splits a string on a delimiter and returns the specified field
- **POSITION()** - Returns the position of a substring within a string
- **STRPOS()** - Alternative to POSITION for finding substring position
- **LEFT()** - Returns the leftmost N characters from a string
- **RIGHT()** - Returns the rightmost N characters from a string
- **LPAD()** - Pads a string on the left to a specified length
- **RPAD()** - Pads a string on the right to a specified length
- **REPEAT()** - Repeats a string a specified number of times
- **REVERSE()** - Reverses the characters in a string

---

## Date/Time Functions

Date and time functions handle temporal data manipulation and calculations.

- **NOW()** - Returns the current date and time with timezone
- **CURRENT_DATE** - Returns the current date (no time component)
- **CURRENT_TIME** - Returns the current time with timezone
- **CURRENT_TIMESTAMP** - Returns the current date and time with timezone
- **DATE_TRUNC()** - Truncates a timestamp to specified precision (second, minute, hour, day, week, month, quarter, year)
- **EXTRACT()** - Extracts a specific part from a date/time value (year, month, day, hour, etc.)
- **DATE_PART()** - Similar to EXTRACT, extracts date/time component
- **AGE()** - Calculates the difference between two timestamps or between a timestamp and current date
- **TO_CHAR()** - Converts a timestamp/date to a string with specified format
- **TO_DATE()** - Converts a string to a date value
- **TO_TIMESTAMP()** - Converts a string to a timestamp
- **INTERVAL** - Represents a time span (e.g., INTERVAL '1 day', '2 hours', '3 months')
- **MAKE_DATE()** - Creates a date from year, month, and day integers
- **MAKE_TIME()** - Creates a time from hour, minute, and second values
- **MAKE_TIMESTAMP()** - Creates a timestamp from individual components

---

## Mathematical Functions

Mathematical functions perform numeric calculations and transformations.

- **ROUND()** - Rounds a number to a specified number of decimal places
- **CEIL() / CEILING()** - Rounds a number up to the nearest integer
- **FLOOR()** - Rounds a number down to the nearest integer
- **ABS()** - Returns the absolute value of a number
- **POWER()** - Raises a number to the power of another number
- **SQRT()** - Returns the square root of a number
- **MOD()** - Returns the remainder of a division operation
- **RANDOM()** - Returns a random number between 0 and 1
- **TRUNC()** - Truncates a number to a specified number of decimal places
- **SIGN()** - Returns the sign of a number (-1, 0, or 1)
- **EXP()** - Returns e raised to the power of a number
- **LN()** - Returns the natural logarithm of a number
- **LOG()** - Returns the base-10 logarithm or logarithm of specified base
- **PI()** - Returns the value of π
- **DEGREES()** - Converts radians to degrees
- **RADIANS()** - Converts degrees to radians
- **SIN(), COS(), TAN()** - Trigonometric functions

---

## Conditional Functions

Conditional functions provide logic and decision-making capabilities within queries.

- **COALESCE()** - Returns the first non-null value in a list of arguments
- **NULLIF()** - Returns null if two expressions are equal, otherwise returns the first expression
- **CASE WHEN** - Provides conditional logic (if-then-else) within SQL queries
- **GREATEST()** - Returns the largest value from a list of expressions
- **LEAST()** - Returns the smallest value from a list of expressions

---

## Window Functions

Window functions perform calculations across a set of rows related to the current row, without collapsing the result set.

- **ROW_NUMBER()** - Assigns a unique sequential number to each row within a partition
- **RANK()** - Assigns a rank to each row with gaps for ties (1, 2, 2, 4...)
- **DENSE_RANK()** - Assigns a rank to each row without gaps for ties (1, 2, 2, 3...)
- **NTILE()** - Divides rows into a specified number of roughly equal groups
- **LAG()** - Accesses data from a previous row in the same result set
- **LEAD()** - Accesses data from a following row in the same result set
- **FIRST_VALUE()** - Returns the first value in an ordered partition
- **LAST_VALUE()** - Returns the last value in an ordered partition
- **NTH_VALUE()** - Returns the nth value in an ordered partition
- **PERCENT_RANK()** - Returns the relative rank of a row (0 to 1)
- **CUME_DIST()** - Returns the cumulative distribution of a value

---

## JSON/JSONB Functions

Functions for working with JSON data types (JSON is text-based, JSONB is binary and more efficient).

- **JSON_BUILD_OBJECT()** - Creates a JSON object from key-value pairs
- **JSON_BUILD_ARRAY()** - Creates a JSON array from values
- **JSONB_BUILD_OBJECT()** - Creates a JSONB object from key-value pairs
- **JSONB_BUILD_ARRAY()** - Creates a JSONB array from values
- **JSON_EXTRACT_PATH()** - Extracts a value from JSON using a path
- **JSONB_EXTRACT_PATH()** - Extracts a value from JSONB using a path
- **JSON_ARRAY_ELEMENTS()** - Expands a JSON array into a set of rows
- **JSONB_ARRAY_ELEMENTS()** - Expands a JSONB array into a set of rows
- **JSON_OBJECT_KEYS()** - Returns set of keys in a JSON object
- **JSONB_SET()** - Updates or inserts a value in a JSONB structure
- **JSON_AGG()** - Aggregates values into a JSON array
- **JSONB_AGG()** - Aggregates values into a JSONB array
- **JSON_TO_RECORD()** - Converts a JSON object to a PostgreSQL record
- **ROW_TO_JSON()** - Converts a row to a JSON object

---

## Array Functions

Functions for manipulating PostgreSQL array data types.

- **ARRAY_LENGTH()** - Returns the length of an array dimension
- **ARRAY_APPEND()** - Appends an element to the end of an array
- **ARRAY_PREPEND()** - Adds an element to the beginning of an array
- **ARRAY_REMOVE()** - Removes all elements equal to a specified value from an array
- **ARRAY_REPLACE()** - Replaces all occurrences of a value in an array
- **ARRAY_CAT()** - Concatenates two arrays
- **ARRAY_POSITION()** - Returns the position of an element in an array
- **ARRAY_POSITIONS()** - Returns all positions of an element in an array
- **UNNEST()** - Expands an array into a set of rows
- **ARRAY_AGG()** - Aggregates values into an array
- **ARRAY_TO_STRING()** - Converts an array to a string with delimiter
- **STRING_TO_ARRAY()** - Converts a string to an array using delimiter

---

## Type Conversion Functions

Functions for converting values between different data types.

- **CAST()** - Converts a value from one data type to another (standard SQL syntax)
- **:: operator** - PostgreSQL shorthand for casting (e.g., '123'::integer)
- **TO_CHAR()** - Converts a value to a string with formatting options
- **TO_NUMBER()** - Converts a string to a numeric value
- **TO_DATE()** - Converts a string to a date
- **TO_TIMESTAMP()** - Converts a string to a timestamp
- **TO_JSON()** - Converts a value to JSON
- **TO_JSONB()** - Converts a value to JSONB

---

## Pattern Matching

Operators and functions for matching text patterns.

- **LIKE** - Pattern matching with % (any characters) and _ (single character)
- **ILIKE** - Case-insensitive LIKE pattern matching
- **NOT LIKE** - Negation of LIKE
- **SIMILAR TO** - Pattern matching using SQL regular expressions
- **~ (tilde)** - Case-sensitive POSIX regular expression matching
- **~\*** - Case-insensitive POSIX regular expression matching
- **!~** - Case-sensitive regular expression not matching
- **!~\*** - Case-insensitive regular expression not matching
- **REGEXP_MATCH()** - Captures substrings matching a regular expression
- **REGEXP_MATCHES()** - Returns all matches of a regular expression
- **REGEXP_REPLACE()** - Replaces substrings matching a regular expression
- **REGEXP_SPLIT_TO_ARRAY()** - Splits a string using a regex delimiter
- **REGEXP_SPLIT_TO_TABLE()** - Splits a string using a regex delimiter into rows

---

## System Information Functions

Functions that provide information about the database system.

- **VERSION()** - Returns PostgreSQL version information
- **CURRENT_USER** - Returns the current user name
- **CURRENT_DATABASE()** - Returns the name of the current database
- **CURRENT_SCHEMA()** - Returns the current schema name
- **PG_BACKEND_PID()** - Returns the process ID of the current server process
- **PG_DATABASE_SIZE()** - Returns the disk space used by a database
- **PG_TABLE_SIZE()** - Returns the disk space used by a table
- **PG_TOTAL_RELATION_SIZE()** - Returns total disk space used by a table including indexes

---

## Other Useful Functions

Additional commonly used functions that don't fit neatly into other categories.

- **GENERATE_SERIES()** - Generates a series of values from start to stop
- **UNNEST()** - Expands arrays or multiple arrays into rows
- **MD5()** - Calculates MD5 hash of a string
- **ENCODE() / DECODE()** - Encodes/decodes binary data to/from text
- **GEN_RANDOM_UUID()** - Generates a random UUID (requires pgcrypto extension)
- **PG_SLEEP()** - Delays execution for a specified number of seconds
- **JUSTIFY_DAYS()** - Adjusts interval to 30-day months
- **JUSTIFY_HOURS()** - Adjusts interval to 24-hour days
- **MAKE_INTERVAL()** - Creates an interval from components