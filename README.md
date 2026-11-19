# Student Result Management System (C++)

**Course:** 25ECE121 – Object-Oriented Programming using C++ Lab
**Task:** Task 2 (Weeks 7–13)
**Institution:** Nitte Meenakshi Institute of Technology (NMIT), Dept. of Electronics and Communication Engineering

A menu-driven C++ program that stores student marks, validates them, computes totals, percentages and grades, saves and loads records from a text file, and filters students above a given total.

---

## Features

- Add students with USN, name and marks in five subjects (Maths, Physics, Electronics, OOP, Signals)
- Marks validated to the range 0–100; invalid records are rejected with an error message
- Duplicate USNs are refused
- Automatic total, percentage, grade and PASS/FAIL result
- Save records to and load records from `students.txt` (corrupt lines are skipped)
- List students scoring above a chosen total, sorted in descending order
- Highest total in the class shown with a function template

## Grading Rules

A student passes only if **every** subject mark is at least 40.

| Grade | Condition |
|-------|-----------|
| S | 90% and above |
| A | 80–89% |
| B | 70–79% |
| C | 60–69% |
| D | 50–59% |
| E | Below 50% (all subjects passed) |
| F | Failed in any subject |

## C++ Concepts Demonstrated

| Concept | Where it is used |
|---------|------------------|
| Inheritance | `Result` publicly inherits from `Student` |
| Runtime polymorphism | `displayDetails()`, `displayMarks()`, `getTotal()`, `toRecord()` are virtual and overridden in `Result`; called through `Student` pointers |
| Virtual destructor | `Student` has a virtual destructor for safe deletion via base pointers |
| Exception handling | Custom `InvalidMarksException` (derived from `std::exception`), plus `std::invalid_argument` and `std::runtime_error` |
| File handling | `ofstream` / `ifstream` with `getline` and `stringstream` |
| Templates | `getHighest<T>()` returns the largest value in a vector |
| STL containers | `std::vector<std::unique_ptr<Student>>` and `std::vector<int>` |
| STL algorithms and lambdas | `for_each`, `sort`, `any_of`, `all_of`, `max_element` |

## Class Overview

```
Student (base)                Result (derived)
├─ usn, name                  ├─ vector<int> marks, int total
├─ virtual displayDetails()   ├─ getPercentage(), hasPassed(), getGrade()
├─ virtual displayMarks()     └─ overrides: displayDetails(), displayMarks(),
├─ virtual getTotal()                       getTotal(), toRecord()
└─ virtual toRecord()
```

## Getting Started

### Requirements

- A C++17 compiler (developed with `g++ 13.3.0` on Ubuntu 24.04)

### Compile

```bash
g++ -std=c++17 -Wall -Wextra -o result_system main.cpp
```

> Replace `main.cpp` with the name of your source file.

### Run

```bash
./result_system
```

On Windows, run `result_system.exe` instead.

## Usage

```
===== Student Result Management System =====
1. Add student
2. Display all students
3. Show students scoring above a total
4. Save records to file
5. Load records from file
6. Exit
Enter choice:
```

1. **Add student**: enter USN, name and five marks. Invalid marks throw an exception and the record is not stored.
2. **Display all students**: shows details, subject marks, total, percentage, grade, result and the highest total.
3. **Show students above a total**: enter a minimum total and matching students are listed in descending order.
4. **Save**: writes all records to `students.txt`.
5. **Load**: reads records back from `students.txt`, replacing the current list.
6. **Exit**: quits the program.

### Data File Format

Each record is one line in `students.txt`:

```
USN|Name|Maths|Physics|Electronics|OOP|Signals
```

Example:

```
7890|RAM|98|80|90|98|96
```

## Sample Output

```
===== STUDENT RESULTS (1 records) =====
----------------------------------------
USN : 7890
Name: RAM
Total Marks: 462 / 500   Percentage: 92.40%
  Maths       : 98
  Physics     : 80
  Electronics : 90
  OOP         : 98
  Signals     : 96
Result: PASS   Grade: S
----------------------------------------
Highest total in class: 462
```

## Repository Structure

```
.
├── main.cpp          # Source code
├── students.txt      # Saved records (created when you save)
├── screenshots/      # Output screenshots
├── Report.pdf        # Task 2 lab report
└── README.md
```

## Author

- **Name:** _Your Name_
- **USN:** _Your USN_
- **Section / Batch:** _Your Section_

## Declaration

This project was completed as part of the OOP using C++ Lab coursework and represents my own work.
