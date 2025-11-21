In PostgreSQL, a **schema** is a namespace that contains database objects like tables, views, functions, and indexes. Think of it as a folder system within a database that helps organize and manage your objects.

## Key Concepts

**Organization**: Schemas let you group related objects together. For example, you might have a `sales` schema for sales-related tables and a `hr` schema for human resources tables - all within the same database.

**Name collision prevention**: Multiple schemas can contain objects with the same name. You could have `sales.customers` and `marketing.customers` as separate tables in the same database.

**Access control**: You can grant permissions at the schema level, making it easier to manage who can access what. This is useful for multi-tenant applications or when different teams need different access levels.

## Default Behavior

Every PostgreSQL database comes with a `public` schema by default. When you create a table without specifying a schema, it goes into `public`. PostgreSQL also has a search path (similar to PATH in operating systems) that determines which schema to use when an object name isn't fully qualified.

## Basic Usage

Creating a schema:
```sql
CREATE SCHEMA sales;
```

Creating a table in that schema:
```sql
CREATE TABLE sales.orders (id INT, amount DECIMAL);
```

Accessing objects - you can use the fully qualified name:
```sql
SELECT * FROM sales.orders;
```

Or set your search path to avoid typing the schema name repeatedly:
```sql
SET search_path TO sales, public;
SELECT * FROM orders;  -- now finds sales.orders
```

Schemas are particularly valuable in larger applications where logical separation of concerns, security boundaries, or multi-tenancy requirements exist.
