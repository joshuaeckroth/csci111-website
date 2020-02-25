---
layout: post
title: student-db.py
---

# student-db.py

```
# Student database

# Record: student id (key), value is:
#  dictionary with name, grade, courses (list)

# Write code that creates a few students and prints
# their info

students = {"800984544": {"name": "Jane",
                          "grade": "Freshman",
                          "courses": ["CSCI 111", "MATH 125"]},
            "800463937": {"name": "James",
                          "grade": "Sophomore",
                          "courses": ["PSYC 101", "ECON 101"]}}

# Print Jane's grade (Freshman)
print(students["800984544"]["grade"])

# Print James' second course (ECON 101)
print(students["800463937"]["courses"][1])

# Print all student info
for studentid in students:
    courses = ', '.join(students[studentid]["courses"])
    name = students[studentid]["name"]
    grade = students[studentid]["grade"]
    print("%s %s, %s, %s" % (studentid, name, grade, courses))
```

