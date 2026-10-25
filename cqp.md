# Python and Quantum Computing Experiments

Compiled from the 15 PDFs supplied from `F:\pqc`. Code is arranged by experiment number and source-document order. Printed notebook outputs are omitted. Typographic corrections and small fixes needed to make examples work are noted in the final section.

## Experiment 1 — Basic concepts and arithmetic (`sampleex1.pdf`)

### Hello World
```python
print("Hello World!\n")
```

### Swap variables
```python
A = 5
B = 10
print("Before Swap:\nA =", A, "\nB =", B)
A, B = B, A
print("\nAfter Swap:\nA =", A, "\nB =", B, "\n")
```

### Personal information output
```python
Name = "David"
Age = 19
Gender = "Female"
Course = "Computer Science"
Address = "Seattle"
print("Name:", Name)
print("Age:", Age)
print("Gender:", Gender)
print("Course:", Course)
print("Address:", Address, "\n")
```

### Personal information using input
```python
Name_Input = input("Enter Name: ")
Age_Input = input("Enter Age: ")
Course_Input = input("Enter Course: ")
Address_Input = input("Enter Address: ")
print("\nName:", Name_Input)
print("Age:", Age_Input)
print("Course:", Course_Input)
print("Address:", Address_Input, "\n")
```

### Average calculation
```python
X = 20
Y = 30
Z = 40
Average = (X + Y + Z) / 3
print("Average =", Average, "\n")
```

### Circle area and circumference
```python
Radius = 20
Pi = 3.14
Area = Pi * (Radius ** 2)
Circumference = 2 * Pi * Radius
print("Area =", Area)
print("Circumference =", Circumference, "\n")
```

### Simple interest
```python
Principal = float(input("Enter the principal amount (P): "))
Rate = float(input("Enter the annual interest rate (R): "))
Time = float(input("Enter the time period in years (T): "))
Simple_Interest = (Principal * Rate * Time) / 100
print("\nSimple Interest =", Simple_Interest, "\n")
```

### Compound amount
```python
Principal = float(input("Enter the principal amount (P): "))
Rate = float(input("Enter the annual interest rate in % (R): "))
Time = float(input("Enter the time period in years (T): "))
Compound_Amount = Principal * (1 + Rate / 100) ** Time
Compound_Interest = Compound_Amount - Principal
print("\nCompound Interest =", Compound_Interest, "\n")
```

## Experiment 2 — Control structures (`sampleex2.pdf`)

### Largest of three numbers
```python
A = int(input("Enter first number: "))
B = int(input("Enter second number: "))
C = int(input("Enter third number: "))
if A >= B and A >= C:
    print(f"\nThe largest number is: {A}\n")
elif B >= C:
    print(f"\nThe largest number is: {B}\n")
else:
    print(f"\nThe largest number is: {C}\n")
```

### Even or odd
```python
Num = int(input("Enter a number: "))
if Num % 2 == 0:
    print("The number is Even.\n")
else:
    print("The number is Odd.\n")
```

### Positive, negative, or zero
```python
Num = int(input("Enter a number: "))
if Num > 0:
    print("The number is Positive.\n")
elif Num < 0:
    print("The number is Negative.\n")
else:
    print("The number is Zero.\n")
```

### Leap year
```python
Year = int(input("Enter a year: "))
if Year % 400 == 0 or (Year % 4 == 0 and Year % 100 != 0):
    print("Year is leap.\n")
else:
    print("Year is not leap.\n")
```

### Pass or fail
```python
Marks = int(input("Enter the marks: "))
if Marks >= 35:
    print("Result: Pass\n")
else:
    print("Result: Fail\n")
```

## Experiment 8 — Control structures and loops (`sampleex8.pdf`)

### Largest of three numbers
```python
A = float(input("Enter first number: "))
B = float(input("Enter second number: "))
C = float(input("Enter third number: "))
if A >= B and A >= C:
    print("The largest number is:", A, "\n")
elif B >= C:
    print("The largest number is:", B, "\n")
else:
    print("The largest number is:", C, "\n")
```

### Even or odd
```python
Num = int(input("Enter a number: "))
if Num % 2 == 0:
    print("The number is Even.\n")
else:
    print("The number is Odd.\n")
```

### Positive, negative, or zero
```python
Num = float(input("Enter a number: "))
if Num > 0:
    print("The number is Positive.\n")
elif Num < 0:
    print("The number is Negative.\n")
else:
    print("The number is Zero.\n")
```

