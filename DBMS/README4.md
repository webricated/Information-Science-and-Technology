```cmd


/* 4.	Consider the following relational schema for the Office of the Controller of Examinations Application. */

Student (Rollno, Name, Dob, Gender, Doa, Bcode);


/* Implement a check constraint for Gender */


Branch (Bcode, Bname, Dno);
Department (Dno, Dname);
Course (Ccode, Cname, Credits, Dno);
Branch_Course (Bcode, Ccode, Semester);
Enrolls (Rollno, Ccode, Sess, Grade);
For Example,SESS can take values ‘MAY2019’, ‘DEC2019’ 
Implement a check constraint for grade Value Set (‘S’, ‘A’, ‘B’, ‘C’, ‘D’, ‘E’, ‘U’ );


/* Students are admitted to Branches and they are offered by Departments. 
A branch is offered by only one department.Each branch has a set of Courses (Subjects). 
Each student must enroll during a semester. Courses are offered by Departments. 
A course is offered only by one department. 
If a student is unsuccessful in a course he/she must enroll for the course during next session. 
A student has successfully completed a course if the grade obtained by is from the list (A, B, C, D, and E).A student is unsuccessful if he/she have grade ‘U’ in a course.
Primary Keys are underlined.
a)	Develop a SQL query to list details of Departments that offer more than 3 branches.
b)	Develop a SQL query to list the details of Departments that offer more than 6 courses.
c)	Develop a SQL query to list the details of courses that are common for more than 3 branches.
d)	Develop a SQL query to list students who got ‘S’ in more than 2 courses during single enrollment.
e)	Create a view that will keep track of the roll number, name and number of courses, a student has completed successfully. */



CREATE TABLE DEPARTMENT (DNO NUMBER (2), DNAME VARCHAR2 (20));
ALTER TABLE DEPARTMENT ADD PRIMARY KEY (DNO);
CREATE TABLE BRANCH (BCODE NUMBER (3), BNAME VARCHAR2 (25), DNO NUMBER (2));
ALTER TABLE BRANCH ADD PRIMARY KEY (BCODE);
ALTER TABLE BRANCH ADD FOREIGN KEY (DNO) REFERENCES DEPARTMENT (DNO);
CREATE TABLE BRANCH_COURSE (BCODE NUMBER(3), CCODE NUMBER(4), SEMESTER NUMBER(2));
ALTER TABLE BRANCH_COURSE ADD PRIMARY KEY (BCODE, CCODE);
ALTER TABLE BRANCH_COURSE ADD FOREIGN KEY (BCODE) REFERENCES BRANCH (BCODE);
ALTER TABLE BRANCH_COURSE ADD FOREIGN KEY (CCODE) REFERENCES COURSE (CCODE);
CREATE TABLE STUDENT (ROLLNO NUMBER (5), NAME VARCHAR2 (20), DOB DATE, GENDER CHAR(2), DOA DATE, BCODE NUMBER(3));
ALTER TABLE STUDENT ADD PRIMARY KEY (ROLLNO);
ALTER TABLE STUDENT ADD FOREIGN KEY (BCODE) REFERENCES BRANCH (BCODE);
ALTER TABLE ADD CONSTRAINT CHK CHECK (GENDER IN ('M','F'));
ALTER TABLE ADD CONSTRAINT CHK2 CHECK (DOA < TO_DATE('31-4-2016,'DD-MM-YYYY');
CREATE TABLE COURSE (CCODE NUMBER (4), CNAME VARCHAR2 (25), CREDITS NUMBER (2), DNO NUMBER (2));
ALTER TABLE COURSE ADD PRIMARY KEY (CCODE);
ALTER TABLE COURSE ADD FOREIGN KEY (DNO) REFERENCES DEPARTMENT (DNO));
CREATE TABLE ENROLLS (ROLLNO NUMBER (5), CCODE NUMBER (4), SESS VARCHAR2 (15), GRADE CHAR (2));
ALTER TABLE ENROLLS ADD PRIMARY KEY (ROLLNO, CCODE, SESS);
ALTER TABLE ENROLLS ADD FOREIGN KEY ROLLNO) REFERENCES STUDENT(ROLLNO);
ALTER TABLE ENROLLS ADD FOREIGN KEY (CCODE) REFERENCES COURSE (CCODE);


/* Insert data into the Tables */

INSERT INTO COURSE VALUES (1011, 'LINEAR ALGEBRA', 2,1);
INSERT INTO STUDENT VALUES ( 12001, 'RAMESH KAUSHIK', TO_DATE( '3-4-1989',DD-MM-YYYY') ,'M' , TO_DATE( '24-4-2016','DD-MM-YYYY'), 110);
INSERT INTO ENROLLS VALUES( 12001, 1112, 'APRIL2013','D');


/* QUERIES
Develop a SQL query to list details of Departments that offer more than 3 branches.
*/

SELECT * FROM DEPARTMENT D WHERE D.DNO IN (SELECT B.DNO FROM BRANCH B GROUP BY B.DNO HAVING COUNT (B.DNO) > 3);


/* Develop a SQL query to list the details of Departments that offer more than 6 courses. */


SELECT * FROM DEPARTMENT D WHERE D.DNO IN (SELECT C.DNO FROM COURSE C GROUP BY C.DNO HAVING COUNT (C.CCODE) > 6);

/* Develop a SQL query to list the details of courses that are common for more than 3 branches. */

SELECT * FROM COURSE C WHERE C.CCODE IN (SELECT B.CCODE FROM BRANCH_COURSE B GROUP BY B.CCODE HAVING COUNT (B.BCODE) > 3);

/* Develop a SQL query to list students who got ‘S’ in more than 2 courses during single enrollment. */

SELECT * FROM STUDENT S WHERE S.ROLLNO IN (SELECT E.ROLLNO FROM ENROLLS E WHERE E.GRADE = 'S' GROUP BY E.ROLLNO HAVING COUNT (E.GRADE) > 2);

/* Create a view that will keep track of the roll number, name and number of courses, a student has completed successfully. */


CREATE VIEW STUDATA AS SELECT E.ROLLNO, S.NAME, COUNT (E.CCODE) AS CC FROM STUDENT S, ENROLLS E WHERE E.ROLLNO = S.ROLLNO AND E.GRADE ! = 'U' GROUP BY E.ROLLNO, S.NAME;

```
