# Lesson 09: Cursors 🎯

## 🎯 Objective
Understand what cursors are in SQL Server and learn how to use them to process rows one by one.

---

## 📖 What is a Cursor?

A Cursor is a database object used to retrieve and process rows individually from a result set.

👉 Normally, SQL works with all rows at once  
👉 Cursors allow row-by-row processing

---

## 🧠 Why Use Cursors?

Cursors are useful when:
- processing rows individually  
- applying custom logic for each row  
- looping through query results  

---

## ⚠️ Important Note

Cursors are slower than normal SQL queries.

👉 Use them only when necessary.

---

# 🔹 Cursor Lifecycle

A cursor usually follows these steps:

1. DECLARE cursor  
2. OPEN cursor  
3. FETCH rows  
4. Process rows  
5. CLOSE cursor  
6. DEALLOCATE cursor  

---

# 🏗️ Declaring a Cursor

```sql
DECLARE cursor_name CURSOR
FOR
SELECT column_name
FROM table_name;
```

---

## ✅ Example
```sql
DECLARE product_cursor CURSOR
FOR
SELECT product_name
FROM production.products;
```

---

## 🔹 Opening a Cursor
```sql
OPEN product_cursor;
```
👉 Activates the cursor.

---

## 🔹 Fetching Data
```sql
DECLARE @product_name VARCHAR(255);

FETCH NEXT FROM product_cursor
INTO @product_name;
```
👉 Retrieves the next row.

---

## 🔹 Using WHILE with Cursor
```sql
DECLARE product_cursor CURSOR
FOR
SELECT product_name
FROM production.products;

DECLARE @product_name VARCHAR(255);

OPEN product_cursor;

FETCH NEXT FROM product_cursor INTO @product_name;

WHILE @@FETCH_STATUS = 0
BEGIN
    PRINT @product_name;

    FETCH NEXT FROM product_cursor INTO @product_name;
END
```

---

## 🔹 Closing a Cursor
```sql
CLOSE product_cursor;
```
👉 Releases the current result set.

## 🔹 Deallocating a Cursor
```sql
DEALLOCATE product_cursor;
```
👉 Removes the cursor completely from memory.

---

## ✅ Full Cursor Example
```sql
DECLARE customer_cursor CURSOR
FOR
SELECT first_name
FROM sales.customers;

DECLARE @first_name VARCHAR(255);

OPEN customer_cursor;

FETCH NEXT FROM customer_cursor INTO @first_name;

WHILE @@FETCH_STATUS = 0
BEGIN
    PRINT @first_name;

    FETCH NEXT FROM customer_cursor INTO @first_name;
END

CLOSE customer_cursor;

DEALLOCATE customer_cursor;
```
