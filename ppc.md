# Object-Oriented Programming C++ Code Collection

Compiled from the 20 `.cpp` files and 9 PDFs supplied from `F:\oop`. The `.cpp` programs are reproduced first in the order supplied, followed by the additional PDF programs. Repeated PDF copies of programs already supplied as `.cpp` files are listed in the notes rather than duplicated. Printed output is excluded.

## Source-file programs

### ex01a.cpp

```cpp
// Experiment No.: 1(A)
// Title: Number System Conversion

#include <iostream>
using namespace std;

int main()
{
    int number;

    cout << "Enter number: ";
    cin >> number;

    cout << showbase;

    cout << "Hexadecimal : " << hex << number << endl;
    cout << "Octal       : " << oct << number << endl;
    cout << "Decimal     : " << dec << number << endl;

    return 0;
}
```

### ex01b.cpp

```cpp
// Experiment No.: 1(B)
// Title: Student Information using Structure

#include <iostream>
#include <string>
using namespace std;

struct Student
{
    string collegeName;
    string deptName;
    string studentName;
    float subjectMarks[3];
    float percentage;
    float CGPA;
};

int main()
{
    Student s;
    float totalMarks = 0;

    cout << "Enter College Name: ";
    getline(cin, s.collegeName);

    cout << "Enter Department Name: ";
    getline(cin, s.deptName);

    cout << "Enter Student Name: ";
    getline(cin, s.studentName);

    for (int i = 0; i < 3; i++)
    {
        cout << "Enter Subject " << i + 1 << " Marks: ";
        cin >> s.subjectMarks[i];
        totalMarks += s.subjectMarks[i];
    }

    s.percentage = (totalMarks * 100) / 300;
    s.CGPA = s.percentage / 10;

    cout << "\n----- Student Details -----\n";
    cout << "College Name : " << s.collegeName << endl;
    cout << "Department   : " << s.deptName << endl;
    cout << "Student Name : " << s.studentName << endl;
    cout << "Total Marks  : " << totalMarks << endl;
    cout << "Percentage   : " << s.percentage << "%" << endl;
    cout << "CGPA         : " << s.CGPA << endl;

    return 0;
}
```

### ex02a.cpp

```cpp
// Experiment No.: 2(A)
// Title: GCD and LCM

#include <iostream>
#include <numeric>
#include <cstdlib>
using namespace std;

int main()
{
    long long num1, num2;
    long long gcd, lcm;

    cout << "Enter two numbers: ";
    cin >> num1 >> num2;

    long long abs1 = std::llabs(num1);
    long long abs2 = std::llabs(num2);
    gcd = std::gcd(abs1, abs2);
    lcm = (gcd == 0) ? 0 : (abs1 / gcd) * abs2;

    cout << "GCD = " << gcd << endl;
    cout << "LCM = " << lcm << endl;

    return 0;
}
```

### ex02b.cpp

