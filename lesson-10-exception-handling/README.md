# Lesson 10: Exception Handling 🚨

## 🎯 Objective
Learn how to handle errors and exceptions in SQL Server using TRY...CATCH blocks.

---

## 📖 What is Exception Handling?

Exception handling is used to detect and manage errors during SQL execution.

👉 It prevents the program from crashing  
👉 Helps display meaningful error messages  

---

## 🧠 Why Use Exception Handling?

- Handle runtime errors  
- Prevent unexpected failures  
- Improve debugging  
- Control transactions safely  

---

## 🔹 TRY...CATCH

SQL Server uses:
- `BEGIN TRY`
- `BEGIN CATCH`

to handle errors.

---

## 🏗️ Syntax

```sql
BEGIN TRY
    -- statements
END TRY

BEGIN CATCH
    -- error handling
END CATCH
```

---

## ✅ Simple Example
```sql
BEGIN TRY
    SELECT 10 / 0;
END TRY

BEGIN CATCH
    PRINT 'An error occurred';
END CATCH
```
👉 Division by zero causes an error
👉 CATCH block handles it

---

## 🔹 Getting Error Information
SQL Server provides built-in functions for error details.

---

## ✅ Example
```sql
BEGIN TRY
    SELECT 10 / 0;
END TRY

BEGIN CATCH
    PRINT ERROR_MESSAGE();
END CATCH
```

---

## 🔹 Common Error Functions

| Function | Description |
|----------|-------------|
| ERROR_MESSAGE() | Returns error message |
| ERROR_NUMBER() | Returns error number |
| ERROR_LINE() | Returns line number |
| ERROR_PROCEDURE() | Returns procedure name |

---

## ✅ Example with Multiple Error Details
```sql
BEGIN TRY
    SELECT 10 / 0;
END TRY

BEGIN CATCH
    PRINT 'Error Number: ' + CAST(ERROR_NUMBER() AS VARCHAR);
    PRINT 'Error Message: ' + ERROR_MESSAGE();
    PRINT 'Error Line: ' + CAST(ERROR_LINE() AS VARCHAR);
END CATCH
```
