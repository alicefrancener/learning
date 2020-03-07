# Formatting your queries
- [Formatting your queries](#formatting-your-queries)
  - [Capitalization](#capitalization)
  - [Avoid spaces in table and variable names](#avoid-spaces-in-table-and-variable-names)
  - [Use white space in queries](#use-white-space-in-queries)
  - [SQL isn't case sensitive](#sql-isnt-case-sensitive)
  - [Semicolons](#semicolons)

## Capitalization

You may have noticed that we have been capitalizing SELECT and FROM, while we leave table and column names lowercase. This is a common formatting convention. It is common practice to capitalize commands (SELECT, FROM), and keep everything else in your query lowercase. This makes queries easier to read, which will matter more as you write more complex queries. For now, it is just a good habit to start getting into.

## Avoid spaces in table and variable names

It is common to use underscores and avoid spaces in column names. It is a bit annoying to work with spaces in SQL. In Postgres if you have spaces in column or table names, you need to refer to these columns/tables with double quotes around them (Ex: FROM "Table Name" as opposed to FROM table_name). In other environments, you might see this as square brackets instead (Ex: FROM [Table Name]).

## Use white space in queries

SQL queries ignore spaces, so you can add as many spaces and blank lines between code as you want, and the queries are the same. This query

```sql
 SELECT account_id FROM orders
```

is equivalent to this query:

```sql
SELECT account_id
FROM orders
```

and this query (but please don't ever write queries like this):

```sql
SELECT              account_id

FROM               orders
```

## SQL isn't case sensitive

If you have programmed in other languages, you might be familiar with programming languages that get very upset if you do not type the correct characters in terms of lower and uppercase. SQL is not case sensitive. The following query:

```sql
SELECT account_id
FROM orders
```

is the same as:

```sql
select account_id
from orders
```

which is also the same as:

```sql
SeLeCt AcCoUnt_id
FrOm oRdErS
```

However, I would again urge you to follow the conventions outlined earlier in terms of fully capitalizing the commands, while leaving other pieces of your code in lowercase.

## Semicolons

Depending on your SQL environment, your query may need a semicolon at the end to execute. Other environments are more flexible in terms of this being a "requirement." It is considered best practices to put a semicolon at the end of each statement, which also allows you to run multiple commands at once if your environment is able to show multiple results at once.

---

Material do curso ["SQL for Data Analysis"](https://classroom.udacity.com/courses/ud198) da [Udacity](https://www.udacity.com/).
