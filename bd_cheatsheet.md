# Sources

- [UNSTPB/ACS](https://ocw.cs.pub.ro/courses/bd/laboratoare/02)
# Login

```sql
connect SYS as SYSDBA
```
```sql
CONNECT  stud1/student
```

# Create a user
```sql
connect SYS as SYSDBA
```
```sql
CREATE USER [name] IDENTIFIED BY [name after /];
```

## Grant special permissions

```sql
GRANT CREATE SESSION TO [username];
GRANT RESOURCE TO [username];
ALTER USER [username] QUOTA UNLIMITED ON USERS;
```

# Create a table

```sql
CREATE TABLE [ schema. ] [table name]
(
    [column_name_1] [datatype] [DEFAULT VALUE|expression] [inline_constraints] ,
    [[column_name_2] [datatype] [DEFAULT VALUE|expression] [inline_constraints] , ....]
    [constraint] [name] [primary key | foreign key] ([attributes])
);
```

## Example

```sql
CREATE TABLE departamente (
    id_departament NUMBER(2) NOT NULL,
    denumire_departament VARCHAR2(30),
    telefon VARCHAR2(10),
    data_infiintarii DATE DEFAULT SYSDATE,

    CONSTRAINT pk_departamente PRIMARY KEY (id_departament),
    CONSTRAINT uq_denumire UNIQUE (denumire_departament),
);
```

# Alter Tables

```sql
-- Primary Key
ALTER TABLE [table name] ADD CONSTRAINT pk_[name of the key] PRIMARY KEY ([attribute]);
```
```sql
-- Foreign Key
ALTER TABLE [name source table] ADD CONSTRAINT fk_[name attribute source]__[name attribute dest] FOREIGN KEY ([source attribute]) REFERENCES [name dest table] ([dest attribute]);
```
```sql
-- Unique
ALTER TABLE [table name] ADD CONSTRAINT uq_[attribute name] UNIQUE ([attribute]);
```

# Insert Data in Table

```sql
INSERT INTO [table name]
    ([column_name1][, column_name2 [, ...]])
    VALUES(value1 [, value2, [....]]);
```
```sql
-- or
INSERT INTO [table name]
    VALUES(value_column1, value_column2, ...) -- for all columns in their order
```

# Select Data from Table

```sql
SELECT [* | [column_name1][, column_name2[,...]]]
    FROM  [table name]
        [WHERE [conditions]]
```

## Example

```sql
SELECT * FROM angajati;

SELECT nume, prenume, functie FROM angajati;

SELECT nume, prenume, functie FROM angajati WHERE functie='Director'
```

# Modify data

```sql
UPDATE [table name]
    SET [column_name1] = [new_value1] [, column_name2 = new_value2, [,...]]
        [WHERE [conditions]]
```

# Delete data

```sql
DELETE FROM [table name] [WHERE [conditions]];
```