### Pass or fail
```python
Marks = float(input("Enter the student's marks: "))
if Marks >= 40:
    print("Result: Pass\n")
else:
    print("Result: Fail\n")
```

### Grade calculation
```python
Marks = float(input("Enter the student's marks: "))
if Marks >= 90:
    print("Grade: A\n")
elif Marks >= 80:
    print("Grade: B\n")
elif Marks >= 70:
    print("Grade: C\n")
elif Marks >= 60:
    print("Grade: D\n")
else:
    print("Grade: F\n")
```

### Income tax calculation
```python
Income = float(input("Enter your annual income: "))
if Income <= 250000:
    Tax = 0
elif Income <= 500000:
    Tax = (Income - 250000) * 0.05
elif Income <= 1000000:
    Tax = 12500 + (Income - 500000) * 0.20
else:
    Tax = 112500 + (Income - 1000000) * 0.30
print("Income Tax =", Tax, "\n")
```

### Print 1 to N
```python
N = int(input("Enter a number: "))
for i in range(1, N + 1):
    print(i)
print("\n")
```

### Reverse while loop (N to 1)
```python
N = int(input("Enter a number: "))
while N >= 1:
    print(N)
    N -= 1
print("\n")
```

### Multiplication table
```python
Num = int(input("Enter a number: "))
i = 1
while i <= 10:
    print(Num, "x", i, "=", Num * i)
    i += 1
print("\n")
```

### Sum of first N natural numbers
```python
N = int(input("Enter a number: "))
i = 1
Total = 0
while i <= N:
    Total += i
    i += 1
print("Sum of first", N, "natural numbers is:", Total, "\n")
```

### Factorial using a while loop
```python
Num = int(input("Enter a number: "))
if Num < 0:
    print("Factorial is not defined for negative numbers.\n")
else:
    i = 1
    Fact = 1
    while i <= Num:
        Fact *= i
        i += 1
    print("Factorial of", Num, "is:", Fact, "\n")
```

### Count digits
```python
Num = abs(int(input("Enter an integer: ")))
Count = 1 if Num == 0 else 0
while Num > 0:
    Num //= 10
    Count += 1
print("Number of digits:", Count, "\n")
```

### Reverse a number
```python
Num = int(input("Enter a number: "))
Sign = -1 if Num < 0 else 1
Num = abs(Num)
Rev = 0
while Num > 0:
    Digit = Num % 10
    Rev = Rev * 10 + Digit
    Num //= 10
Rev *= Sign
print("Reversed number is:", Rev, "\n")
```

### Palindrome check
```python
Num = int(input("Enter a number: "))
Original = Num
if Num < 0:
    print("Not a palindrome number\n")
else:
    Rev = 0
    while Num > 0:
        Digit = Num % 10
        Rev = Rev * 10 + Digit
        Num //= 10
    if Original == Rev:
        print("Palindrome number\n")
    else:
        print("Not a palindrome number\n")
```

### Sum of digits
```python
Num = abs(int(input("Enter a number: ")))
Sum_Digits = 0
while Num > 0:
    Sum_Digits += Num % 10
    Num //= 10
print("Sum of digits:", Sum_Digits, "\n")
```

### Prime number check
```python
def is_prime(n):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    i = 5
    while i * i <= n:
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6
    return True

Num = int(input("Enter a number: "))
if is_prime(Num):
    print(f"{Num} is a prime number.\n")
else:
    print(f"{Num} is not a prime number.\n")
```

### Prime numbers in a range
```python
def is_prime_range(n):
    if n <= 1:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

Start = int(input("Enter start of range: "))
End = int(input("Enter end of range: "))
print(f"Prime numbers between {Start} and {End}:")
for num in range(Start, End + 1):
    if is_prime_range(num):
        print(num, end=" ")
print("\n")
```

## Experiment 4 — Linear algebra operations (`sampleexp04.pdf`)