```cpp
// Experiment No.: 2(B)
// Title: Shopping List using Class

#include <iostream>
using namespace std;

class Shopping
{
private:
    int itemCode[100];
    float itemPrice[100];
    int count = 0;

public:
    void addItem()
    {
        int n;

        cout << "Enter Number of Items: ";
        cin >> n;

        for (int i = 0; i < n; i++)
        {
            cout << "\nItem " << i + 1 << endl;

            cout << "Enter Item Code: ";
            cin >> itemCode[count];

            cout << "Enter Item Price: ";
            cin >> itemPrice[count];

            count++;

            cout << "Item Added Successfully!\n";
        }

        cout << "\nAll Items Added Successfully.\n";
    }

    void deleteItem()
    {
        int code;

        cout << "Enter Item Code to Delete: ";
        cin >> code;

        for (int i = 0; i < count; i++)
        {
            if (itemCode[i] == code)
            {
                for (int j = i; j < count - 1; j++)
                {
                    itemCode[j] = itemCode[j + 1];
                    itemPrice[j] = itemPrice[j + 1];
                }

                count--;

                cout << "Item Deleted Successfully!\n";
                return;
            }
        }

        cout << "Item Not Found!\n";
    }

    void displayItem()
    {
        if (count == 0)
        {
            cout << "\nShopping List is Empty.\n";
            return;
        }

        cout << "\n========== Shopping List ==========\n";
        cout << "Item Code\tItem Price\n";
        cout << "-----------------------------------\n";

        for (int i = 0; i < count; i++)
        {
            cout << itemCode[i] << "\t\t" << itemPrice[i] << endl;
        }

        cout << "-----------------------------------\n";
    }

    void totalPrice()
    {
        float total = 0;

        for (int i = 0; i < count; i++)
        {
            total += itemPrice[i];
        }

        cout << "\n-----------------------------------\n";
        cout << "Total Shopping Price = " << total << endl;
        cout << "-----------------------------------\n";
    }
};

int main()
{
    Shopping s;
    int choice;

    do
    {
        cout << "\n========== SHOPPING MENU ==========\n";
        cout << "1. Add Item\n";
        cout << "2. Delete Item\n";
        cout << "3. Display Items\n";
        cout << "4. Total Price\n";
        cout << "5. Exit\n";
        cout << "===================================\n";

        cout << "Enter Your Choice: ";
        cin >> choice;

        switch (choice)
        {
            case 1:
                s.addItem();
                break;

            case 2:
                s.deleteItem();
                break;

            case 3:
                s.displayItem();
                break;

            case 4:
                s.totalPrice();
                break;

            case 5:
                cout << "\nThank You for Using Shopping List Program!\n";
                cout << "Visit Again!\n";
                break;

            default:
                cout << "\nInvalid Choice! Please Enter a Number Between 1 and 5.\n";
        }

    } while (choice != 5);

    return 0;
}
```

### ex03a.cpp

```cpp
// Experiment No.: 3(A)
// Title: Function Overloading for Area of Triangle, Rectangle and Sphere

#include <iostream>
using namespace std;

class Area
{
public:
    // area of triangle
    void area(float base, float height)
    {
        cout << "Area of Triangle: " << (0.5 * base * height) << endl;
    }

    // area of rectangle
    void area(double length, double breadth)
    {
        cout << "Area of Rectangle: " << (length * breadth) << endl;
    }

    // area of sphere
    void area(float radius)
    {
        cout << "Area of Sphere: " << (4 * 3.14 * radius * radius) << endl;
    }
};

int main()
{
    Area a;
    float base, height, radius;
    double length, breadth;

    cout << "Enter the base and height of triangle: " << endl;
    cin >> base >> height;
    a.area(base, height);

    cout << "Enter the length and breadth of rectangle: " << endl;
    cin >> length >> breadth;
    a.area(length, breadth);

    cout << "Enter the radius of sphere: " << endl;
    cin >> radius;
    a.area(radius);

    return 0;
}
```

### ex03b.cpp

```cpp
// Experiment No.: 3(B)
// Title: Friend Function to Find Maximum of Two Numbers

#include <iostream>
using namespace std;

class Maximum
{
private:
    int n1, n2;

public:
    void getData()
    {
        cout << "Enter First Number: ";
        cin >> n1;

        cout << "Enter Second Number: ";
        cin >> n2;
    }

    friend void findMax(Maximum m);
};

void findMax(Maximum m)
{
    if (m.n1 > m.n2)
    {
        cout << "\nMaximum Number = " << m.n1 << endl;
    }
    else
    {
        cout << "\nMaximum Number = " << m.n2 << endl;
    }
}

int main()
{
    Maximum m;

    m.getData();

    findMax(m);

    return 0;
}
```

### ex07.cpp

```cpp
// Experiment No.: 7
// Title: Dynamic Memory Allocation and Deallocation

#include <iostream>
using namespace std;

int main()
{
    int n;

    cout << "Enter the number of elements: ";
    cin >> n;

    if (n <= 0)
    {
        cout << "The number of elements must be positive." << endl;
        return 1;
    }

    // Dynamic memory allocation
    int *arr = new int[n];

    cout << "Enter " << n << " elements:" << endl;

    for (int i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    cout << "The elements are:" << endl;

    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }

    // Dynamic memory deallocation
    delete[] arr;

    cout << "\nMemory deallocated successfully." << endl;

    return 0;
}
```

