# Lesson 05: User Defined Functions Part 1 ⚙️

## 🎯 Objective
Understand what User Defined Functions are and learn how scalar functions work in SQL Server.

---

## 📖 What are User Defined Functions (UDF)?

A User Defined Function (UDF) is a custom function created by the user to perform specific operations.

👉 Functions help simplify and reuse SQL code.

👉 SQL Server supports:
- Scalar Functions  
- Table-Valued Functions  

---

## 🧠 What are Scalar Functions?

A Scalar Function:
- accepts one or more parameters  
- returns a single value  

Scalar functions are useful when:
- a complex formula appears in many queries  
- you want reusable business logic  

---

## 🏗️ Creating a Scalar Function

To create a scalar function, use:

```sql
CREATE FUNCTION [schema_name.]function_name (parameter_list)
RETURNS data_type
AS
BEGIN
    statements
    RETURN value
END
```

---

## ✅ Example
```sql
CREATE FUNCTION sales.udfNetSale(
    @quantity INT,
    @list_price DEC(10,2),
    @discount DEC(4,2)
)
RETURNS DEC(10,2)
AS 
BEGIN
    RETURN @quantity * @list_price * (1 - @discount);
END;
```
👉 This function calculates net sale amount.

---

## ▶️ Calling a Scalar Function
You can call a scalar function like a built-in function:

```sql
SELECT 
    sales.udfNetSale(10,100,0.1) AS net_sale;
```

---

## 💡 Using Scalar Function in Query
```sql
SELECT 
    order_id, 
    SUM(sales.udfNetSale(quantity, list_price, discount)) AS net_amount
FROM 
    sales.order_items
GROUP BY 
    order_id
ORDER BY
    net_amount DESC;
```

---

## ✏️ Modifying a Scalar Function
To modify a function, use ALTER FUNCTION:

```sql
ALTER FUNCTION sales.udfNetSale(
    @quantity INT,
    @list_price DEC(10,2),
    @discount DEC(4,2)
)
RETURNS DEC(10,2)
AS
BEGIN
    RETURN (@quantity * @list_price) - (@quantity * @list_price * @discount);
END;
```

---

## 🆕 CREATE OR ALTER
```sql
CREATE OR ALTER FUNCTION sales.udfNetSale(
    @quantity INT,
    @list_price DEC(10,2),
    @discount DEC(4,2)
)
RETURNS DEC(10,2)
AS
BEGIN
    RETURN @quantity * @list_price * (1 - @discount);
END;
```
👉 Creates function if it does not exist
👉 Alters it if it already exists

---

## ❌ Removing a Scalar Function
```sql
DROP FUNCTION sales.udfNetSale;
```

---

## 🧪 Practice Task
Create a function:
- to calculate tax
- to calculate discount

Try:
- altering the function
- deleting the function