```python
import numpy as np

# Vector operations
v1 = np.array([1, 2, 3])
v2 = np.array([4, 5, 6])
print("Vector 1:", v1)
print("Vector 2:", v2)
print("\nVector Addition:", v1 + v2)
print("Vector Subtraction:", v1 - v2)

# Matrix operations
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])
print("\nMatrix A:\n", A)
print("\nMatrix B:\n", B)
print("\nMatrix Addition:\n", A + B)
print("\nMatrix Subtraction:\n", A - B)
print("\nTranspose of A:\n", A.T)

# Conjugate transpose
C = np.array([[1 + 2j, 3 - 1j], [2 + 4j, 5 + 0j]])
print("\nComplex Matrix C:\n", C)
print("\nConjugate Transpose of C:\n", C.conj().T)

# Determinant, inverse, and eigenvalues
det_A = np.linalg.det(A)
print("\nDeterminant of A:", det_A)
inverse_A = np.linalg.inv(A)
print("\nInverse of A:\n", inverse_A)
eigenvalues, eigenvectors = np.linalg.eig(A)
print("\nEigenvalues:", eigenvalues)
```

## Experiment 5 — Vector operations in quantum-state representation (`sampleexp05.pdf`)

```python
import numpy as np

v1 = np.array([1, 0], dtype=complex)
v2 = np.array([1, 1], dtype=complex)
print("Vector 1:", v1)
print("Vector 2:", v2)
print("\nMagnitude of Vector 1:", np.linalg.norm(v1))
print("Magnitude of Vector 2:", np.linalg.norm(v2))

v2_norm = v2 / np.linalg.norm(v2)
print("\nNormalized Vector 2:", v2_norm)
inner_product = np.vdot(v1, v2_norm)
print("\nInner Product:", inner_product)
outer_product = np.outer(v1, np.conjugate(v2_norm))
print("\nOuter Product:")
print(outer_product)

v3 = np.array([0, 1], dtype=complex)
inner_orthogonal = np.vdot(v1, v3)
print("\nVector 3:", v3)
print("Inner Product of Vector 1 and Vector 3:", inner_orthogonal)
if np.isclose(inner_orthogonal, 0):
    print("Vector 1 and Vector 3 are Orthogonal")
else:
    print("Vector 1 and Vector 3 are Not Orthogonal")

basis0 = np.array([1, 0], dtype=complex)
basis1 = np.array([0, 1], dtype=complex)
print("\nBasis Vectors:")
print("|0> =", basis0)
print("|1> =", basis1)
print("\nBasis Vector Inner Product:", np.vdot(basis0, basis1))
if np.isclose(np.vdot(basis0, basis1), 0):
    print("|0> and |1> are Orthogonal Basis Vectors")
```

## Experiment 6 — Quantum-state transformations (`sampleexp06.pdf`)

```python
import numpy as np

state = np.array([[1], [0]])
print("Initial Quantum State:")
print(state)

H = (1 / np.sqrt(2)) * np.array([[1, 1], [1, -1]])
print("Hadamard Matrix:")
print(H)
state_after_H = np.dot(H, state)
print("State after applying Hadamard Gate:")
print(state_after_H)

X = np.array([[0, 1], [1, 0]])
print("Pauli-X Matrix:")
print(X)

combined_matrix = np.dot(X, H)
print("Matrix Multiplication (X x H):")
print(combined_matrix)
final_state = np.dot(combined_matrix, state)
print("Final Quantum State:")
print(final_state)
```

## Experiment 7 — Identity matrices and unitary check (`sampleexp7.pdf`)

```python
import numpy as np

# 1-, 2-, and 3-qubit identity matrices
I1 = np.eye(2, dtype=int)
I2 = np.kron(I1, I1)
I3 = np.kron(I2, I1)
print("1-Qubit Identity Matrix:")
print(I1)
print("\n2-Qubit Identity Matrix:")
print(I2)
print("\n3-Qubit Identity Matrix:")
print(I3)

psi = np.array([1 / np.sqrt(2), 1 / np.sqrt(2)])
result = I1 @ psi
print("Original state:")
print(psi)
print("After applying identity:")
print(result)
print("State unchanged:", np.allclose(psi, result))

psi_2 = np.array([1, 2, 3, 4], dtype=float)
psi_2 = psi_2 / np.linalg.norm(psi_2)
result_2 = I2 @ psi_2
print("Original:", psi_2)
print("After identity:", result_2)
print("Unchanged:", np.allclose(psi_2, result_2))

psi_3 = np.ones(8, dtype=float)
psi_3 = psi_3 / np.linalg.norm(psi_3)
result_3 = I3 @ psi_3
print("Original state:")
print(psi_3)
print("\nAfter applying identity:")
print(result_3)
print("\nUnchanged:", np.allclose(psi_3, result_3))

X = np.array([[0, 1], [1, 0]])
check = X.conj().T @ X
print("X†X =")
print(check)
print("X is unitary:", np.allclose(check, I1))

XI = np.kron(X, I1)
print(XI)
```

