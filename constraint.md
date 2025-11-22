# Constraints in PostgreSQL

**Constraints** are rules applied to columns or tables that enforce data integrity and validity. They prevent invalid data from being inserted into your database.

## Types of Constraints

### 1. NOT NULL
Ensures a column cannot have NULL values.

```sql
CREATE TABLE employees (
    emp_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL
);
```

### 2. UNIQUE
Ensures all values in a column (or combination of columns) are distinct.

```sql
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE,
    email VARCHAR(100) UNIQUE
);
```

### 3. PRIMARY KEY
Combines NOT NULL and UNIQUE. Uniquely identifies each row.

```sql
CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,
    product_name VARCHAR(100)
);
```

### 4. FOREIGN KEY
Ensures values match entries in another table, maintaining referential integrity.

```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    user_id INTEGER,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```

**Common foreign key options:**
- `ON DELETE CASCADE` - Delete child records when parent is deleted
- `ON DELETE SET NULL` - Set foreign key to NULL when parent is deleted
- `ON DELETE RESTRICT` - Prevent deletion of parent if children exist (default)
- `ON UPDATE CASCADE` - Update foreign key when parent key changes

### 5. CHECK
Ensures values meet a specific condition.

```sql
CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,
    price DECIMAL(10,2) CHECK (price > 0),
    quantity INTEGER CHECK (quantity >= 0),
    discount DECIMAL(5,2) CHECK (discount >= 0 AND discount <= 100)
);
```

### 6. DEFAULT
Provides a default value when no value is specified.

```sql
CREATE TABLE posts (
    post_id SERIAL PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(20) DEFAULT 'draft'
);
```

### 7. EXCLUDE
Prevents overlapping values (useful for date ranges, geographic data, etc.).

```sql
CREATE TABLE bookings (
    room_id INTEGER,
    during TSRANGE,
    EXCLUDE USING GIST (room_id WITH =, during WITH &&)
);
```

This prevents double-booking a room during overlapping time periods.

## Adding Constraints to Existing Tables

You can add constraints after table creation:

```sql
-- Add NOT NULL
ALTER TABLE employees ALTER COLUMN email SET NOT NULL;

-- Add UNIQUE
ALTER TABLE users ADD CONSTRAINT unique_email UNIQUE (email);

-- Add CHECK
ALTER TABLE products ADD CONSTRAINT positive_price CHECK (price > 0);

-- Add FOREIGN KEY
ALTER TABLE orders ADD CONSTRAINT fk_user 
    FOREIGN KEY (user_id) REFERENCES users(user_id);
```

## Naming Constraints

It's good practice to name your constraints explicitly for easier management:

```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    user_id INTEGER,
    total DECIMAL(10,2),
    CONSTRAINT fk_orders_users FOREIGN KEY (user_id) REFERENCES users(user_id),
    CONSTRAINT check_positive_total CHECK (total >= 0)
);
```

## Why Use Constraints?

Constraints are essential because they:
- Ensure data accuracy and consistency
- Prevent invalid data entry at the database level
- Make your data rules explicit and enforceable
- Provide better error messages when violations occur
- Reduce the need for validation logic in application code

Think of constraints as a safety net that catches data problems before they corrupt your database.
