# Primary Keys and Foreign Keys in PostgreSQL

## Primary Key

A **primary key** is a column (or set of columns) that uniquely identifies each row in a table. Think of it like a unique ID card for every record.

**Key characteristics:**
- Must contain unique values (no duplicates)
- Cannot contain NULL values
- Each table can have only one primary key
- Automatically creates an index for faster lookups

**Example:**

```sql
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL
);
```

Here, `user_id` is the primary key. Each user gets a unique ID that distinguishes them from all other users.

## Foreign Key

A **foreign key** is a column (or set of columns) that creates a link between two tables. It references the primary key of another table, establishing a relationship between them.

**Key characteristics:**
- Must match a value in the referenced table's primary key (or be NULL if allowed)
- Enforces referential integrity, preventing orphaned records
- A table can have multiple foreign keys

**Example:**

```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    user_id INTEGER NOT NULL,
    order_date DATE NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```

Here, `user_id` in the `orders` table is a foreign key that references `user_id` in the `users` table. This ensures every order is linked to a valid user.

## How They Work Together

Foreign keys enforce data integrity. In the example above, PostgreSQL will prevent you from inserting an order with a `user_id` that doesn't exist in the `users` table. You also can't delete a user if they have orders, unless you specify a cascade behavior like `ON DELETE CASCADE`.

This relationship system is fundamental to relational databases and helps maintain consistent, accurate data across your database.