## Experiment 9 — Functions (`sampleexp9.pdf`)

```python
# Function with arguments and no return value
def square_cube(num):
    Square = num ** 2
    Cube = num ** 3
    print("Square =", Square)
    print("Cube =", Cube, "\n")

N = int(input("Enter a number: "))
square_cube(N)

# Function with arguments and a return value
def check_even_odd(num):
    if num % 2 == 0:
        return "Even"
    return "Odd"

N = int(input("Enter a number: "))
Result = check_even_odd(N)
print(f"{N} is {Result}.\n")

# Function to calculate factorial
def factorial(num):
    Fact = 1
    for i in range(1, num + 1):
        Fact *= i
    return Fact

N = int(input("Enter a number: "))
if N < 0:
    print("Factorial is not defined for negative numbers.\n")
else:
    print("Factorial =", factorial(N), "\n")

# Function with default arguments
def simple_interest(principal, rate=5, time=1):
    SI = (principal * rate * time) / 100
    print("Simple Interest =", SI, "\n")

P = float(input("Enter Principal Amount: "))
simple_interest(P)

# Function using *args
def calculate_sum(*args):
    Total = sum(args)
    print("Sum =", Total)

calculate_sum(10, 20, 30)
calculate_sum(5, 15, 25, 35, 45)
print("\n")

# Function using **kwargs
def employee_details(**kwargs):
    print("Employee Details:")
    for key, value in kwargs.items():
        print(f"{key}: {value}")
    print("\n")

employee_details(
    Name="David",
    Age=19,
    Gender="Female",
    Department="Computer Science",
    Location="Seattle",
)

# Function returning multiple values
def calculate(values):
    Total = sum(values)
    Average = Total / len(values)
    Maximum = max(values)
    return Total, Average, Maximum

Numbers = [10, 20, 30, 40, 50]
S, Avg, Mx = calculate(Numbers)
print("Sum =", S)
print("Average =", Avg)
print("Maximum =", Mx, "\n")
```

## Experiment 10 — Recursive functions (`sampleexp10.pdf`)

```python
# Recursive Fibonacci function
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

Terms = int(input("Enter number of terms: "))
print("Fibonacci Series:")
for i in range(Terms):
    print(fibonacci(i), end=" ")
print("\n\n")

# Recursive factorial function
def factorial_rec(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial_rec(n - 1)

Num = int(input("Enter a number: "))
if Num < 0:
    print("Factorial is not defined for negative numbers.\n")
else:
    print("Factorial of", Num, "is", factorial_rec(Num), "\n")

# Recursive sum of digits
def sum_digits_rec(n):
    if n == 0:
        return 0
    return (n % 10) + sum_digits_rec(n // 10)

Num = abs(int(input("Enter a number: ")))
print("Sum of digits:", sum_digits_rec(Num), "\n")
```

## Experiment 11 — Operations on lists (`sampleexp-11.pdf`)

