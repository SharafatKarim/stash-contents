## Problem set 1

Write the following queries in SQL, using this schema. The expected output is given for
each query when run on `large-university.db` (download this file and run SQLite locally via
`sqlite3` large-university.db or upload to the browser-based version).

1. Find the names of those departments whose budget is higher than that of Astronomy. List them in alphabetic order. 
```sql
SELECT 
    dept_name
FROM
    department
WHERE
    budget > (SELECT 
            budget
        FROM
            department
        WHERE
            dept_name = 'Astronomy');

# dept_name
'Athletics'
'Biology'
'Cybernetics'
'Finance'
'History'
'Math'
'Physics'
'Psychology'
            ```

2. Display a list of all instructors, showing each instructor&#39;s ID and the number of sections taught. Make sure to show the number of sections as 0 for instructors who have not taught any section. 
```sql
SELECT 
    I.ID, COUNT(T.ID) as number_of_sections
FROM
    instructor AS I
        NATURAL LEFT JOIN
    teaches AS T
GROUP BY I.ID
ORDER BY number_of_sections;

# ID, number_of_sections
'35579', '0'
'52647', '0'
'50885', '0'
'57180', '0'
'58558', '0'
'59795', '0'
'63395', '0'
'64871', '0'
'72553', '0'
'4034', '0'
'37687', '0'
'74426', '0'
'78699', '0'
'79653', '0'
'31955', '0'
'95030', '0'
'96895', '0'
'16807', '0'
'97302', '0'
'15347', '1'
'73623', '1'
'65931', '1'
'80759', '1'
'90376', '1'
'90643', '1'
'48570', '1'
'25946', '1'
'50330', '1'
'4233', '1'
'42782', '1'
'48507', '1'
'14365', '2'
'63287', '2'
'3335', '2'
'28400', '2'
'81991', '2'
'28097', '2'
'41930', '3'
'19368', '3'
'34175', '3'
'43779', '4'
'95709', '4'
'3199', '4'
'36897', '5'
'77346', '6'
'79081', '6'
'74420', '6'
'99052', '9'
'6569', '10'
'22591', '13'
```

3. For each student who has retaken a course at least twice (i.e., the student has taken the course at least three times), show the course ID and the student&#39;s ID. Please display your results in order of course ID and do not display duplicate rows. 
```sql
select distinct course_id, ID
	from takes
    group by ID, course_id having count(*) > 2
    order by course_id;

# course_id, ID
'362', '16480'
'362', '16969'
'362', '27236'
'362', '39925'
'362', '39978'
'362', '44881'
'362', '49611'
'362', '5414'
'362', '69581'
'362', '9993'
```

4. Find the names of Biology students who have taken at least 3 Accounting courses. 
```sql
select name
from student natural join (
	select ID from takes
	where course_id in ( select course_id from course
		where dept_name = "Accounting")
		group by ID having count(*) > 2
    ) as T where dept_name = "Biology";

SELECT s.name
FROM student s
JOIN takes t ON s.ID = t.ID
JOIN course c ON t.course_id = c.course_id
WHERE s.dept_name = 'Biology'
AND c.dept_name = 'Accounting'
GROUP BY s.ID
HAVING COUNT(*) > 2;

# name
'Michael'
'Dalton'
'Shoji'
'Wehen'
'Uchiyama'
'Schill'
'Kaminsky'
'Giannoulis'
```

5. Find the sections that had maximum enrollment in Fall 2010. 
```sql
SELECT course_id, sec_id 
FROM takes
WHERE semester = 'Fall' AND year = 2010
GROUP BY course_id, sec_id
HAVING COUNT(ID) = (
    SELECT MAX(enrollment_count) 
    FROM (
        SELECT COUNT(ID) AS enrollment_count
        FROM takes
        WHERE semester = 'Fall' AND year = 2010
        GROUP BY course_id, sec_id
    ) AS subquery
);

# course_id, sec_id
'867', '2'
```

6. Find student names and the number of law courses taken for students who have taken at least half of the available law courses. (These courses are named things like 'Tort Law' or 'Environmental Law'). 
```sql
select name, count(*)
from student as S
join takes T on S.ID = T.ID
where T.course_id in (
	select course_id
    from course
    where title like "%Law%" )
group by S.ID
having count(*) >= ( 
	select count(course_id) / 2 
	from (   
		select course_id
		from course
		where title like "%Law%" ) 
        as D 
	);

# name, count(*)
'Nakajima', '4'
'Nikut', '4'
'Hahn-', '4'
'Nanda', '4'
'Schinag', '4'
```

