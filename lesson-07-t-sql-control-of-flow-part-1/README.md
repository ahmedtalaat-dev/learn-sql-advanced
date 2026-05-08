# Lesson 07: T-SQL Control of Flow Part 1 🔄

## 🎯 Objective
Learn how to control the execution flow in T-SQL using BEGIN...END and IF statements.

---

## 📖 What is Control of Flow?

Control-of-flow statements determine how SQL Server executes statements, conditions, and blocks of code.

👉 They help add logic to SQL scripts.

---

## 🔹 BEGIN...END

The `BEGIN...END` block groups multiple SQL statements together.

---

## 🏗️ Syntax

```sql
BEGIN
    statement1
    statement2
END
```

---

## ✅ Example
```sql
BEGIN
    PRINT 'Welcome';
    PRINT 'SQL Server';
END
```
👉 Both statements execute as one block.

---

## 🔹 IF Statement
The IF statement executes code only when a condition is true.

## 🏗️ Syntax
```sql
IF condition
BEGIN
    statements
END
```

---

## ✅ Example
```sql
DECLARE @price DECIMAL(10,2) = 1500;

IF @price > 1000
BEGIN
    PRINT 'Expensive Product';
END
```

---

## 🔹 IF...ELSE
Use ELSE when the condition is false.

---

## 🏗️ Syntax
```sql
IF condition
BEGIN
    statements
END
ELSE
BEGIN
    statements
END
```

---

## ✅ Example
```sql
DECLARE @quantity INT = 5;

IF @quantity > 10
BEGIN
    PRINT 'Large Order';
END
ELSE
BEGIN
    PRINT 'Small Order';
END
```

---

## ✅ Example
```sql
DECLARE @score INT = 85;

IF @score >= 50
BEGIN
    IF @score >= 80
    BEGIN
        PRINT 'Excellent';
    END
END
```

---

## 🧠 Key Notes
- BEGIN...END groups statements
- IF executes code conditionally
- ELSE runs when condition is false

---

## 🧪 Practice Task
Create:
- IF statement checking product price
- IF...ELSE checking stock quantity
