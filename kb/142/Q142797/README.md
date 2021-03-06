---
layout: page
title: "Q142797: FIX: Allow Nulls on Field Change Results of SELECT-SQL"
permalink: /kb/142/Q142797/
---

## Q142797: FIX: Allow Nulls on Field Change Results of SELECT-SQL

{% raw %}

	Article: Q142797
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The results of a three-table join are different if the key field is set to allow
	NULL values.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Microsoft Visual
	FoxPro 3.0b for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Use the following commands to create three tables to use in the join.
	
	     CREATE DATABASE grader
	
	     CREATE TABLE students ;
	        (student_id C(10), stu_lname C(30), stu_fname C(30))
	     ALTER TABLE students ADD PRIMARY KEY student_id TAG student_id
	     INSERT INTO students VALUES ;
	        ('0000000001', 'Slade', 'Cameron')
	     INSERT INTO students VALUES ;
	        ('0000000002', 'Larson', 'Debby')
	     INSERT INTO students VALUES ;
	        ('0000000003', 'Kautzman', 'Pat')
	     INSERT INTO students VALUES ;
	        ('0000000004', 'Lund', 'Tres')
	
	     CREATE TABLE classes ;
	        (class_id C(6), room_num C(5), period C(2), ;
	        subject C(30), instructor C(6))
	     ALTER TABLE classes ADD PRIMARY KEY class_id TAG class_id
	     INSERT INTO classes VALUES ;
	        ('BUS125', '2/103', '1', 'Business Law', '')
	     INSERT INTO classes VALUES ;
	        ('HOM132', '1/101', '2', 'Home Economics', '')
	
	     CREATE TABLE classmem ;
	        (student_id C(10), class_id C(6), grade C(2))
	     INDEX ON student_id TAG student_id
	     INDEX ON class_id TAG class_id
	     INSERT INTO classmem VALUES ('0000000001', 'BUS125', 'A')
	     INSERT INTO classmem VALUES ('0000000002', 'BUS125', 'B')
	     INSERT INTO classmem VALUES ('0000000003', 'BUS125', 'C')
	     INSERT INTO classmem VALUES ('0000000001', 'HOM132', 'A')
	     INSERT INTO classmem VALUES ('0000000002', 'HOM132', 'A')
	     INSERT INTO classmem VALUES ('0000000004', 'HOM132', 'A')
	
	2. Use the following SELECT command to join the three tables:
	
	     SELECT stu_lname, stu_fname, subject, grade ;
	        FROM students, classes, classmem ;
	        WHERE students.student_id = classmem.student_id ;
	        AND classmem.class_id = classes.class_id ;
	        ORDER BY subject
	
	  Notice that the result is six records.
	
	3. Modify the structure of the Students table, and place a check in the NULL
	  column of the student_id field so that it will allow NULL values.
	
	     SELECT students
	     MODIFY STRUCTURE
	
	4. Rerun the SELECT command shown in step 2. In Visual FoxPro 3.0, the result is
	  no records. In Visual FoxPro 3.0b, the result is six records as expected.
	
	Additional query words: VFoxWin buglist3.00 fixlist3.00b
	
	======================================================================
	Keywords          :  kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