7. Find the rank and name of the 10 students who earned the most A grades (A-, A, A+). Use alphabetical order by name to break ties. Note: the browser SQLite does not support window functions. [**Ans didn't math with sample data**]
```sql
select row_number() over () as rnk, P.name from ( 
	select name, count(*) as cnt
	from student S
	join takes T on S.ID = T.ID
	where T.grade in ("A+", "A", "A-")
	group by T.ID
    ) as P
order by P.cnt desc, P.name
limit 10;

# rnk, name
'1', 'Lepp'
'2', 'Eller'
'3', 'Masri'
'4', 'Vries'
'5', 'Åström'
'6', 'Gandhi'
'7', 'Greene'
'8', 'Haigh'
'9', 'McCarter'
'10', 'Sanchez'
```

## Problem set 2
1. Find out the ID and salary of the instructors.
```sql
select ID, salary from instructor;

-- small database
# ID, salary
'10101', '65000.00'
'12121', '90000.00'
'15151', '40000.00'
'22222', '95000.00'
'32343', '60000.00'
'33456', '87000.00'
'45565', '75000.00'
'58583', '62000.00'
'76543', '80000.00'
'76766', '72000.00'
'83821', '92000.00'
'98345', '80000.00'

-- big database
# ID, salary
'14365', '32241.56'
'15347', '72140.88'
'16807', '98333.65'
'19368', '124651.41'
'22591', '59706.49'
'25946', '90891.69'
'28097', '35023.18'
'28400', '84982.92'
'31955', '71351.42'
'3199', '82534.37'
'3335', '80797.83'
'34175', '115469.11'
'35579', '62579.61'
'36897', '43770.36'
'37687', '104563.38'
'4034', '61387.56'
'41930', '50482.03'
'4233', '88791.45'
'42782', '34272.67'
'43779', '79070.08'
'48507', '107978.47'
'48570', '87549.80'
'50330', '108011.81'
'50885', '32570.50'
'52647', '87958.01'
'57180', '43966.29'
'58558', '66143.25'
'59795', '48803.38'
'63287', '103146.87'
'63395', '94333.99'
'64871', '45310.53'
'6569', '105311.38'
'65931', '79866.95'
'72553', '46397.59'
'73623', '90038.09'
'74420', '121141.99'
'74426', '106554.73'
'77346', '99382.59'
'78699', '59303.62'
'79081', '47307.10'
'79653', '89805.83'
'80759', '45538.32'
'81991', '77036.18'
'90376', '117836.50'
'90643', '57807.09'
'95030', '54805.11'
'95709', '118143.98'
'96895', '119921.41'
'97302', '51647.57'
'99052', '93348.83'
```
2. Find out the ID and salary of the instructor who gets more than $85,000.
```sql
select ID, salary from instructor
where salary > 85000;

-- small db
# ID, salary
'12121', '90000.00'
'22222', '95000.00'
'33456', '87000.00'
'83821', '92000.00'

-- big db
# ID, salary
'16807', '98333.65'
'19368', '124651.41'
'25946', '90891.69'
'34175', '115469.11'
'37687', '104563.38'
'4233', '88791.45'
'48507', '107978.47'
'48570', '87549.80'
'50330', '108011.81'
'52647', '87958.01'
'63287', '103146.87'
'63395', '94333.99'
'6569', '105311.38'
'73623', '90038.09'
'74420', '121141.99'
'74426', '106554.73'
'77346', '99382.59'
'79653', '89805.83'
'90376', '117836.50'
'95709', '118143.98'
'96895', '119921.41'
'99052', '93348.83'
```
3. Find out the department names and their budget at the university.
```sql
select dept_name, budget from department;

-- small db
# dept_name, budget
'Biology', '90000.00'
'Comp. Sci.', '100000.00'
'Elec. Eng.', '85000.00'
'Finance', '120000.00'
'History', '50000.00'
'Music', '80000.00'
'Physics', '70000.00'

-- big db
# dept_name, budget
'Accounting', '441840.92'
'Astronomy', '617253.94'
'Athletics', '734550.70'
'Biology', '647610.55'
'Civil Eng.', '255041.46'
'Comp. Sci.', '106378.69'
'Cybernetics', '794541.46'
'Elec. Eng.', '276527.61'
'English', '611042.66'
'Finance', '866831.75'
'Geology', '406557.93'
'History', '699140.86'
'Languages', '601283.60'
'Marketing', '210627.58'
'Math', '777605.11'
'Mech. Eng.', '520350.65'
'Physics', '942162.76'
'Pol. Sci.', '573745.09'
'Psychology', '848175.04'
'Statistics', '395051.74'
```
4. List out the names of the instructors from Computer Science who have more than $70,000.
```sql
desc instructor;
select name from instructor
where salary > 70000;

-- small db
# name
'Wu'
'Einstein'
'Gold'
'Katz'
'Singh'
'Crick'
'Brandt'
'Kim'

-- big db
# name
'Bawa'
'Yazdi'
'Wieland'
'Liley'
'Atanassov'
'Moreira'
'Gustafsson'
'Bourrier'
'Bondi'
'Arias'
'Luo'
'Romero'
'Lent'
'Sarkar'
'Shuming'
'Bancilhon'
'Jaekel'
'McKinnon'
'Mingoz'
'Pimenta'
'Sullivan'
'Voronina'
'Kenje'
'Mahmoud'
'Levine'
'Valtchev'
'Bietzk'
'Sakurai'
'Mird'
'Dale'
```
5. For all instructors in the university who have taught some course, find their names and the course ID of
all courses they taught.
6. Find the names of all instructors whose salary is greater than at least one instructor in the Biology
department.

7. Find the advisor of the student with ID 12345
8. Find the average salary of all instructors.
9. Find the names of all departments whose building name includes the substring &#39;Watson&#39;.
10. Find the names of instructors with salary amounts between $90,000 and $100,000.
11. Find the instructor names and the courses they taught for all instructors in the Biology department who
have taught some course.
12. Find the courses taught in Fall-2009 semester.
13. Find the set of all courses taught either in Fall-2009 or in Spring-2010.
14. Find the set of all courses taught in the Fall-2009 as well as in Spring-2010.
15. Find all courses taught in the Fall-2009 semester but not in the Spring-2010 semester.
16. Find all instructors who appear in the instructor relation with null values for salary.
17. Find the average salary of instructors in the Finance department.
18. Find the total number of instructors who teach a course in the Spring-2010 semester.
19. Find the average salary in each department.
20. Find the number of instructors in each department who teach a course in the Spring-2010 semester.
21. List out the departments where the average salary of the instructors is more than $42,000.
22. For each course section offered in 2009, find the average total credits (tot cred) of all students enrolled
in the section, if the section had at least 2 students.
23. Find all the courses taught in both the Fall-2009 and Spring-2010 semesters.
24. Find all the courses taught in the Fall-2009 semester but not in the Spring-2010 semester.
25. Select the names of instructors whose names are neither &quot;Mozart&quot; nor &quot;Einstein&quot;.
26. Find the total number of (distinct) students who have taken course sections taught by the instructor
with ID 110011.
27. Find the ID and names of all instructors whose salary is greater than at least one instructor in the History
department.
28. Find the names of all instructors that have a salary value greater than that of each instructor in the
Biology department.
29. Find the departments that have the highest average salary.
30. Find all courses taught in both the Fall 2009 semester and in the Spring-2010 semester.
31. Find all students who have taken all the courses offered in the Biology department.
32. Find all courses that were offered at most once in 2009.
33. Find all courses that were offered at least twice in 2009.
34. Find the average instructors&#39; salaries of those departments where the average salary is greater than
$42,000.
35. Find the maximum across all departments of the total salary at each department.
36. List all departments along with the number of instructors in each department.

## Problem set 3

37. Find the titles of courses in the Comp. Sci. department that have 3 credits.
38. Find the IDs of all students who were taught by an instructor named Einstein; make
sure there are no duplicates in the result.
39. Find the ID and name of each student who has taken at least one Comp. Sci. course;
make sure there are no duplicate names in the result.
40. Find the course id, section id, and building for each section of a Biology course.
41. Output instructor names sorted by the ratio of their salary to their department&#39;s budget
(in ascending order).
42. Output instructor names and buildings for each building an instructor has taught in.
Include instructor names who have not taught any classes (the building name should
be NULL in this case).
43. Find the names of those departments whose budget is higher than that of Astronomy.
List them in alphabetic order.1
44. Output instructor names and buildings for each building an instructor has taught in.
Include instructor names who have not taught any classes (the building name should
be NULL in this case).
45. For each student who has retaken a course at least twice (i.e., the student has taken the
course at least three times), show the course ID and the student&#39;s ID. Please display
your results in order of course ID and do not display duplicate rows.

46. Find the names of Biology students who have taken at least 3 Accounting
courses
47. Find the rank and name of the 10 students who earned the most A grades (A-,
A, A+). Use alphabetical order by name to break ties. Note: the browser SQLite does
not support window functions.