### ex08a.cpp

```cpp
// Experiment No.: 8A
// Title: File Handling Using ifstream and ofstream

#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
    string name;
    int roll_no;
    float marks;

    // Write to a file
    ofstream ofile("student.txt");
    if (!ofile)
    {
        cerr << "Unable to open student.txt for writing." << endl;
        return 1;
    }

    cout << "Student details:" << endl;
    cout << "Student name:" << endl;
    getline(cin, name);

    cout << "Student roll no.:" << endl;
    cin >> roll_no;

    cout << "Student marks:" << endl;
    cin >> marks;

    ofile << name << endl;
    ofile << roll_no << endl;
    ofile << marks << endl;

    ofile.close();

    // Read from the file
    ifstream ifile("student.txt");
    if (!ifile)
    {
        cerr << "Unable to open student.txt for reading." << endl;
        return 1;
    }

    getline(ifile, name);
    ifile >> roll_no;
    ifile >> marks;

    ifile.close();

    cout << "\nStudent details from the file:" << endl;
    cout << "Name:" << name << endl;
    cout << "Roll No.:" << roll_no << endl;
    cout << "Marks:" << marks << endl;

    return 0;
}
```

### ex08a2.cpp

```cpp
// Experiment No.: 8A
// Title: File Handling Using Class and Object with ifstream and ofstream

#include <iostream>
#include <fstream>
#include <string>
#include <limits>
using namespace std;

class Student
{
private:
    string name;
    int rollNo;
    double grade;
    string address;

public:
    void getData()
    {
        cout << "Enter Student Name: ";
        getline(cin, name);

        cout << "Enter Roll Number: ";
        cin >> rollNo;

        cout << "Enter Grade: ";
        cin >> grade;

        cin.ignore(numeric_limits<streamsize>::max(), '\n');

        cout << "Enter Address: ";
        getline(cin, address);
    }

    void writeData()
    {
        ofstream file("student.txt");

        if (!file)
        {
            cout << "Error in opening file!" << endl;
            return;
        }

        file << "Student Name: " << name << endl;
        file << "Roll Number: " << rollNo << endl;
        file << "Grade: " << grade << endl;
        file << "Address: " << address << endl;

        file.close();

        cout << "\nStudent data written successfully." << endl;
    }

    void readData()
    {
        ifstream file("student.txt");

        if (!file)
        {
            cout << "Error in opening file!" << endl;
            return;
        }

        string line;

        cout << "\nStudent Information:" << endl;

        while (getline(file, line))
        {
            cout << line << endl;
        }

        file.close();
    }
};

int main()
{
    Student s;

    s.getData();
    s.writeData();
    s.readData();

    return 0;
}
```

### ex08b.cpp

```cpp
// Experiment No.: 8B
// Title: Read/Write Binary I/O Operations on a File

#include <iostream>
#include <fstream>
#include <iomanip>
using namespace std;

struct Student
{
    int rollNo;
    char name[30];
    int age;
    char department[30];
    float marks;
};

int main()
{
    Student s;

    cout << "Enter Roll No: ";
    cin >> s.rollNo;

    cout << "Enter Name: ";
    cin >> setw(sizeof(s.name)) >> s.name;

    cout << "Enter Age: ";
    cin >> s.age;

    cout << "Enter Department: ";
    cin >> setw(sizeof(s.department)) >> s.department;

    cout << "Enter Marks: ";
    cin >> s.marks;

    ofstream outfile("student.dat", ios::binary);

    outfile.write((char*)&s, sizeof(s));

    outfile.close();

    ifstream infile("student.dat", ios::binary);

    Student s1;

    infile.read((char*)&s1, sizeof(s1));

    cout << "\nData from binary file:\n";
    cout << "Roll No: " << s1.rollNo << endl;
    cout << "Name: " << s1.name << endl;
    cout << "Age: " << s1.age << endl;
    cout << "Department: " << s1.department << endl;
    cout << "Marks: " << s1.marks << endl;

    infile.close();

    return 0;
}
```

