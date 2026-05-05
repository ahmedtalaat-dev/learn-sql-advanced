# Lesson 02: Stored Procedure Part 2 (Parameters) ⚙️

## 🎯 Objective
Learn how to use parameters in stored procedures to make them dynamic and reusable.

---

## 📖 What are Parameters?

Parameters are values passed to a stored procedure when it is executed.

👉 They allow you to customize the behavior of the procedure

---

## 🧠 Why Use Parameters?

- Make procedures dynamic  
- Avoid repeating code  
- Pass different values each time  

---

## 🏗️ Syntax

```sql
CREATE PROCEDURE procedure_name
    @parameter_name data_type
AS
BEGIN
END;
```

---

## ✅ Example 1 (Single Parameter)
```sql
CREATE PROCEDURE get_product_by_id
    @product_id INT
AS
BEGIN
    SELECT * 
    FROM production.products
    WHERE product_id = @product_id;
END;
```

---

## ▶️ Execute Procedure with Parameter
```sql
EXEC get_product_by_id @product_id = 1;
```

---

## 🏗️ Example 2 (Multiple Parameters)
```sql
CREATE PROCEDURE get_products_by_price
    @min_price DECIMAL(10,2),
    @max_price DECIMAL(10,2)
AS
BEGIN
    SELECT product_name, list_price
    FROM production.products
    WHERE list_price BETWEEN @min_price AND @max_price;
END;
```

---

## ▶️ Execute Multiple Parameters
```sql
EXEC get_products_by_price 
    @min_price = 500,
    @max_price = 2000;
```

---

## 🏗️ Default Parameter Value
```sql
CREATE PROCEDURE get_products_min_price
    @min_price DECIMAL(10,2) = 100
AS
BEGIN
    SELECT product_name, list_price
    FROM production.products
    WHERE list_price >= @min_price;
END;
```
👉 If no value is passed → default is used

---

## ▶️ Execute with Default
```sql
EXEC get_products_min_price;
```

---

## 🧠 Key Notes
- Parameters start with @
- You must define data type
- You can use multiple parameters
- You can assign default values

---

## 🧪 Practice Task
Create a procedure:
- get customer by id

Create another:
- get orders between two dates

Try:
- using default values
- passing different parameters
