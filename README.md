# company.sql
SQL COMPANY EXAMPLE QUERIES
use company;

-- #QUESTION 1
```sql
INSERT INTO EMPLOYEE(fname, minit, lname, ssn, bdate, address, sex, salary) VALUES ('arnold', 's', 'sanders', 999999999, '1988-11-16', '2605 Grand Concourse apt 1106', 'M', '140000');
```

-- #QUESTION 2
```sql
INSERT INTO DEPARTMENT(dname, dnumber, mgrssn, mgrstartdate) VALUES ('AI', 9, 999999999, '2024-11-16');
INSERT INTO DEPARTMENT(dname, dnumber, mgrssn, mgrstartdate) VALUES ('Data Science Research', 10, 999999999, '2020-10-21');
```
-- #QUESTION 3

```sql
SELECT lname FROM EMPLOYEE ORDER BY lname ASC;
```
-- #QUESTION 4

```sql
SELECT employee.fname, employee.lname, project.pname, works_on.hours FROM works_on, project, employee WHERE pnumber=pno and ssn=essn AND hours > 10.0;
```

-- #QUESTION 5
```sql
SELECT fname, minit, lname FROM EMPLOYEE WHERE dno=5 AND salary > 25000 AND salary < 45000;
```

-- #QUESTION 6		
```sql
SELECT bdate, address FROM EMPLOYEE WHERE fname='Joyce' AND minit='A' AND lname='English';
```

-- #QUESTION 7

```sql
SELECT fname, minit, lname FROM EMPLOYEE, DEPENDENT WHERE dependent_name = fname;
```
-- #QUESTION 8

```sql
SELECT * FROM EMPLOYEE WHERE superssn IN (SELECT ssn FROM EMPLOYEE WHERE fname='Franklin' AND lname='Wong');
```

-- #QUESTION 9

```sql
SELECT AVG(salary), department.dname, COUNT(employee.ssn) AS employee_count FROM EMPLOYEE, DEPARTMENT WHERE salary > 30000 GROUP BY department.dnumber=employee.dno, department.dname;
```

-- #QUESTION 10

```sql
SELECT fname, lname, salary, dno FROM EMPLOYEE, DEPARTMENT WHERE sex='M' AND salary > 30000 GROUP BY dno=dnumber, fname, lname, salary, dno;

SELECT * FROM EMPLOYEE WHERE dno IN (SELECT dno, MAX(salary) FROM EMPLOYEE GROUP BY dno ORDER BY dno DESC LIMIT 1);

SELECT * FROM EMPLOYEE WHERE superssn=888665555;

SELECT employee.fname, employee.lname, 1.3 * salary as increased_salary, salary AS original_salary FROM EMPLOYEE, WORKS_ON, PROJECT WHERE employee.ssn=works_on.essn AND works_on.pno=project.pnumber AND project.pname="ProductY";

SELECT fname, lname, address FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND department.dname="Headquarters";

UPDATE employee SET bdate="1965-01-08" WHERE ssn=123456789;

SELECT pnumber, dnum, lname, address, bdate FROM PROJECT, DEPARTMENT, EMPLOYEE WHERE dnum=dnumber AND mgrssn=ssn AND plocation="Stafford";

SELECT pnumber, fname, lname FROM employee, project WHERE employee.dno=project.dnum AND lname="Smith";

SELECT E.fname, E.lname, P.pname, D.dname FROM EMPLOYEE AS E, DEPARTMENT AS D, PROJECT AS P WHERE E.dno=D.dnumber AND E.dno=P.dnum ORDER BY E.fname, E.lname;

INSERT INTO DEPARTMENT (dname, dnumber, mgrssn, mgrstartdate) VALUES ("Marketing", 11, 666666601, '2000-07-22');
INSERT INTO DEPARTMENT (dname, dnumber, mgrssn, mgrstartdate) VALUES ("Human Resources", 12, 987654321, '2010-04-02');
INSERT INTO DEPARTMENT (dname, dnumber, mgrssn, mgrstartdate) VALUES ("Finance", 13, 444444402, '2012-07-12');
INSERT INTO DEPARTMENT (dname, dnumber, mgrssn, mgrstartdate) VALUES ("Operations", 14, 666666602, '2024-05-22');
INSERT INTO DEPARTMENT (dname, dnumber, mgrssn, mgrstartdate) VALUES ("Customer Service", 15, 666666600, '2020-05-22');
```

-- SKIP 21-26 

```sql
SELECT * FROM EMPLOYEE WHERE fname LIKE 'a%';
SELECT * FROM EMPLOYEE WHERE fname LIKE '%es';
ALTER TABLE employee ADD zipcode char(5);
ALTER TABLE employee RENAME COLUMN zipcode to empl_zipcode;
ALTER TABLE employee MODIFY COLUMN empl_zipcode varchar(5);

SELECT fname, lname, 1.1 * salary AS increased_salary FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND dname="Research";
SELECT COUNT(ssn) FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND dname="Administration" AND employee.salary > 50000;
SELECT AVG(salary) AS average_salary FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND dname="Administration";
SELECT employee.fname, employee.lname, employee.dno, MAX(salary) FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND department.dname="Administration" GROUP BY dno, lname, fname LIMIT 1;
SELECT employee.fname, employee.lname, employee.dno, MIN(salary) FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND department.dname="Administration" GROUP BY dno, lname, fname ORDER BY dno LIMIT 1;
SELECT SUM(salary) FROM EMPLOYEE, DEPARTMENT WHERE employee.dno=department.dnumber AND department.dname="Research";
```
