# Lesson 12: Triggers ⚡

## 🎯 Objective
Learn how to create and use triggers in SQL Server to automatically execute actions after INSERT, UPDATE, or DELETE events.

---

## 📖 What is a Trigger?

A Trigger is a special type of stored procedure that automatically executes when a specific event occurs on a table.

👉 Triggers respond to:
- INSERT  
- UPDATE  
- DELETE  

---

## 🧠 Why Use Triggers?

Triggers are useful for:
- auditing changes  
- logging operations  
- enforcing business rules  
- preventing invalid operations  

---

# 🔹 CREATE TRIGGER Syntax

```sql
CREATE TRIGGER [schema_name.]trigger_name
ON table_name
AFTER [INSERT], [UPDATE], [DELETE]
AS
BEGIN
    sql_statements
END
```

---

## 🧠 Syntax Explanation

| Part | Description |
|------|-------------|
| CREATE TRIGGER | Creates new trigger |
| ON table_name | Table linked to trigger |
| AFTER | Event that fires trigger |
| AS | Beginning of trigger body |

---

## 🔹 Trigger Events

| Event | Description |
|------|-------------|
| INSERT | Trigger fires after insert |
| UPDATE | Trigger fires after update |
| DELETE | Trigger fires after delete |

---

## 🔹 Virtual Tables in Triggers

SQL Server provides two special tables inside triggers:

| Table | Description |
|------|-------------|
| INSERTED | Holds new rows |
| DELETED | Holds old/deleted rows |

---

## 🔹 INSERTED and DELETED Behavior

| DML Event | INSERTED Table | DELETED Table |
|-----------|----------------|---------------|
| INSERT | New rows | Empty |
| UPDATE | Updated rows | Old rows |
| DELETE | Empty | Deleted rows |

---

## 🔹 Creating Audit Table
```sql
CREATE TABLE production.product_audits(
    change_id INT IDENTITY PRIMARY KEY,
    product_id INT NOT NULL,
    product_name VARCHAR(255) NOT NULL,
    brand_id INT NOT NULL,
    category_id INT NOT NULL,
    model_year SMALLINT NOT NULL,
    list_price DEC(10,2) NOT NULL,
    updated_at DATETIME NOT NULL,
    operation CHAR(3) NOT NULL,
    CHECK(operation = 'INS' OR operation = 'DEL')
);
```
👉 This table stores product changes.

---

## 🔹 Creating a Trigger
```sql
CREATE TRIGGER production.trg_product_audit
ON production.products
AFTER INSERT, DELETE
AS
BEGIN
    SET NOCOUNT ON;

    INSERT INTO production.product_audits(
        product_id,
        product_name,
        brand_id,
        category_id,
        model_year,
        list_price,
        updated_at,
        operation
    )

    SELECT
        i.product_id,
        product_name,
        brand_id,
        category_id,
        model_year,
        i.list_price,
        GETDATE(),
        'INS'
    FROM inserted i

    UNION ALL

    SELECT
        d.product_id,
        product_name,
        brand_id,
        category_id,
        model_year,
        d.list_price,
        GETDATE(),
        'DEL'
    FROM deleted d;
END
```

---

## 🔹 Testing INSERT Trigger
```sql
INSERT INTO production.products(
    product_name,
    brand_id,
    category_id,
    model_year,
    list_price
)
VALUES (
    'Test product',
    1,
    1,
    2018,
    599
);
```
👉 Trigger automatically inserts audit record.

---

## 🔹 View Audit Data
```sql
SELECT *
FROM production.product_audits;
```

---

## 🔹 Testing DELETE Trigger
```sql
DELETE FROM production.products
WHERE product_id = 322;
```
👉 Deleted row is stored in audit table.

---

## 🔹 Modify a Trigger
```sql
ALTER TRIGGER production.trg_product_audit
ON production.products
AFTER INSERT, DELETE
AS
BEGIN
    PRINT 'Trigger Executed';
END
```

---

## 🔹 Drop a Trigger
```sql
DROP TRIGGER production.trg_product_audit;
```