### ex09a.cpp

```cpp
// Experiment No.: 9A
// Title: Bubble Sort Using Template Function

#include <iostream>
using namespace std;

template <class T>
void bubbleSort(T arr[], int n)
{
    for (int i = 0; i < n - 1; i++)
    {
        for (int j = 0; j < n - i - 1; j++)
        {
            if (arr[j] > arr[j + 1])
            {
                T temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

template <class T>
void display(T arr[], int n)
{
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";

    cout << endl;
}

int main()
{
    int intArr[] = {9, 4, 7, 2, 6};
    float floatArr[] = {6.4, 2.7, 8.1, 3.9, 1.5};
    char charArr[] = {'H', 'D', 'A', 'F', 'B'};

    int n = 5;

    cout << "Integer Array: ";
    display(intArr, n);
    bubbleSort(intArr, n);
    cout << "Sorted Integer Array: ";
    display(intArr, n);

    cout << "\nFloat Array: ";
    display(floatArr, n);
    bubbleSort(floatArr, n);
    cout << "Sorted Float Array: ";
    display(floatArr, n);

    cout << "\nAlphabet Array: ";
    display(charArr, n);
    bubbleSort(charArr, n);
    cout << "Sorted Alphabet Array: ";
    display(charArr, n);

    return 0;
}
```

### ex09b.cpp

```cpp
// Experiment No.: 9B
// Title: Sorting Built-in and User-Defined Types Using Function Template

#include <iostream>
#include <string>
using namespace std;

// Function template for sorting an array
template <class T>
void sortArray(T arr[], int n)
{
    for (int i = 0; i < n - 1; i++)
    {
        for (int j = 0; j < n - i - 1; j++)
        {
            if (arr[j] > arr[j + 1])
            {
                T temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

// Function template to display an array
template <class T>
void display(T arr[], int n)
{
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";

    cout << endl;
}

// User-defined Date class
class Date
{
    int day, month, year;

public:
    Date(int d = 0, int m = 0, int y = 0)
    {
        day = d;
        month = m;
        year = y;
    }

    bool operator>(const Date& d) const
    {
        if (year != d.year)
            return year > d.year;

        if (month != d.month)
            return month > d.month;

        return day > d.day;
    }

    friend ostream& operator<<(ostream& out, const Date& d)
    {
        out << d.day << "/" << d.month << "/" << d.year;
        return out;
    }
};

int main()
{
    int a[] = {35, 12, 48, 7};
    float b[] = {7.6, 2.4, 9.1, 3.5};
    char c[] = {'m', 'c', 'x', 'a'};

    string s[] = {"Peach", "Grape", "Cherry", "Kiwi"};

    Date dates[] = {
        Date(20, 3, 2025),
        Date(12, 7, 2021),
        Date(8, 11, 2023)
    };

    cout << "Sorted integers: ";
    sortArray(a, 4);
    display(a, 4);

    cout << "Sorted floats: ";
    sortArray(b, 4);
    display(b, 4);

    cout << "Sorted characters: ";
    sortArray(c, 4);
    display(c, 4);

    cout << "Sorted strings: ";
    sortArray(s, 4);
    display(s, 4);

    cout << "Sorted dates: ";
    sortArray(dates, 3);
    display(dates, 3);

    return 0;
}
```

### ex10a.cpp

```cpp
// Experiment No.: 10A
// Title: Exception Handling Using try, throw and catch

#include <iostream>
using namespace std;

int main()
{
    int a, b;

    cout << "Enter numerator: ";
    cin >> a;

    cout << "Enter denominator: ";
    cin >> b;

    try
    {
        if (b == 0)
        {
            throw b;
        }

        int result = a / b;
        cout << "Result = " << result << endl;
    }
    catch (int x)
    {
        cout << "Exception caught: Division by zero is not allowed."
             << endl;
    }

    cout << "Program executed successfully." << endl;

    return 0;
}
```

### ex10b.cpp

