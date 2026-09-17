 ELIGIBILITY AND RESULT TESTING SYSTEM  FOR UNIVERSITY
Group 23
GROUP MEMBERS:
BRUCE KARITI     C026-01-0969/2025
KELVIN MUSINA    C026-01-0946/2025
ALLAN CHESIPUL   C026-01-0946/2025
System Description
This is a system written in c that checks all requirement for student to sit for an exam and also processes students results. 

The system stores student information using a struct, validates marks, checks examination eligibility, calculates total marks, assigns grades, displays results, calculates basic statistics.

Eligibility Rules
A student is eligible when:

The fee balance is zero.
An examination card is available.
The student has registered for between 4 and 8 units.
The student has no disciplinary restriction.
The marks entered are within the permitted ranges.
Mark Ranges
CAT: 0–30
Practical: 0–20
Examination: 0–50
Maximum total: 100
Grading
Total	Grade
70–100	A
60–69	B
50–59	C
40–49	D
Below 40	F
How the System Works
A dynamic dataset of students is created using malloc.
Each student's information is stored in a Student structure.
Marks are validated.
Examination eligibility is checked using the fee, examination-card, unit, and disciplinary conditions.
CAT, practical, and examination marks are added to obtain the total.
A grade is assigned according to the total mark.
Student results are displayed.
Basic statistics are calculated.
Tests demonstrate important system conditions and C programming concepts.
Dynamically allocated memory is released using free.
Programming Language
C

Programming Language Concepts Demonstrated
The program uses different variables with different data types and storage characteristics.

Named Constants
#define is used for fixed values such as MIN_UNITS, MAX_UNITS, MAX_CAT, and PASS_MARK.

L-values and R-values
The program demonstrates the difference between an l-value, which identifies a storage location, and an r-value, which represents a value used in an expression.

Aliasing and Pointers
moderateMark receives a pointer to a mark, allowing a function to modify the original value. Pointer aliasing is also demonstrated in the tests.

Scope
The program contains global and local variables. systemVersion is global while variables inside functions have local/block scope.

Static Storage
The global variable systemVersion has static storage duration.

Dynamic Storage
Student records are dynamically allocated using malloc and released using free.

Structures
The Student structure groups related student information into one data type.

Modularity
The program is divided into functions such as validateMarks, checkEligibility, processStudent, displayStudentResult, and calculateStatistics.