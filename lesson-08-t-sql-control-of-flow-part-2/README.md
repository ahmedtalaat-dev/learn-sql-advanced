# Lesson 08: T-SQL Control of Flow Part 2 🔁

## 🎯 Objective
Learn how to use WHILE loops, BREAK, and CONTINUE statements in T-SQL.

---

## 📖 What is a WHILE Loop?

The `WHILE` loop repeatedly executes a block of code while a condition is true.

---

## 🏗️ Syntax

```sql
WHILE condition
BEGIN
    statements
END
```

---

## ✅ Example
```sql
DECLARE @counter INT = 1;

WHILE @counter <= 5
BEGIN
    PRINT @counter;
    SET @counter = @counter + 1;
END
```
👉 Prints numbers from 1 to 5.

---

## 🔹 BREAK Statement
The BREAK statement exits the loop immediately.

---

## ✅ Example
```sql
DECLARE @counter INT = 1;

WHILE @counter <= 10
BEGIN
    IF @counter = 5
    BEGIN
        BREAK;
    END

    PRINT @counter;
    SET @counter = @counter + 1;
END
```
👉 Loop stops when counter equals 5.

---

## 🔹 CONTINUE Statement
The CONTINUE statement skips the current iteration and moves to the next iteration.

---

## ✅ Example
```sql
DECLARE @counter INT = 0;

WHILE @counter < 5
BEGIN
    SET @counter = @counter + 1;

    IF @counter = 3
    BEGIN
        CONTINUE;
    END

    PRINT @counter;
END
```
👉 Number 3 will not be printed.

---

## 🔹 WHILE with Database Example
```sql
DECLARE @number INT = 1;

WHILE @number <= 3
BEGIN
    PRINT CONCAT('Order Number: ', @number);

    SET @number += 1;
END
```

---

## 🧠 Key Notes
- WHILE repeats code while condition is true
- BREAK exits the loop
- CONTINUE skips current iteration
- Loops should always update variables

---

## ⚠️ Common Mistakes
- Infinite loops
- Forgetting to update variable
- Wrong loop condition

---

## 🧪 Practice Task
Create:
- loop printing numbers 1 → 10
- loop stopping at number 7
- loop skipping even numbers