```cpp
// Experiment No.: 10B
// Title: Exception Handling Using Multiple Catch Statements

#include <iostream>
using namespace std;

int main()
{
    int choice;

    cout << "1. Integer Exception" << endl;
    cout << "2. Character Exception" << endl;
    cout << "3. Double Exception" << endl;
    cout << "Enter your choice: ";
    cin >> choice;

    try
    {
        if (choice == 1)
        {
            throw 100;
        }
        else if (choice == 2)
        {
            throw 'A';
        }
        else if (choice == 3)
        {
            throw 12.5;
        }
        else
        {
            throw "Invalid choice";
        }
    }
    catch (int x)
    {
        cout << "Integer exception caught: "
             << x << endl;
    }
    catch (char ch)
    {
        cout << "Character exception caught: "
             << ch << endl;
    }
    catch (double d)
    {
        cout << "Double exception caught: "
             << d << endl;
    }
    catch (...)
    {
        cout << "Unknown exception caught." << endl;
    }

    cout << "Program executed successfully." << endl;

    return 0;
}
```

### exp04A1.cpp

```cpp
// Experiment No.: 4(A)
// Title: Parameterized Constructor for Student

#include <iostream>
#include <string>
using namespace std;

class student
{
public:
    string name;
    int rollno;
    float id;
    string address;

    student(string n, int r, float i, string a)
    {
        name = n;
        rollno = r;
        id = i;
        address = a;
    }

    void display()
    {
        cout << "Student Name : " << name << endl;
        cout << "Roll Number : " << rollno << endl;
        cout << "Student ID : " << id << endl;
        cout << "Address : " << address << endl;
    }
};

int main()
{
    student s1("David Miller", 21, 42, "Seattle");

    s1.display();

    return 0;
}
```

### exp04A2.cpp

```cpp
// Experiment No.: 4(A)
// Title: Parameterized Constructor for Employee

#include <iostream>
#include <string>
using namespace std;

class employee
{
public:
    string empname;
    int empid;
    float salary;
    string department;

    employee(string emp, int em, float s, string d)
    {
        empname = emp;
        empid = em;
        salary = s;
        department = d;
    }

    void display()
    {
        cout << "Employee Name : " << empname << endl;
        cout << "Employee ID : " << empid << endl;
        cout << "Salary : " << salary << endl;
        cout << "Department : " << department << endl;
    }
};

int main()
{
    employee e1("Tom Carter", 2042, 50000, "Computer Science");

    e1.display();

    return 0;
}
```

### exp04B1.cpp

```cpp
// Experiment No.: 4(B)
// Title: Copy Constructor for Employee

#include <iostream>
#include <string>
using namespace std;

class employee
{
public:
    string empname;
    int empid;
    float salary;
    string department;

    employee(string emp, int em, float s, string d)
    {
        empname = emp;
        empid = em;
        salary = s;
        department = d;
    }

    employee(const employee &e)
    {
        empname = e.empname;
        empid = e.empid;
        salary = e.salary;
        department = e.department;
    }

    void display()
    {
        cout << "Employee Name : " << empname << endl;
        cout << "Employee ID : " << empid << endl;
        cout << "Salary : " << salary << endl;
        cout << "Department : " << department << endl;
    }
};

int main()
{
    employee e1("Tom Carter", 2042, 50000, "Computer Science");

    cout << "Employee Data:" << endl;
    e1.display();

    cout << endl;

    employee e2 = e1;

    e2.display();

    return 0;
}
```

### exp04B2.cpp

```cpp
// Experiment No.: 4(B)
// Title: Copy Constructor for Student

#include <iostream>
#include <string>
using namespace std;

class student
{
public:
    string name;
    int rollno;
    float id;
    string address;

    student(string n, int r, float i, string a)
    {
        name = n;
        rollno = r;
        id = i;
        address = a;
    }

    student(const student &s)
    {
        name = s.name;
        rollno = s.rollno;
        id = s.id;
        address = s.address;
    }

    void display()
    {
        cout << "Student Name : " << name << endl;
        cout << "Roll Number : " << rollno << endl;
        cout << "Student ID : " << id << endl;
        cout << "Address : " << address << endl;
    }
};

int main()
{
    student s1("David Miller", 21, 42, "Seattle");

    cout << "The Student Data:" << endl;
    s1.display();

    cout << endl;

    student s2 = s1;

    s2.display();

    return 0;
}
```