```python
# Append
A = [2, 3, 4, 5, 6, 9, 8]
A.append(10)
print("A =", A, "\n")

# Insert
A = [45, 67, 44, 14, 22, 13]
A.insert(3, 50)
print("A =", A, "\n")

# Delete by index (pop)
A = [22, 45, 14, 5, 67, 88]
A.pop(4)
print("A =", A, "\n")

# Remove by value
A = [45, 67, 33, 69, 39, 40]
A.remove(40)
print("A =", A, "\n")

# Slicing
A = [12, 46, 67, 33, 45, 22, 90, 55]
Slice_Start = A[0:7]
print("Slice:", Slice_Start, "\n")

# Extend
A = [22, 45, 5, 78, 14, 60]
B = [1, 2, 4, 10]
A.extend(B)
print("Extended A:", A, "\n")

# Indexing
A = [12, 23, 34, 56, 67, 78]
print("Element at index 4:", A[4], "\n")

# Concatenation
A = [44, 56, 67, 12, 34]
B = [50, 34, 22, 1]
print("Concatenation:", A + B, "\n")

# Repetition
A = [20, 30, 40]
print("Repetition:", A * 4, "\n")

# Updating
A = [34, 2, 12, 66, 7, 98]
print("Before update element at index 2:", A[2])
A[2] = 80
print("Updated A:", A, "\n")

# Membership
A = [23, 44, 36, 88, 79]
print("Is 5 in A?", 5 in A, "\n")

# Comparison
A = [33, 4, 5, 13, 88]
B = [45, 56, 7, 78]
print("Is A != B?", A != B, "\n")

# Sorting
A = [3, 5, 9, 4, 2, 7, 6]
A.sort()
print("Sorted A:", A, "\n")

# Reversing
B = [78, 68, 33, 90, 34, 14, 44]
B.reverse()
print("Reversed B:", B, "\n")

# Count, copy, length, sum, maximum, clear, and delete
A = [4, 6, 9, 7, 2, 8, 9]
print("Count of 9 in A:", A.count(9), "\n")
A = [2, 3, 4, 5, 5, 6, 7, 7, 8]
B = A.copy()
print("Copied B:", B, "\n")
A = [4, 5, 6, 778, 89, 23]
print("Length of A:", len(A), "\n")
A = [22, 45, 6, 3, 21, 2]
print("Sum of A:", sum(A), "\n")
A = [23, 88, 98, 786, 14, 2]
print("Maximum in A:", max(A), "\n")
A = [23, 4, 5, 67, 78, 90]
A.clear()
print("Cleared A:", A, "\n")
A = [3, 54, 56, 67, 78, 98]
del A[3]
print("After deleting element at index 3:", A, "\n")
```

## Experiments 11 & 12 — Advanced list and set operations (`sampleexp11&12.pdf`)

```python
# Reverse list iteration
print("--- Reverse List Iteration ---")
A = [1, 2, 3, 4, 5]
for i in range(len(A) - 1, -1, -1):
    print(A[i], end=" ")
print("\n\n")

# Maximum and minimum in a list
print("--- Max and Min in List ---")
A = [10, 25, 8, 50, 3]
Maximum = A[0]
Minimum = A[0]
for i in A:
    if i > Maximum:
        Maximum = i
    if i < Minimum:
        Minimum = i
print("Maximum =", Maximum)
print("Minimum =", Minimum, "\n")

# Extend list
print("--- Extend List ---")
List1 = [1, 2, 3]
List2 = [4, 5, 6]
List1.extend(List2)
print("Extended List:", List1, "\n")

# Common elements in two lists
print("--- Common Elements ---")
List1 = [1, 2, 3, 4]
List2 = [3, 4, 5, 6]
Common = []
for i in List1:
    if i in List2:
        Common.append(i)
print("Common Elements:", Common, "\n")

# Create set from list
print("--- Set Creation ---")
List1 = [1, 2, 2, 3, 4, 4, 5]
Set1 = set(List1)
print("Set from list:", Set1, "\n")

# Element search in set
print("--- Set Element Search ---")
Set1 = {"apple", "banana", "cherry"}
if "banana" in Set1:
    print("Element Found\n")
else:
    print("Element Not Found\n")

# Set difference
print("--- Set Difference ---")
Set1 = {1, 2, 3, 4}
Set2 = {3, 4, 5, 6}
print("Difference (Set1 - Set2):", Set1.difference(Set2), "\n")

# Set union
print("--- Set Union ---")
Set1 = {1, 2, 3}
Set2 = {3, 4, 5}
print("Union:", Set1.union(Set2), "\n")

# Set intersection
print("--- Set Intersection ---")
Set1 = {1, 2, 3}
Set2 = {2, 3, 4}
print("Intersection:", Set1.intersection(Set2), "\n")
```

## Experiment 13 — Tuple operations (`sampleexp13.pdf`)

