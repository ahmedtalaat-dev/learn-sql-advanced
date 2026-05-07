# Lesson 06: User Defined Functions Part 2 (Table-Valued Functions) 📋

## 🎯 Objective
Learn how to create and use table-valued functions in SQL Server.

---

## 📖 What is a Table-Valued Function?

A Table-Valued Function (TVF) is a user-defined function that returns a table.

👉 You can use it just like a normal table.

---

## 🧠 Why Use Table-Valued Functions?

- Reuse query logic  
- Create parameterized views  
- Simplify complex queries  

---

# 🔹 Inline Table-Valued Function

An Inline Table-Valued Function returns the result of a single SELECT statement.

---

## 🏗️ Creating an Inline TVF

```sql
CREATE FUNCTION function_name(parameter)
RETURNS TABLE
AS
RETURN
(
    SELECT ...
)
```

---

## ✅ Example
```sql
CREATE FUNCTION udfProductInYear (
    @model_year INT
)
RETURNS TABLE
AS
RETURN
    SELECT 
        product_name,
        model_year,
        list_price
    FROM
        production.products
    WHERE
        model_year = @model_year;
```

---

## ▶️ Executing a Table-Valued Function
```sql
SELECT 
    * 
FROM 
    udfProductInYear(2017);
```

---

## ✅ Selecting Specific Columns
```sql
SELECT 
    product_name,
    list_price
FROM 
    udfProductInYear(2018);
```

---

## ✏️ Modifying a Table-Valued Function
```sql
ALTER FUNCTION udfProductInYear (
    @start_year INT,
    @end_year INT
)
RETURNS TABLE
AS
RETURN
    SELECT 
        product_name,
        model_year,
        list_price
    FROM
        production.products
    WHERE
        model_year BETWEEN @start_year AND @end_year;
```

---

## ✅ Example
```sql
CREATE FUNCTION udfContacts()
RETURNS @contacts TABLE (
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(255),
    phone VARCHAR(25),
    contact_type VARCHAR(20)
)
AS
BEGIN
    INSERT INTO @contacts
    SELECT 
        first_name, 
        last_name, 
        email, 
        phone,
        'Staff'
    FROM sales.staffs;

    INSERT INTO @contacts
    SELECT 
        first_name, 
        last_name, 
        email, 
        phone,
        'Customer'
    FROM sales.customers;

    RETURN;
END;
```

---

## ▶️ Execute MSTVF
```sql
SELECT * 
FROM udfContacts();
```