### openended01.cpp

```cpp
// Experiment No.: Open-Ended Experiment 1
// Title: Lambda Expression Using Reference Capture

#include <iostream>
using namespace std;

int main()
{
    int a = 10;
    int b = 20;

    cout << "Before lambda expression:" << endl;
    cout << "a = " << a << ", b = " << b << endl;

    // Capture all used external variables by reference
    auto modify = [&]() {
        a = a + 5;
        b = b + 10;

        cout << "\nInside lambda expression:" << endl;
        cout << "a = " << a << ", b = " << b << endl;
    };

    modify();

    cout << "\nAfter lambda expression:" << endl;
    cout << "a = " << a << ", b = " << b << endl;

    return 0;
}
```

### openended02.cpp

```cpp
// Experiment No.: Open-Ended Experiment 2
// Title: Demonstration of Vector Operations in C++

#include <iostream>
#include <vector>
using namespace std;

int main()
{
    vector<int> numbers;

    // Insert elements into the vector
    numbers.push_back(10);
    numbers.push_back(20);
    numbers.push_back(30);
    numbers.push_back(40);
    numbers.push_back(50);

    cout << "Elements of the vector:" << endl;

    for (size_t i = 0; i < numbers.size(); i++)
    {
        cout << numbers.at(i) << " ";
    }

    cout << "\n\nSize of vector: " << numbers.size();

    // Add another element
    numbers.push_back(60);

    cout << "\n\nAfter inserting 60:" << endl;

    for (int value : numbers)
    {
        cout << value << " ";
    }

    // Remove the last element
    numbers.pop_back();

    cout << "\n\nAfter removing the last element:" << endl;

    for (int value : numbers)
    {
        cout << value << " ";
    }

    cout << "\n\nFinal size of vector: "
         << numbers.size() << endl;

    return 0;
}
```


## Additional programs found only in the PDFs

### Program 4(C) — Multiple inheritance (`OOP_4C.pdf`)

```cpp
#include <iostream>
using namespace std;

class Alpha
{
public:
    int a;
    Alpha(int x)
    {
        a = x;
        cout << "The Alpha constructor is created" << endl;
        cout << "Value of Alpha: " << a << endl;
    }
};

class Beta
{
public:
    int b;
    Beta(int y)
    {
        b = y;
        cout << "The Beta constructor is created" << endl;
        cout << "Value of Beta: " << b << endl;
    }
};

class Gamma : public Alpha, public Beta
{
public:
    int c;
    Gamma(int x, int y, int z) : Alpha(x), Beta(y)
    {
        c = z;
        cout << "The Gamma constructor is created" << endl;
        cout << "Value of Gamma: " << c << endl;
    }
};

int main()
{
    Gamma g(10, 20, 30);
    return 0;
}
```

### Program 5(A) — Multiple / hybrid inheritance (`OOP_5.pdf`)