```python
# Accessing
print("--- Tuple Accessing ---")
A = (10, 20, 30, 40)
print("Element at index 3:", A[3], "\n")

# Concatenation
print("--- Tuple Concatenation ---")
A = (20, 30, 40, 59, 90)
B = (34, 56, 60, 79, 90)
C = A + B
print("The new tuple is:", C, "\n")

# Slicing
print("--- Tuple Slicing ---")
A = (20, 30, 40, 59, 90)
print("Sliced Tuple:", A[:4], "\n")

# Sum and average
print("--- Sum and Average ---")
T = (10, 20, 30, 40, 50)
Total = sum(T)
Average = Total / len(T)
print("Sum =", Total)
print("Average =", Average, "\n")

# Length of tuple
print("--- Length Calculation ---")
T = (10, 20, 30, 40, 50)
Count = 0
for i in T:
    Count += 1
print("Length of tuple =", Count, "\n")

# Search element
print("--- Search Element ---")
T = (10, 20, 30, 40, 50)
Element = int(input("Enter element to search: "))
if Element in T:
    print("Element exists in the tuple.\n")
else:
    print("Element does not exist.\n")

# Extract even and odd numbers
print("--- Even and Odd Extraction ---")
T = (18, 15, 22, 37, 48, 51, 64)
print("Even numbers:")
for i in T:
    if i % 2 == 0:
        print(i, end=" ")
print("\nOdd numbers:")
for i in T:
    if i % 2 != 0:
        print(i, end=" ")
print("\n\n")

# Remove duplicates while preserving order
print("--- Remove Duplicates ---")
T = (10, 20, 10, 30, 40, 20, 50)
New_Tuple = tuple(dict.fromkeys(T))
print("Original tuple:", T)
print("Tuple after removing duplicates:", New_Tuple, "\n")

# Second-smallest and second-largest distinct values
print("--- Second Smallest and Largest ---")
T = (10, 50, 30, 20, 40)
Values = sorted(set(T))
if len(Values) < 2:
    raise ValueError("At least two distinct values are required")
print("Second smallest =", Values[1])
print("Second largest =", Values[-2], "\n")

# Reverse tuple
print("--- Reverse Tuple ---")
T = (10, 20, 30, 40, 50)
Rev = ()
for i in T:
    Rev = (i,) + Rev
print("Original tuple:", T)
print("Reversed tuple:", Rev, "\n")

# Delete tuple name
print("--- Tuple Deletion ---")
A = (1, 2, 3, 4, 5, 6, 7, 8, 9, 0)
print("Before Deletion:", A)
del A
print("Tuple variable deleted")
```

## Experiment 14 — Dictionary operations (`sampleexp14.pdf`)

The following snippets are separate exercises; each creates its own sample dictionary.

```python
# Create a dictionary and display all keys and values
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
print("Student Details:")
for Key, Value in Student.items():
    print(Key, ":", Value)
```

```python
# Access values using keys
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
print("Roll No:", Student["Roll No"])
print("Name:", Student["Name"])
print("Age:", Student["Age"])
print("Location:", Student["Location"], "\n")
```

```python
# Count key-value pairs
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
print("Total key-value pairs:", len(Student), "\n")
```

```python
# Check whether a key exists
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
Key_Search = input("Enter key to search: ")
if Key_Search in Student:
    print("Key exists in dictionary\n")
else:
    print("Key does not exist in dictionary\n")
```

```python
# Update an existing value
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
Student["Age"] = 20
print("Updated dictionary:", Student, "\n")
```

```python
# Add a key-value pair
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
Student["Gender"] = "Female"
print("Updated dictionary:", Student, "\n")
```

```python
# Delete a specific key
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
del Student["Location"]
print("Dictionary after deletion:", Student, "\n")
```

```python
# Remove the last inserted key-value pair
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
Removed = Student.popitem()
print("Removed item:", Removed)
print("Dictionary:", Student, "\n")
```

```python
# Clear all dictionary entries
Student = {"Roll No": 42, "Name": "David", "Age": 21, "Location": "Seattle"}
Student.clear()
print("Dictionary after clearing:", Student, "\n")
```

```python
# Display all key-value pairs with items()
Student = {"Roll No": 42, "Name": "David", "Course": "Computer Science", "CGPA": 8.5}
for Key, Value in Student.items():
    print(Key, ":", Value)
```

```python
# Display all keys
Student = {"Roll No": 42, "Name": "David", "Course": "Computer Science", "CGPA": 8.5}
print("Keys:", Student.keys(), "\n")
```

```python
# Display keys using a loop
Student = {"Roll No": 42, "Name": "David", "Course": "Computer Science", "CGPA": 8.5}
for Key in Student.keys():
    print(Key)
```

```python
# Display all values
Student = {"Roll No": 42, "Name": "David", "Course": "Computer Science", "CGPA": 8.5}
for Value in Student.values():
    print(Value)
```

