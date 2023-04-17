# Introduction to Database Indexing
## Introduction
In this lesson, we'll go over and learn how to apply database indexes.
## Objectives
- Learn how database indexes help query performance

### What are database indexes?

Indexes are an abstraction used in the background of a database to speed up querying. Indexes reduce query runtime by providing a way to quickly look up the requested data. A table can have one or more indexes associated with it. An index is defined by a field, usually on a foreign key.

### Why are indexes needed?

Imagine you have a table with millions rows - searching for a single row, like `SELECT * FROM table WHERE emp_id = 'E104592VK'` would take a full table scan. But if you have the `emp_id` field as an index, the driver would be able to find this row very quickly. It is important to note that you only want to index few columns that you may search over multiple times instead of creating indexes for all columns. Think of it as instead of doing a full scan, you apply `WHERE` clause on an index, like a phone book or a dictionary, where you can think of the alphabet as an index, then you can search the word faster.

### How are indexes created?

The syntax for creating an index will vary depending on the database, but typically looks like this:
```
CREATE INDEX <index_name>
ON <table_name> (column1, column2, ...)
```

For example, if we want to create an index on `employee` table, we can do something like this:

```
CREATE INDEX employee_idx
ON employee (emp_id)
```

Keep in mind, the indexes are just abstractions so it's not visible to the users.

### Indexes sound amazing all around.. what's the downside?

Inserting/Deleting/Updating records for tables that have indexes will have decreased query performance. The indexes are created to really speed up the search, but not the other operations. So a thoughtful design process is required when adding or removing indexes from a table.


### Summary

We discussed why we may need an index and how to create them. We also discussed the downside of creating the index.
