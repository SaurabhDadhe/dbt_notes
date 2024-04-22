===========================================Day6=====================================
1. equijoin
select dname, ename from emp, dept
where dept.deptno = emp. deptno
and dname = 'TRN';

DNAME 		ENAME
TRN 		Arun
TRN		Ali
-----------------------------------------------------------------------------------------------------------

2. Inequijoin
select dname, ename from emp, dept
where dept.deptno != emp.deptno
and dname = 'TRN'•,

DNAPIE 		ENAME
TRN 		Jack
TRN		Thomas

-----------------------------------------------------------------------------------------------------------
3. Outerjoin
*join with a (+) sign
*shows matching rows of both the tables
plus
non-matching	rows of	"Outer" table
*Outer table	-Y table	which is on Outer side of (+) sign
*Outer table	-Y table	which is on Opposite side of (+) sign
*Uses:-
	a. master-Detail Report (Parent-Child Report)
select dname, ename from emp, dept
where dept.deptno = emp.deptno (+) ;

DNAME 		ENAME
TRN 		Arun
TRN 		Ali
TRN 		Kirun
EXP 		Jack
EXP 		Thomas
MKTG		


**Suppose i put (+) Sign on left side
---------------
select dname, ename from emp, dept
where dept.deptno (+) = emp.deptno;
DNAME 		ENAME
TRN 		Arun
TRN	 	Ali
TRN 		Kirun
EXP 		Jack
EXP 		Thomas
		Scott

---------------------------
a. Half Outerjoin
(+) sign on any 1 side, i.e.	LHS or RI-IS
i. Right Outerjoin ( (+) sign	on RI-IS)
ii. Left Outerjoin ((+) sign	on LHS)
select dname, ename from emp, dept
 where dept.deptno =emp.deptno (+) ;		Right Outerjoin
select dname, ename from emp, dept
where dept.deptno (+)= emp.deptno;		Left Outerjoin
**ANSI syntax for Right Outerjoin:-
	select dname, ename from emp right outer join dept
	on (dept.deptno = emp. deptno) ;

**ANSI syntax for Left Outerjoin:-
	select dname, ename from emp left outer join dept
	on (dept.deptno = emp.deptno);
-----------------------------
Full Outerjoin
*** Suppose the table has 6th row as follows
EMP
empno 	ename 	sal 		deptno 	job 		mgr
------ 	------ 	----- 	-	----- 		------ 	-------
	1 	Arun 	8000 	1 		M 		4
	2 	Ali 		7000 	1 		C 		1
	3 	Kirun 	3000 	1 		C 		1
	4 	Jack 	9000 	2 		M 		null
	5 	Thomas 	8000 	2 		C 		4
	6 	Scott 	6000 	99

select dname, ename from emp, dept
where dept.deptno = emp.deptno (+)
		union
select dname, ename from emp, dept
where dept.deptno (+) = emp.deptno;
DNAME 		ENAME
TRN 		Arun
TRN 		Ali
TRN 		Kirun
EXP 		Jack
EXP 		Thomas
MKTG
			Scott

*shows matching rows of both the tables
plus
non-matching rows of both the tables
*based on Nested Do-While loop
**ANSI syntax for Full Outerjoin:-
	select dname, ename from emp full outer join dept
	on (dept.deptno = emp.deptno);

*We can't you plus (+) on the both side therefore we need to use full outerjoin
*definition of full outerjoin is that it that shows the matching data of both the table and non matching data of both table
---------------------------
**(+) sign for Outerjoin is not supported in MySQL
**ANSI syntax for Right Outerjoin:-
*supported by MySQL
	select dname, ename from emp right outer join dept
	on (dept.deptno = emp. deptno) ;

**ANSI syntax for Left Outerjoin:-
*supported by MySQL
	select dname, ename from emp left outer join dept
	on (dept.deptno = emp.deptno);

**ANSI syntax for Full Outerjoin:-
*not supported by MySQL
	*To create Full Outerjoin in MySQL:-
		select dname, ename from emp right outer join dept
		on (dept.deptno = emp. deptno)
			union
		select dname, ename from emp left outer join dept
		on (dept.deptno =emp. deptno) ;

-----------------------------------------------------------------------------------------------------------

***Innerjoin
*DO NOT MENTION UNLESS EXPLICITLY ASKED IN INTERVIEWS
*By default every join is an Inner join; using a (+) sign or using
the keyword "Outer" is what makes it an Outerjoin

-----------------------------------------------------------------------------------------------------------

4. Cartesian	join
join	without a WHERE clause
every row of driving table is combined with each and every row of
driven table
cross product of 2 tables and therefore it's also known as Cross
boin
select dname,	ename from emp, dept;