```python
# Sum numeric values
Marks = {"Maths": 80, "Physics": 75, "Chemistry": 85, "Python": 90}
Total = sum(Marks.values())
print("Sum of values:", Total, "\n")
```

```python
# Find maximum and minimum values
Marks = {"Maths": 80, "Physics": 75, "Chemistry": 85, "Python": 90}
Maximum = max(Marks.values())
Minimum = min(Marks.values())
print("Maximum value:", Maximum)
print("Minimum value:", Minimum, "\n")
```

```python
# Reverse dictionary item order
Student = {"Roll No": 42, "Name": "David", "Course": "Computer Science", "CGPA": 8.5}
Reverse = dict(reversed(list(Student.items())))
print("Original dictionary:", Student)
print("Reversed dictionary:", Reverse, "\n")
```

## Experiment 15 — String operations (`sampleexp15.pdf`)

```python
# List slicing (as shown in source)
Numbers = [10, 20, 30, 40, 50, 60]
print("Sliced list:", Numbers[1:4], "\n")
```

```python
# String concatenation
First = "Hello"
Second = "Python"
Result = First + " " + Second
print("Concatenation:", Result, "\n")
```

```python
# String length
A = "college"  # Corrected spelling from source's "collage".
print("Length of string:", len(A))
print("String:", A, "\n")
```

```python
# Uppercase and lowercase conversions
First = "Hello"
Second = "Alex"
Result = First + " " + Second
print("Uppercase:", Result.upper())
print("Lowercase:", Result.lower(), "\n")
```

```python
# Replace substring
Text = "Hello World"
Text = Text.replace("World", "Python")
print("Replaced string:", Text, "\n")
```

```python
# Count vowels, consonants, digits, and other characters
Text = input("Enter a string: ")
Vowels = Consonants = Digits = Special = 0
for Ch in Text:
    if Ch.isalpha():
        if Ch.lower() in "aeiou":
            Vowels += 1
        else:
            Consonants += 1
    elif Ch.isdigit():
        Digits += 1
    else:
        Special += 1
print("Vowels:", Vowels)
print("Consonants:", Consonants)
print("Digits:", Digits)
print("Special Characters:", Special, "\n")
```

```python
# Frequency of a specific character
Text = input("Enter a string: ")
Ch = input("Enter character to find: ")
Count = 0
for C in Text:
    if C == Ch:
        Count += 1
print("Frequency of", Ch, "is:", Count, "\n")
```

```python
# Count words starting with a vowel
Sentence = input("Enter a sentence: ")
Words = Sentence.split()
Count = sum(1 for Word in Words if Word[0].lower() in "aeiou")
print("Words starting with a vowel:", Count, "\n")
```

```python
# Find longest and shortest word
Sentence = input("Enter a sentence: ")
Words = Sentence.split()
if not Words:
    print("No words were entered.")
else:
    Longest = max(Words, key=len)
    Shortest = min(Words, key=len)
    print("Longest word:", Longest)
    print("Shortest word:", Shortest, "\n")
```

```python
# Find most frequent character
Text = input("Enter a string: ")
if not Text:
    print("No characters were entered.")
else:
    Most_Frequent = max(set(Text), key=Text.count)
    print("Most frequent character:", Most_Frequent)
    print("Frequency:", Text.count(Most_Frequent), "\n")
```

```python
# Count words in a sentence
Sentence = input("Enter a sentence: ")
Words = Sentence.split()
print("Number of words:", len(Words), "\n")
```

```python
# Find duplicate words
Sentence = input("Enter a sentence: ")
Words = Sentence.lower().split()
Duplicates = []
for Word in Words:
    if Words.count(Word) > 1 and Word not in Duplicates:
        Duplicates.append(Word)
print("Duplicate words:", Duplicates, "\n")
```

```python
# Remove duplicate words while preserving order
Sentence = input("Enter a sentence: ")
Words = Sentence.split()
Result = list(dict.fromkeys(Words))
New_Sentence = " ".join(Result)
print("After removing duplicates:")
print(New_Sentence, "\n")
```

```python
# Reverse each word in a sentence
Sentence = input("Enter a sentence: ")
Words = Sentence.split()
Result = [Word[::-1] for Word in Words]
New_Sentence = " ".join(Result)
print("Reversed words:")
print(New_Sentence, "\n")
```