```cpp
#include <iostream>
#include <string>
using namespace std;

class Person
{
protected:
    string mName;
    string mBirthDate;
    string mSex;
public:
    void getName() { cout << "Enter Name: "; cin >> mName; }
    void getBirthDate() { cout << "Enter Birth Date: "; cin >> mBirthDate; }
    void getSex() { cout << "Enter Sex: "; cin >> mSex; }
    void displayPerson()
    {
        cout << "\nName        : " << mName;
        cout << "\nBirth Date  : " << mBirthDate;
        cout << "\nSex         : " << mSex;
    }
};

class Student : virtual public Person
{
protected:
    string address;
    string department;
public:
    void getAddress() { cout << "Enter Address: "; cin >> address; }
    void getDepartment() { cout << "Enter Student Department: "; cin >> department; }
    void displayStudent()
    {
        cout << "\nAddress     : " << address;
        cout << "\nDepartment  : " << department;
    }
};

class Teacher : virtual public Person
{
protected:
    string rank;
    string teacherDepartment;
    string courseInfo;
public:
    void getRank() { cout << "Enter Rank: "; cin >> rank; }
    void getTeacherDepartment() { cout << "Enter Teacher Department: "; cin >> teacherDepartment; }
    void getCourseInfo() { cout << "Enter Course Information: "; cin >> courseInfo; }
    void displayTeacher()
    {
        cout << "\nRank        : " << rank;
        cout << "\nDepartment  : " << teacherDepartment;
        cout << "\nCourse      : " << courseInfo;
    }
};

class GradTeachingFellow : public Student, public Teacher
{
private:
    string supervisor;
public:
    void getSupervisor() { cout << "Enter Supervisor: "; cin >> supervisor; }
    void display()
    {
        displayPerson();
        displayStudent();
        displayTeacher();
        cout << "\nSupervisor  : " << supervisor;
    }
};

int main()
{
    GradTeachingFellow g;
    cout << "Enter Graduate Teaching Fellow Details\n";
    g.getName();
    g.getBirthDate();
    g.getSex();
    g.getAddress();
    g.getDepartment();
    g.getRank();
    g.getTeacherDepartment();
    g.getCourseInfo();
    g.getSupervisor();
    cout << "Graduate details";
    g.display();
    return 0;
}
```

### Program 5(B) — Runtime polymorphism with virtual functions (`OOP_5.pdf`)

```cpp
#include <iostream>
#include <string>
using namespace std;

class Account
{
protected:
    int accNo;
    string accHolderName;
    double balance;
public:
    Account(int no, string name, double bal)
        : accNo(no), accHolderName(name), balance(bal) {}
    virtual double calculateInterest() { return 0; }
    virtual void displayAccount()
    {
        cout << "Account No: " << accNo << endl;
        cout << "Account Holder Name: " << accHolderName << endl;
        cout << "Balance: " << balance << endl;
    }
    virtual ~Account() = default;
};

class SavingAccount : public Account
{
public:
    SavingAccount(int no, string name, double bal) : Account(no, name, bal) {}
    double calculateInterest() override { return balance * 0.06; }
};

class CurrentAccount : public Account
{
public:
    CurrentAccount(int no, string name, double bal) : Account(no, name, bal) {}
    double calculateInterest() override { return 0; }
};

class SalaryAccount : public Account
{
public:
    SalaryAccount(int no, string name, double bal) : Account(no, name, bal) {}
    double calculateInterest() override { return balance * 0.05; }
};

int main()
{
    SavingAccount s(101, "Alex", 50000);
    CurrentAccount c(102, "Alex", 90000);
    SalaryAccount sa(103, "Tom", 80000);
    Account* ptr;

    ptr = &s;
    ptr->displayAccount();
    cout << "Interest: " << ptr->calculateInterest() << endl << endl;
    ptr = &c;
    ptr->displayAccount();
    cout << "Interest: " << ptr->calculateInterest() << endl << endl;
    ptr = &sa;
    ptr->displayAccount();
    cout << "Interest: " << ptr->calculateInterest() << endl;
    return 0;
}
```

### Program 6(A) — Payments using runtime polymorphism (`OOP_6.pdf`)

