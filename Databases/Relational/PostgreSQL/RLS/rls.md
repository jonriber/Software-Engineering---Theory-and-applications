# Row Level Security (RLS)

![alt text](image.png)

This is a postgresql resource in which you can control the access to specific rows in a table based on different conditions.

Using this feature, we can control who are the ones who can view/modify rows.

## How is it done?

- enhanced security
- granular control

### Requirements

- PostgreSQL 9.5 or higher
- Access to a PostgreSQL instance with enough permissions to create tables, policies and users

### Tutorial

- Create an `employees` table

```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    department TEXT NOT NULL,
    salary NUMERIC NOT NULL,
    user_role TEXT NOT NULL  -- Usado para aplicar RLS
);
```

