# Lesson 04: Built-in Functions Part 2 📅

## 🎯 Objective
Learn how to use date, NULL handling, and system functions in SQL.

---

## 📅 Date Functions

### 🔹 GETDATE

```sql
SELECT GETDATE();
```
👉 Returns current date and time

### 🔹 YEAR / MONTH / DAY
```sql
SELECT YEAR(order_date), MONTH(order_date), DAY(order_date)
FROM sales.orders;
```
👉 Extract parts of date

---

## 🚫 NULL Functions

### 🔹 ISNULL
```sql
SELECT ISNULL(phone, 'No Phone')
FROM sales.customers;
```
👉 Replace NULL values

### 🔹 COALESCE
```sql
SELECT COALESCE(phone, email, 'No Data')
FROM sales.customers;
```
👉 Returns first non-null value

---

## ⚙️ System Functions

### 🔹 NEWID
```sql
SELECT NEWID();
```
👉 Generates unique ID

### 🔹 @@VERSION
```sql
SELECT @@VERSION;
```
👉 Shows SQL Server version

---

## 🧠 Key Notes
- Date functions help in time-based queries
- NULL functions prevent errors
- System functions give database info

---

## 🧪 Practice Task
- Get current date
- Extract year from orders
- Replace NULL values
