---
layout: page
title: "Table Variables and Set operators"
tags: [isuki, sql_custom, table variables, set operator, random tag, tcsobay]
---

> create table College(cName VARCHAR(60), state VARCHAR(60), enrollment int);
> create table Student(sID int, sName VARCHAR(60), GPA real, sizeHS int);
> create table Apply(sID int, cName VARCHAR(60), major VARCHAR(60), decision VARCHAR(60));



###  IDs of students who applied to CS but not EE

```sql
SELECT sID FROM Apply WHERE major = 'CS'
except
SELECT sID FROM Apply WHERE major = 'EE';
```

###  IDs of students who applied to CS but not EE
  Some systems don't support except

```sql
SELECT A1.sID
FROM Apply A1, Apply A2
WHERE A1.sID = A2.sID
	AND A1.major = 'CS'
	AND A2.major <> 'EE';
```