```python
# Basic email validation
Email = input("Enter email address: ")
if (
    "@" in Email
    and "." in Email
    and Email.count("@") == 1
    and not Email.startswith("@")
    and not Email.endswith("@")
    and not Email.startswith(".")
    and not Email.endswith(".")
):
    print("Valid email address\n")
else:
    print("Invalid email address\n")
```

## Experiment 16 — File operations (`sampleexp16.pdf`)

The PDF labels this experiment as “String Operations and Manipulations,” but its programs demonstrate file handling, so this heading reflects the code content.

```python
# Read a file if it exists
import os

filename = "student.txt"
if os.path.exists(filename):
    with open(filename, "r") as file:
        print(file.read())
else:
    print("File does not exist.")
```

```python
# Read the first three lines
filename = "student.txt"
with open(filename, "r") as file:
    for i in range(3):
        line = file.readline()
        if line == "":
            break
        print(line, end="")
```

```python
# Read the last three lines
filename = "student.txt"
with open(filename, "r") as file:
    lines = file.readlines()
for line in lines[-3:]:
    print(line, end="")
```

```python
# Read the last three lines (repeated example in source)
filename = "student.txt"
with open(filename, "r") as file:
    lines = file.readlines()
for line in lines[-3:]:
    print(line, end="")
```

```python
# Count lines, words, and characters
with open("student.txt") as f:
    data = f.read()
print("No. of Lines:", len(data.splitlines()))
print("No. of Words:", len(data.split()))
print("No. of Characters:", len(data))
```

```python
# Count digits and special characters
with open("student.txt") as f:
    data = f.read()
print("Digits:", sum(c.isdigit() for c in data))
print("Special characters:", sum(not c.isalnum() and not c.isspace() for c in data))
```

```python
# Replace a word in a file
with open("student.txt") as f:
    data = f.read()
data = data.replace(input("Old word: "), input("New word: "))
with open("student.txt", "w") as f:
    f.write(data)
```

```python
# Replace a sentence or phrase in a file
with open("student.txt") as f:
    data = f.read()
data = data.replace(input("Old sentence: "), input("New sentence: "))
with open("student.txt", "w") as f:
    f.write(data)
```

```python
# Find longest and shortest lines
with open("student.txt") as f:
    lines = f.readlines()
if lines:
    print("Longest:", max(lines, key=len))
    print("Shortest:", min(lines, key=len))
else:
    print("The file is empty.")
```

```python
# Most common word
from collections import Counter

with open("student.txt") as f:
    words = f.read().lower().split()
print(Counter(words).most_common(1))
```

```python
# Compare two files
file1 = "student.txt"
file2 = "data.txt"
with open(file1, "r") as f1:
    content1 = f1.read()
with open(file2, "r") as f2:
    content2 = f2.read()
if content1 == content2:
    print("Both files have the same content.")
else:
    print("The files have different content.")
```

```python
# Combine two files into combined.txt
files = ["student.txt", "data.txt"]
with open("combined.txt", "w") as output:
    for filename in files:
        with open(filename, "r") as file:
            output.write(file.read())
            output.write("\n")
print("Files combined successfully into combined.txt")
```

## Corrections and uncertainties

- The 15 named PDFs were visually reviewed page by page (46 pages total). Printed outputs were not copied as code. No code characters or lines were unreadable in the supplied PDFs.
- `sampleexp2.pdf`: corrected leap-year logic to account for century years, and made the largest-number example handle ties.
- `sampleex8.pdf`: the largest-number logic was adjusted for ties; factorial and digit-sum examples now handle negative input safely.
- `sampleexp-11.pdf`: removed an unrelated `square_cube(N)` call that depended on a variable and function from another notebook/session, where it would otherwise fail when run independently.
- `sampleexp13.pdf`: corrected the tuple access label/index wording and removed the final attempt to print a tuple variable after deleting it, which raised `NameError`. Duplicate removal now preserves order; second-extreme values validate there are at least two distinct items.
- `sampleexp15.pdf`: corrected `collage` to `college`; added empty-input handling to word/character operations.
- `sampleexp16.pdf`: fixed a missing closing parenthesis in the special-character counter; used context managers for file reading; added empty-file handling where needed.
- The source PDFs include overlapping material: one file is titled Experiments 11 & 12, and another separately contains Experiment 11 list operations. Both are retained as separate sections.
- `F:\pqc` also contained an unlisted Qiskit installation guide PDF; it was not included in this extraction because it was not among the files you listed.


