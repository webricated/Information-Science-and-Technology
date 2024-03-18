```cmd



/*
3.	Consider the Employee-pay scenario given below.
EMPLOYEE(emp_id : integer, emp_name: string)
DEPARTMENT(dept_id: integer, dept_name:string)
PAYDETAILS(emp_id : integer, dept_id: integer, basic: integer, deductions: integer, additions: integer, DOJ: date)
PAYROLL(emp_id : integer, pay_date: date)
For the above schema, perform the following:
a) Create the tables with the appropriate integrity constraints
b) Insert around 10 records in each of the tables
c) List the employee details department wise
d) List all the employee names who joined after particular date
e) List the details of employees whose basic salary is between 10,000 and 20,000
f) Give a count of how many employees are working in each department
g) Give a names of the employees whose netsalary>10,000
h) List the details for an employee_id=5
i) Create a view which lists out the emp_name, department, basic, dedeuctions, netsalary
j) Create a view which lists the emp_name and his netsalary 
*/

create table employee(emp_id int(5) primary key,emp_name varchar2(25));
create table department(dept_id int(5) primary key,dept_name varchar2(20));
create table paydetails(emp_id int(5) references employee(emp_id),dept_id int(5) reerences department(dept_id),basic int(7,2),deductions int(5,2),additions int(5,2),doj date);
create table payroll(emp_id int(5)references employee(emp_id),pay_date date);
desc employee;
desc department;
desc paydetails;
desc payroll;
insert into employee values(&emp_id,’&emp_name’);
select * from employee;
insert  into department values(&dept_id,’&dept_name’);
select * from department;
insert into paydeatils values(&emp_id,&dept_id, &basic,&deductions,&additions,&doj);
select * from paydeatils;
insert into payroll values(&emp_id,’&date’);
select * from payroll;

/*
List all the employee names who joined after particular date
*/

SQL>select e,empname from employee e,paydet p where e.empid=p.empid
and p.doj>=’05-mar-06’;

/*
List the details of employees whose basic salary is between 10k and 20k
*/

SQL>Select empid,empname  from employee where salary between 10kand 20k;
select e.emp_id , e.emp_name,d.dept_id , d.dept_name , pd.basic from employee e , department d , paydetails pd , payroll pr where e.emp_id=pd.emp_id and d.dept_id=pd.dept_id and e.emp_id=pr.emp_id and pd.basic between 600 and 1000;

/*
Give a count of how many employees are working in each department
*/

SQL>select count(empid),deptid from paydet group by deptid;

/*
Give a names of the employees whose netsalary>10,000
*/

SQL> select empname from employee where empid in(select empid from
paydet where basic-deduction>10000);

/*
List the details for an employee_id=5
*/

sql> select * from employee where empid=5;

/*
Create a view which lists out the emp_name, department, basic, dedeuctions, netsalary
*/

create view vw as select e.emp_name , d.dept_name , pd.basic,pd.deductions , (pd.basic+pd.additions-pd.deductions) netsalary from employee e, department d, paydetails pd,payroll pr where e.emp_id=pd.emp_id and d.dept_id=pd.dept_id and e.emp_id=pr.emp_id  ;

select * from vw ;

/*
Create a view which lists the emp_name and his netsalary
*/
create view vew as select e.emp_name , (pd.basic+pd.additions-pd.deductions) netsalary from employee e, department d, paydetails pd,payroll pr where e.emp_id=pd.emp_id and d.dept_id=pd.dept_id and e.emp_id=pr.emp_id  ;

select * from vew ;

```
