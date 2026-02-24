# Experiment 2: DDL Commands
# Register Number : 212224230304
# Developed By : B.VIMALRAJ

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="536" height="192" alt="image" src="https://github.com/user-attachments/assets/07a5dd89-1442-411b-9408-73096bc84723" />


```sql
insert into Products (Name , Category , Price , Stock) values ("Smartphone" , "Electronics" , 800 , 150);

insert into Products (Name , Category , Price , Stock) values ("Headphones" , "Accessories" , 200 , 300);
```

**Output:**

<img width="901" height="245" alt="image" src="https://github.com/user-attachments/assets/b54d113e-913a-4e83-9037-aeaeb4c98e74" />


**Question 2**
---
<img width="918" height="240" alt="image" src="https://github.com/user-attachments/assets/7610a5d2-3d5a-49b0-a21a-8bd866f0389f" />


```sql
create table Department (
    DepartmentID INTEGER primary key , 
    DepartmentName TEXT Unique not null , 
    Location TEXT
);
```

**Output:**

<img width="831" height="167" alt="image" src="https://github.com/user-attachments/assets/b527d62b-cf9e-4147-ba8b-dd66cb5abe5b" />


**Question 3**
---
<img width="927" height="249" alt="image" src="https://github.com/user-attachments/assets/c7c588bc-ab62-409c-ab9d-0e2e5b99de3a" />


```sql
Alter table Employees
add salary INTEGER Check(salary > 0)
```

**Output:**

<img width="893" height="150" alt="image" src="https://github.com/user-attachments/assets/e7ab6630-15e2-434b-919c-1d273a2b6404" />


**Question 4**
---
<img width="811" height="336" alt="image" src="https://github.com/user-attachments/assets/c0b30801-6c9f-4870-b26d-401e4823c5ee" />


```sql
Insert into Customers select * from Old_customers;
```

**Output:**

<img width="891" height="149" alt="image" src="https://github.com/user-attachments/assets/3b5e9a1f-d9cb-4998-b15a-6d02287e5ff3" />

**Question 5**

---
<img width="716" height="180" alt="image" src="https://github.com/user-attachments/assets/8b3a01e6-d170-4ecd-b5ca-5e43495076d7" />


```sql
create table Attendance(
    AttendanceID INTEGER , 
    EmployeeID INTEGER references Employees(EmployeeID) , 
    AttendanceDate DATE , 
    Status TEXT CHECK(Status IN('Present' , 'Absent' , 'Leave'))
);
```

**Output:**

<img width="878" height="175" alt="image" src="https://github.com/user-attachments/assets/49658fc6-da43-45d4-99cd-63e74a03ed52" />

**Question 6**
---
<img width="864" height="195" alt="image" src="https://github.com/user-attachments/assets/94e798d2-cb7c-4ea1-b76e-f266dd62c6cd" />


```sql
insert into Products(ProductID , Name , Category , Price , Stock) values (101 , "Laptop" , "Electronics" , 1500 , 50);
```

**Output:**

<img width="855" height="126" alt="image" src="https://github.com/user-attachments/assets/836466fa-f697-4e40-9bb9-ce9f18fabf70" />

**Question 7**
---
<img width="730" height="164" alt="image" src="https://github.com/user-attachments/assets/59285efb-5e23-442a-9f3c-f269808a6702" />


```sql
create table ProjectAssignments
(
    AssignmentID INTEGER Primary key , 
    EmployeeID INTEGER references Employees(EmployeeID) , 
    ProjectID INTEGER references Projects(ProjectID) ,
    AssignmentDate DATE not null
);
```

**Output:**

<img width="846" height="179" alt="image" src="https://github.com/user-attachments/assets/7ff243c1-a7af-4771-8424-fee53c950054" />

**Question 8**
---
<img width="447" height="114" alt="image" src="https://github.com/user-attachments/assets/f7ddd484-8d88-4541-a90d-cd294dae3ad6" />


```sql
create table Orders
(
    OrderID INTEGER , 
    OrderDate TEXT , 
    CustomerID INTEGER
);
```

**Output:**

<img width="881" height="227" alt="image" src="https://github.com/user-attachments/assets/7bbb779d-2618-479c-9b02-4be95799341e" />

**Question 9**
---
<img width="889" height="213" alt="image" src="https://github.com/user-attachments/assets/fee8d0b4-2c48-4841-804d-918264174d24" />


```sql
Alter table employee add first_name varchar(50);
Alter table employee add last_name varchar(50);
```

**Output:**

<img width="911" height="181" alt="image" src="https://github.com/user-attachments/assets/bef16c55-7792-4d65-96ad-f890eac78021" />

**Question 10**
---
<img width="519" height="103" alt="image" src="https://github.com/user-attachments/assets/d4e43a7f-7bd9-4d9b-9340-c1b725d9f84e" />


```sql
create table Orders(
    OrderID INTEGER primary key ,
    OrderDate DATE not null ,
    CustomerID INTEGER references Customers(CustomerID)
);
```

**Output:**

<img width="780" height="218" alt="image" src="https://github.com/user-attachments/assets/7b76d45c-a934-4f82-903c-d58162f05e5a" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
