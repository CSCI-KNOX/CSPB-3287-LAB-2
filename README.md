# CSPB-3287-LAB-2
## Constraints and Triggers

# Referential Integrity in MySQL

## Declaring Referential Integrity (Foreign Key) Constraints

Foreign key constraints are used to check referential integrity between tables in a database. Consider, for example, the
following two tables:

```
    create table Residence (
      name VARCHAR PRIMARY KEY ,
      capacity INT
    );
    create table Student (
      id INT PRIMARY KEY ,
      firstName VARCHAR ,
      lastName VARCHAR ,
      residence VARCHAR
    );
```
We can enforce the constraint that a `Student`’s residence actually exists by making `Student.residence` a foreign key
that refers to `Residence.name`. SQLite lets you specify this relationship in several different ways:

```
    create table Residence (
      name VARCHAR PRIMARY KEY ,
      capacity INT
    );
    create table Student (
      id INT PRIMARY KEY ,
      firstName VARCHAR ,
      lastName VARCHAR ,
      residence VARCHAR ,
      FOREIGN KEY(residence) REFERENCES Residence(name)
    );
```
or

```
    create table Residence (
      name VARCHAR PRIMARY KEY ,
      capacity INT
    );
    create table Student (
      id INT PRIMARY KEY ,
      firstName VARCHAR ,
      lastName VARCHAR ,
      residence VARCHAR REFERENCES Residence(name)
    );
```
or

```
    create table Residence (
      name VARCHAR PRIMARY KEY ,
      capacity INT
    );
    create table Student (
      id INT PRIMARY KEY ,
      firstName VARCHAR ,
      lastName VARCHAR ,
      residence VARCHAR REFERENCES Residence -- Implicitly references the
      primary key of the Residence table.
    );
```
All three forms are valid syntax for specifying the same constraint.
