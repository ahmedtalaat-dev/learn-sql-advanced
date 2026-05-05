# Lesson 01: Stored Procedure Part 1 ⚙️

## 🎯 Objective
Understand what a stored procedure is and learn how to create, execute, modify, and delete it.

---

## 📖 What is a Stored Procedure?

A Stored Procedure is a saved SQL query that you can reuse and execute multiple times.

👉 It is stored inside the database  
👉 Helps organize and reuse code  

---

## 🧠 Why Use Stored Procedures?

- Reuse SQL code  
- Improve performance  
- Enhance security  
- Simplify complex operations  

---

## 🏗️ Create a Stored Procedure

```sql
CREATE PROCEDURE procedure_name
AS
BEGIN
    SELECT * FROM table_name;
END;
```

---

## ✅ Example
```sql
CREATE PROCEDURE get_all_products
AS
BEGIN
    SELECT * FROM production.products;
END;
```

---

## ▶️ Execute a Stored Procedure
```sql
EXEC get_all_products;
```
👉 Runs the stored procedure and returns the result

---

## ✏️ Modify a Stored Procedure
```sql
ALTER PROCEDURE get_all_products
AS
BEGIN
    SELECT product_name, list_price
    FROM production.products;
END;
```

---

## ❌ Delete a Stored Procedure
```sql
DROP PROCEDURE get_all_products;
```

---

## 🧠 Key Notes
- Stored procedures are stored in the database
- Use EXEC to run them
- Use ALTER to update them
- Use DROP to remove them

---

## 🧪 Practice Task
- Create a procedure
- Modify it
- Execute it
- Delete it