```cpp
#include <iostream>
#include <string>
using namespace std;

class Payment
{
protected:
    int paymentId;
    string payerName;
    double amount;
public:
    Payment(int id, string name, double amt)
        : paymentId(id), payerName(name), amount(amt) {}
    virtual void makepayment() { cout << "Processing a generic payment" << endl; }
    void displayPayment()
    {
        cout << "Payment ID    : " << paymentId << endl;
        cout << "Payer Name    : " << payerName << endl;
        cout << "Amount        : Rs. " << amount << endl;
    }
    virtual ~Payment() = default;
};

class CreditCard : public Payment
{
public:
    CreditCard(int id, string name, double amt) : Payment(id, name, amt) {}
    void makepayment() override
    {
        cout << "Payment Mode  : Credit Card" << endl;
        cout << "Status        : Payment of Rs. " << amount << " processed successfully." << endl;
    }
};

class UPI : public Payment
{
public:
    UPI(int id, string name, double amt) : Payment(id, name, amt) {}
    void makepayment() override
    {
        cout << "Payment Mode  : UPI" << endl;
        cout << "Status        : Payment of Rs. " << amount << " processed successfully." << endl;
    }
};

class Cash : public Payment
{
public:
    Cash(int id, string name, double amt) : Payment(id, name, amt) {}
    void makepayment() override
    {
        cout << "Payment Mode  : Cash" << endl;
        cout << "Status        : Payment of Rs. " << amount << " processed successfully." << endl;
    }
};

int main()
{
    CreditCard cc(101, "Alex", 1000.0);
    UPI upi(102, "Alex", 500.5);
    Cash cash(103, "Tom", 200.0);
    Payment* ptr;

    cout << "\nCredit Card Payment" << endl;
    ptr = &cc;
    ptr->displayPayment();
    ptr->makepayment();

    cout << "\nUPI Payment" << endl;
    ptr = &upi;
    ptr->displayPayment();
    ptr->makepayment();

    cout << "\nCash Payment" << endl;
    ptr = &cash;
    ptr->displayPayment();
    ptr->makepayment();
    return 0;
}
```

### Program 6(B) — Media management using runtime polymorphism (`OOP_6.pdf`)

```cpp
#include <iostream>
#include <string>
using namespace std;

class Media
{
public:
    int id;
    string title;
    bool issued = false;
    Media(int i, string t) : id(i), title(t) {}
    virtual void display()
    {
        cout << "ID: " << id
             << "\nTitle: " << title
             << "\nIssued: " << (issued ? "Yes" : "No") << endl;
    }
    void issue() { issued = true; cout << "Issued successfully.\n"; }
    void deposit() { issued = false; cout << "Deposited successfully.\n"; }
    virtual ~Media() = default;
};

class Book : public Media
{
    string author;
public:
    Book(int i, string t, string a) : Media(i, t), author(a) {}
    void display() override
    {
        cout << "\n--- Book ---" << endl;
        Media::display();
        cout << "Author: " << author << endl;
    }
};

class Tape : public Media
{
    double duration;
public:
    Tape(int i, string t, double d) : Media(i, t), duration(d) {}
    void display() override
    {
        cout << "Tape" << endl;
        Media::display();
        cout << "Duration: " << duration << " mins" << endl;
    }
};

int main()
{
    Book b(101, "C++ Programming", "Alex");
    Tape t(102, "C++ Tutorial", 120);
    Media* ptr = &b;
    ptr->display();
    ptr->issue();
    ptr = &t;
    ptr->display();
    ptr->deposit();
    return 0;
}
```

## Review and correction notes

- Total: **25 unique programs**: 20 source-file programs plus 5 additional programs from the PDFs. The PDFs repeat several supplied `.cpp` programs; those duplicates were not copied twice.
- `OOP_9.pdf` and `OOP_9 (1).pdf` are duplicate copies of the same PDF. Both contain Programs 9(A) and 9(B), which are also present as `.cpp` files.
- `OOP_7.pdf`, `OOP_8.pdf`, `OOP_8B.pdf`, and `OOP_10.pdf` repeat programs supplied as source files. OOP 8 PDF contains a second class-based file example matching `ex08a2.cpp`.
- Small corrections were made in the compiled listings: support for names with spaces in `ex01b.cpp` and `ex08a.cpp`; robust GCD/LCM handling in `ex02a.cpp` (C++17 `std::gcd`); positive-size validation in `ex07.cpp`; full-line cleanup in `ex08a2.cpp` and bounded character-array input in `ex08b.cpp`; and the missing `<string>` include in the PDF's Account program. Virtual base classes also receive virtual destructors in the corrected polymorphism listings.
- Some input prompts and field names were lightly normalized while preserving each program's purpose and structure.
- No code was unreadable. The PDFs contain 42 pages total; output pages/screenshots were excluded. The two OOP 9 PDFs are duplicates.
- Code was not compiled or run.
