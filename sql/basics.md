# SQL Basics

## SQL statements

- CREATE TABLE is a statement that creates a new table in a database.
- DROP TABLE is a statement that removes a table in a database.
- SELECT allows you to read data and display it. This is called a **query**.

## SELECT

- SELECT indicates which column(s) you want to be given the data for.
- FROM specifies from which table(s) you want to select the columns. Notice the columns need to exist in this table.
- Asterisk "*" means all columns.

```sql
SELECT id, account_id, occurred_at
FROM orders;
```

**Every SQL query** will have at least a SELECT and FROM statement. The SELECT statement is where you put the columns for which you would like to show the data. The FROM statement is where you put the tables from which you would like to pull data.

## LIMIT

The LIMIT statement is useful when you want to see just the first few rows of a table. This can be much faster for loading than if we load the entire dataset.  

The LIMIT command is always the very last part of a query.

```sql
SELECT occurred_at, account_id, channel
FROM web_events
LIMIT 15;
```

## ORDER BY

The ORDER BY statement allows us to order our table by any row.  

The ORDER BY statement is always after the SELECT and FROM statements, but it is before the LIMIT statement. As you learn additional commands, the order of these statements will matter more. If we are using the LIMIT statement, it will always appear last.  

Remember DESC can be added after the column in your ORDER BY statement to sort in descending order, as the default is to sort in ascending order.  

We can ORDER BY more than one column at a time. The statement sorts according to columns listed from left first and those listed on the right after that. 


---

Material do curso ["SQL for Data Analysis"](https://classroom.udacity.com/courses/ud198) da [Udacity](https://www.udacity.com/).