# Data Science Module 3: Python Functions (Part 2)

Practical notebook from the **Virel Digital Data Science Programme, Day 03**. It covers advanced Python functions and ends with a supermarket sales analysis mini project.

**Notebook:** `Data_Science_Module_3.ipynb` (built in Google Colab)

## Topics Covered

1. Multiple parameters
2. Default arguments
3. Keyword arguments
4. Returning multiple values
5. Mini project: Supermarket weekly sales analysis (function composition)

---

## 1. Multiple Parameters

A function can accept more than one input.

```python
def calculate_area(length, width):
    area = length * width
    return area

print(calculate_area(12, 5))
```

**Output**
```
60
```

---

## 2. Default Arguments

A default argument is used when the caller does not supply a value.

```python
def calculate_salary(basic_salary, bonus=2000):
    salary = basic_salary + bonus
    return salary

print(calculate_salary(30000))
```

**Output**
```
32000
```

Overriding the default:

```python
print(calculate_salary(30000, 5000))
```

**Output**
```
35000
```

---

## 3. Keyword Arguments

Values are passed by parameter name, so order does not matter.

```python
def employee_details(name, department, salary):
    return f"Name: {name}, Department: {department}, Salary: {salary}"

# Calling the function using keyword arguments
print(employee_details(department="Data science", name="Evance", salary=30000))
```

**Output**
```
Name: Evance, Department: Data science, Salary: 30000
```

---

## 4. Returning Multiple Values

`*marks` accepts any number of arguments. The returned values are packed into a tuple.

```python
def student_perfomance(*marks):
    total_marks = sum(marks)
    average_marks = total_marks / len(marks)
    highest_marks = max(marks)
    lowest_marks = min(marks)
    return total_marks, average_marks, highest_marks, lowest_marks

print(student_perfomance(65, 80, 75, 90, 70))
```

**Output**
```
(380, 76.0, 90, 65)
```

---

## 5. Mini Project: Supermarket Weekly Sales Analysis

**Objective:** Use functions to analyse a week of supermarket sales and generate a report showing total sales, average daily sales, and the highest and lowest sales days.

### Step 1: Create the dataset

```python
sales = {
    "Monday": 4500,
    "Tuesday": 6000,
    "Wednesday": 3500,
    "Thursday": 8000,
    "Friday": 7000,
    "Saturday": 9500,
    "Sunday": 5000
}
```

### Step 2: Calculate total weekly sales

```python
def calculate_total(sales):
    return sum(sales.values())

print(calculate_total(sales))
```

**Output**
```
43500
```

### Step 3: Calculate average daily sales

```python
def calculate_average(sales):
    return sum(sales.values()) / len(sales)

print(calculate_average(sales))
```

**Output**
```
6214.285714285715
```

### Step 4: Identify the highest sales day

```python
def highest_sales_day(sales):
    return max(sales, key=sales.get)

print(highest_sales_day(sales))
```

**Output**
```
Saturday
```

### Step 5: Identify the lowest sales day

```python
def lowest_sales_day(sales):
    return min(sales, key=sales.get)

print(lowest_sales_day(sales))
```

**Output**
```
Wednesday
```

### Step 6: Generate a complete sales report

```python
def sales_report(sales):

    total = calculate_total(sales)
    average = calculate_average(sales)
    highest = highest_sales_day(sales)
    lowest = lowest_sales_day(sales)

    print("SUPERMARKET WEEKLY SALES REPORT")
    print("--------------------------------")
    print("Total weekly sales:", total)
    print("Average daily sales:", round(average, 2))
    print("Highest sales day:", highest)
    print("Lowest sales day:", lowest)


sales_report(sales)
```

**Output**
```
SUPERMARKET WEEKLY SALES REPORT
--------------------------------
Total weekly sales: 43500
Average daily sales: 6214.29
Highest sales day: Saturday
Lowest sales day: Wednesday
```

### Findings

| Metric | Result |
|---|---:|
| Total weekly sales | KSh 43,500 |
| Average daily sales | KSh 6,214.29 |
| Highest sales day | Saturday (KSh 9,500) |
| Lowest sales day | Wednesday (KSh 3,500) |

**Interpretation:** Saturday was the strongest day and Wednesday the weakest. A manager could investigate what drives Saturday sales and plan strategies to lift midweek sales.

---

## Key Takeaways

- Functions make code reusable and easier to maintain.
- Default arguments make inputs optional.
- Keyword arguments improve readability and remove order dependence.
- Functions can return multiple values as a tuple.
- Small functions can be combined to solve bigger problems (function composition).


