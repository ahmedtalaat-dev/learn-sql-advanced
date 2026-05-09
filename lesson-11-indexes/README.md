# Lesson 11: Indexes ⚡

## 🎯 Objective
Understand what indexes are in SQL Server and learn how to create, use, and remove them to improve query performance.

---

## 📖 What is an Index?

An Index is a database object that improves the speed of data retrieval operations.

👉 It works similarly to an index in a book  
👉 SQL Server uses indexes to find data faster

---

## 🧠 Why Use Indexes?

- Improve SELECT query performance  
- Speed up searching and filtering  
- Optimize JOIN operations  
- Reduce table scans  

---

## ⚠️ Important Note

Indexes improve read performance, but:
- may slow down INSERT, UPDATE, DELETE operations  
- consume additional storage  

---

## 🔹 Types of Indexes

| Type | Description |
|------|-------------|
| Clustered Index | Sorts and stores table data physically |
| Non-Clustered Index | Stores index separately from table data |

---

## 🔹 Clustered Index

A table can have only one clustered index because the data rows can only be sorted one way.

---

## 🏗️ Create Clustered Index

```sql
CREATE CLUSTERED INDEX index_name
ON table_name(column_name);
```

---

## ✅ Example
```sql
CREATE CLUSTERED INDEX idx_product_id
ON production.products(product_id);
```

---

## 🔹 Non-Clustered Index

A non-clustered index creates a separate structure that points to table data.

👉 A table can have multiple non-clustered indexes.

---

## 🏗️ Create Non-Clustered Index
```sql
CREATE NONCLUSTERED INDEX index_name
ON table_name(column_name);
```

---

## ✅ Example
```sql
CREATE NONCLUSTERED INDEX idx_product_name
ON production.products(product_name);
```

