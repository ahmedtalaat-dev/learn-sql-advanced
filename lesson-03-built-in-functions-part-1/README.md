# Lesson 03: Built-in Functions Part 1 🔧

## 🎯 Objective
Learn how to use built-in SQL functions for string and numeric operations.

---

## 📖 What are Built-in Functions?

Built-in functions are predefined functions provided by SQL to perform common operations.

---

## 🔤 String Functions

### 🔹 UPPER

```sql
SELECT UPPER(first_name) FROM sales.customers;
```
👉 Converts text to uppercase

### 🔹 LOWER
```sql
SELECT LOWER(first_name) FROM sales.customers;
```
👉 Converts text to lowercase

### 🔹 LEN
```sql
SELECT LEN(first_name) FROM sales.customers;
```
👉 Returns length of string

### 🔹 CONCAT
```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM sales.customers;
```
👉 Combines strings

### 🔹 SUBSTRING
```sql
SELECT SUBSTRING(first_name, 1, 3)
FROM sales.customers;
```
👉 Extracts part of string

---

## 🔢 Numeric Functions
### 🔹 ROUND
```sql
SELECT ROUND(list_price, 0)
FROM production.products;
```
👉 Rounds number

### 🔹 ABS
```sql
SELECT ABS(-100);
```
👉 Returns absolute value

### 🔹 CEILING
```sql
SELECT CEILING(10.2);
```
👉 Rounds up

### 🔹 FLOOR
```sql
SELECT FLOOR(10.8);
```
👉 Rounds down

---

## 🧠 Key Notes
- Functions simplify calculations
- Can be used inside SELECT
- Can be combined with other queries

---

## 🧪 Practice Task
- Convert names to uppercase
- Get length of customer names
- Round product prices
