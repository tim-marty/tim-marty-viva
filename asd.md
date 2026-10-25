# Data Structures and Algorithms Laboratory Programs

Arranged to match the assignment order in the syllabus image. **12 syllabus items; 15 separate C programs.** Output screenshots are excluded. Code formatting is normalized. Important corrections are summarized at the end.

## 1. Implement Linear Search and Binary Search for a given array.

### Linear Search

*Source: DSA28F.pdf, p. 1*

```c
// Q1. Implement Linear Search for a given array.
#include <stdio.h>
#include <stdlib.h>
int main()
{
    int noe;
    printf("Enter no of elements you want in array: ");
    scanf("%d", &noe);
    if (noe <= 0)
        return 1;
    int arr[noe];
    printf("Enter elements: ");
    for (int n = 0; n < noe; n++)
    {
        scanf("%d", &arr[n]);
    }
    int key;
    printf("Enter Key to search: ");
    scanf("%d", &key);
    int found = 0;
    int foundat = -1;
    for (int i = 0; i < noe; i++)
    {
        if (arr[i] == key)
        {
            found = 1;
            foundat = i + 1;
            break;
        }
    }
    if (found == 0)
    {
        printf("Element not found");
    }
    else
    {
        printf("Element found at %d position", foundat);
    }
    return 0;
}
```

### Binary Search

*Source: DSA28F.pdf, p. 2*

```c
// Q1. Implement Binary Search for a given array.
#include <stdio.h>
#include <stdlib.h>
int main()
{
    int noe;
    printf("Enter no of elements you want in array: ");
    scanf("%d", &noe);
    if (noe <= 0)
        return 1;
    int arr[noe];
    printf("Enter elements in sorted form: ");
    for (int n = 0; n < noe; n++)
    {
        scanf("%d", &arr[n]);
    }
    int key;
    printf("Enter Key to search: ");
    scanf("%d", &key);
    int start = 0;
    int end = noe - 1;
    int found = 0;
    while (start <= end)
    {
        int mid = (start + end) / 2;
        if (arr[mid] == key)
        {
            found = 1;
            printf("Element found at %d position", mid + 1);
            break;
        }
        else if (arr[mid] > key)
        {
            end = mid - 1;
        }
        else
        {
            start = mid + 1;
        }
    }
    if (found == 0)
    {
        printf("Element Not found");
    }
    return 0;
}
```

## 2. Arrange student roll numbers in ascending order.

### a) Bubble Sort

*Source: DSA28F.pdf, p. 3*

```c
// Q2(a). Arrange the list of students according to roll numbers in ascending order using Bubble Sort.
#include <stdio.h>
#include <stdlib.h>
void swap(int *x, int *y)
{
    int temp = *x;
    *x = *y;
    *y = temp;
}
void bSort(int rollNo[], int noe)
{
    int i, j;
    for (i = noe - 1; i > 0; i--)
    {
        for (j = 0; j < i; j++)
        {
            if (rollNo[j] > rollNo[j + 1])
                swap(&rollNo[j], &rollNo[j + 1]);
        }
    }
}
int main()
{
    int noe;
    printf("Enter No of roll no you want in unsorted manner\n");
    scanf("%d", &noe);
    if (noe <= 0)
        return 1;
    int rollNo[noe];
    printf("Enter roll no you want in list\n");
    for (int i = 0; i < noe; i++)
        scanf("%d", &rollNo[i]);
    printf("\nYour roll numbers\n");
    for (int k = 0; k < noe; k++)
        printf("%d ", rollNo[k]);
    bSort(rollNo, noe);
    printf("\nSorted roll numbers\n");
    for (int k = 0; k < noe; k++)
        printf("%d ", rollNo[k]);
    return 0;
}
```

### b) Insertion Sort

*Source: DSA28F.pdf, p. 4*

```c
// Q2(b). Arrange the list of students according to roll numbers in ascending order using Insertion Sort.
#include <stdio.h>
#include <stdlib.h>
void inSort(int rollNo[], int noe)
{
    int item;
    for (int i = 1; i < noe; i++)
    {
        item = rollNo[i];
        int j = i - 1;
        while (j >= 0 && rollNo[j] > item)
        {
            rollNo[j + 1] = rollNo[j];
            j--;
        }
        rollNo[j + 1] = item;
    }
}
int main()
{
    int noe;
    printf("Enter No of roll no you want in unsorted manner\n");
    scanf("%d", &noe);
    if (noe <= 0)
        return 1;
    int rollNo[noe];
    printf("Enter roll no you want in list\n");
    for (int i = 0; i < noe; i++)
        scanf("%d", &rollNo[i]);
    printf("\nYour roll numbers\n");
    for (int k = 0; k < noe; k++)
        printf("%d ", rollNo[k]);
    inSort(rollNo, noe);
    printf("\nSorted roll numbers\n");
    for (int k = 0; k < noe; k++)
        printf("%d ", rollNo[k]);
    return 0;
}
```

### c) Quick Sort

*Source: DSA28F.pdf, p. 5*

```c
// Q2(c). Arrange the list of students according to roll numbers in ascending order using Quick Sort.
#include <stdio.h>
#include <stdlib.h>
void swap(int *a, int *b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}
int partition(int arr[], int low, int high)
{
    int pivot = arr[high];
    int i = low;
    for (int j = low; j < high; j++)
    {
        if (arr[j] < pivot)
        {
            swap(&arr[i], &arr[j]);
            i++;
        }
    }
    swap(&arr[i], &arr[high]);
    return i;
}
void quicksort(int arr[], int low, int high)
{
    if (low < high)
    {
        int p = partition(arr, low, high);
        quicksort(arr, low, p - 1);
        quicksort(arr, p + 1, high);
    }
}
int main()
{
    int noe;
    printf("Enter no of elements you want in array\n");
    scanf("%d", &noe);
    if (noe <= 0)
        return 1;
    int arr[noe];
    printf("Enter values: ");
    for (int n = 0; n < noe; n++)
        scanf("%d", &arr[n]);
    printf("Unsorted array\n");
    for (int i = 0; i < noe; i++)
        printf("%d ", arr[i]);
    printf("\n");
    quicksort(arr, 0, noe - 1);
    printf("Sorted Array\n");
    for (int i = 0; i < noe; i++)
        printf("%d ", arr[i]);
    return 0;
}
```

## 3. Implement sparse matrix operations.

### Initialize, insert, sort by row and column, transpose, and display

*Source: DSA28F.pdf, pp. 7-8*

```c
// Q3. Implement sparse matrix operations: initialize, insert, sort by row and column, transpose, and display.
#include <stdio.h>
#define MAX_TERMS 1000

typedef struct
{
    int row;
    int col;
    int value;
} Term;
typedef struct
{
    int rows;
    int cols;
    int count;
    Term terms[MAX_TERMS];
} SparseMatrix;

void initialize(SparseMatrix *matrix, int rows, int cols)
{
    matrix->rows = rows;
    matrix->cols = cols;
    matrix->count = 0;
}

int insertElement(SparseMatrix *matrix, int row, int col, int value)
{
    if (row < 0 || row >= matrix->rows || col < 0 || col >= matrix->cols)
        return 0;
    for (int i = 0; i < matrix->count; i++)
    {
        if (matrix->terms[i].row == row && matrix->terms[i].col == col)
        {
            matrix->terms[i].value = value;
            if (value == 0)
            {
                for (int j = i; j < matrix->count - 1; j++)
                    matrix->terms[j] = matrix->terms[j + 1];
                matrix->count--;
            }
            return 1;
        }
    }
    if (value == 0)
        return 1;
    if (matrix->count == MAX_TERMS)
        return 0;
    matrix->terms[matrix->count++] = (Term){row, col, value};
    return 1;
}

void sortByRowColumn(SparseMatrix *matrix)
{
    for (int i = 1; i < matrix->count; i++)
    {
        Term item = matrix->terms[i];
        int j = i - 1;
        while (j >= 0 &&
               (matrix->terms[j].row > item.row ||
                (matrix->terms[j].row == item.row && matrix->terms[j].col > item.col)))
        {
            matrix->terms[j + 1] = matrix->terms[j];
            j--;
        }
        matrix->terms[j + 1] = item;
    }
}

SparseMatrix transpose(const SparseMatrix *matrix)
{
    SparseMatrix result;
    initialize(&result, matrix->cols, matrix->rows);
    for (int i = 0; i < matrix->count; i++)
        insertElement(&result, matrix->terms[i].col, matrix->terms[i].row, matrix->terms[i].value);
    sortByRowColumn(&result);
    return result;
}

void display(const SparseMatrix *matrix)
{
    printf("Rows: %d, Columns: %d, Non-zero terms: %d\n", matrix->rows, matrix->cols, matrix->count);
    printf("Row\tColumn\tValue\n");
    for (int i = 0; i < matrix->count; i++)
        printf("%d\t%d\t%d\n", matrix->terms[i].row, matrix->terms[i].col, matrix->terms[i].value);
}

int main(void)
{
    SparseMatrix matrix;
    int rows, cols, choice, row, col, value;
    printf("Enter number of rows and columns: ");
    if (scanf("%d %d", &rows, &cols) != 2 || rows <= 0 || cols <= 0)
    {
        printf("Invalid matrix dimensions.\n");
        return 1;
    }
    initialize(&matrix, rows, cols);
    do
    {
        printf("\n1. Insert or update element\n");
        printf("2. Sort by row and column\n");
        printf("3. Transpose matrix\n");
        printf("4. Display matrix terms\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        if (scanf("%d", &choice) != 1)
            return 1;
        switch (choice)
        {
            case 1:
                printf("Enter row, column and value: ");
                if (scanf("%d %d %d", &row, &col, &value) != 3 ||
                    !insertElement(&matrix, row, col, value))
                    printf("Invalid position or sparse matrix capacity exceeded.\n");
                break;
            case 2:
                sortByRowColumn(&matrix);
                printf("Sparse matrix sorted.\n");
                break;
            case 3:
                matrix = transpose(&matrix);
                printf("Matrix transposed.\n");
                break;
            case 4:
                display(&matrix);
                break;
            case 5:
                break;
            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 5);
    return 0;
}
```

## 4. Linked list functions.

### Add and delete nodes, count nodes, and display in reverse using recursion

*Source: DSA28F.pdf, pp. 9-11*

```c
// Q4. Write functions to add and delete nodes in a singly linked list, compute total number of nodes, and display the [remaining comment clipped].
#include <stdio.h>
#include <stdlib.h>
struct Node
{
    int data;
    struct Node *next;
};
void insertFirst(struct Node **head)
{
    int data;
    printf("Enter data: ");
    scanf("%d", &data);
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    if (newNode == NULL)
    {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = *head;
    *head = newNode;
}
void insertEnd(struct Node **head)
{
    int data;
    printf("Enter data: ");
    scanf("%d", &data);
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    if (newNode == NULL)
    {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = NULL;
    if (*head == NULL)
    {
        *head = newNode;
        return;
    }
    struct Node *temp = *head;
    while (temp->next != NULL)
        temp = temp->next;
    temp->next = newNode;
}
void insertMiddle(struct Node **head)
{
    int data, position;
    printf("Enter data: ");
    scanf("%d", &data);
    printf("Enter position: ");
    scanf("%d", &position);
    if (position < 1)
    {
        printf("Invalid position.\\n");
        return;
    }
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    if (newNode == NULL)
    {
        printf("Memory allocation failed.\\n");
        return;
    }
    newNode->data = data;
    if (position == 1)
    {
        newNode->next = *head;
        *head = newNode;
        return;
    }
    struct Node *temp = *head;
    for (int i = 1; i < position - 1 && temp != NULL; i++)
        temp = temp->next;
    if (temp == NULL)
    {
        printf("Invalid position.\\n");
        free(newNode);
        return;
    }
    newNode->next = temp->next;
    temp->next = newNode;
}
void deleteFirst(struct Node **head)
{
    if (*head == NULL)
    {
        printf("List is empty.\n");
        return;
    }
    struct Node *temp = *head;
    printf("Deleted data: %d\n", temp->data);
    *head = temp->next;
    free(temp);
}
void deleteEnd(struct Node **head)
{
    if (*head == NULL)
    {
        printf("List is empty.\n");
        return;
    }
    if ((*head)->next == NULL)
    {
        printf("Deleted data: %d\n", (*head)->data);
        free(*head);
        *head = NULL;
        return;
    }
    struct Node *temp = *head;
    while (temp->next->next != NULL)
        temp = temp->next;
    printf("Deleted data: %d\n", temp->next->data);
    free(temp->next);
    temp->next = NULL;
}
void deleteMiddle(struct Node **head)
{
    int position;
    if (*head == NULL)
    {
        printf("List is empty.\n");
        return;
    }
    printf("Enter position to delete: ");
    scanf("%d", &position);
    if (position <= 1)
    {
        deleteFirst(head);
        return;
    }
    struct Node *temp = *head;
    for (int i = 1; i < position - 1 && temp->next != NULL; i++)
        temp = temp->next;
    if (temp->next == NULL)
    {
        printf("Invalid position.\n");
        return;
    }
    struct Node *deleteNode = temp->next;
    printf("Deleted data: %d\n", deleteNode->data);
    temp->next = deleteNode->next;
    free(deleteNode);
}
int countNodes(struct Node *head)
{
    int count = 0;
    while (head != NULL)
    {
        count++;
        head = head->next;
    }
    return count;
}
void display(struct Node *head)
{
    if (head == NULL)
    {
        printf("List is empty.\n");
        return;
    }
    while (head != NULL)
    {
        printf("%d -> ", head->data);
        head = head->next;
    }
    printf("NULL\n");
}
void displayReverse(struct Node *head)
{
    if (head == NULL)
        return;
    displayReverse(head->next);
    printf("%d -> ", head->data);
}
int main()
{
    struct Node *head = NULL;
    int choice;
    while (1)
    {
        printf("\n1. Insert at First\n");
        printf("2. Insert at Middle\n");
        printf("3. Insert at End\n");
        printf("4. Delete from First\n");
        printf("5. Delete from Middle\n");
        printf("6. Delete from End\n");
        printf("7. Count Nodes\n");
        printf("8. Display List\n");
        printf("9. Display Reverse\n");
        printf("10. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1: insertFirst(&head); break;
            case 2: insertMiddle(&head); break;
            case 3: insertEnd(&head); break;
            case 4: deleteFirst(&head); break;
            case 5: deleteMiddle(&head); break;
            case 6: deleteEnd(&head); break;
            case 7: printf("Total nodes: %d\n", countNodes(head)); break;
            case 8: printf("Linked List: "); display(head); break;
            case 9: printf("Reverse List: "); displayReverse(head); printf("NULL\n"); break;
            case 10: printf("Exiting...\n"); return 0;
            default: printf("Invalid choice!\n");
        }
    }
    return 0;
}
```

## 5. Polynomial data type and operations.

### Create, insert terms, add polynomials, and evaluate

*Source: DSA28F.pdf, pp. 14-16*

```c
// Q5. Implement a data type to represent a Polynomial with operations like create an empty polynomial, insert an entry, add two polynomials, [remainder clipped].
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
struct Node
{
    int coeff;
    int exp;
    struct Node *next;
};
typedef struct Node Node;
Node *createPolynomial()
{
    return NULL;
}
Node *insertTerm(Node *poly, int coeff, int exp)
{
    Node *newNode, *temp, *prev;
    if (coeff == 0)
        return poly;
    if (poly == NULL)
    {
        newNode = (Node *)malloc(sizeof(Node));
        newNode->coeff = coeff;
        newNode->exp = exp;
        newNode->next = NULL;
        return newNode;
    }
    temp = poly;
    prev = NULL;
    while (temp != NULL)
    {
        if (temp->exp == exp)
        {
            temp->coeff += coeff;
            if (temp->coeff == 0)
            {
                if (prev == NULL)
                    poly = temp->next;
                else
                    prev->next = temp->next;
                free(temp);
            }
            return poly;
        }
        prev = temp;
        temp = temp->next;
    }
    newNode = (Node *)malloc(sizeof(Node));
    newNode->coeff = coeff;
    newNode->exp = exp;
    if (exp > poly->exp)
    {
        newNode->next = poly;
        return newNode;
    }
    temp = poly;
    while (temp->next != NULL && temp->next->exp > exp)
        temp = temp->next;
    newNode->next = temp->next;
    temp->next = newNode;
    return poly;
}
void displayPolynomial(Node *poly)
{
    Node *temp = poly;
    if (temp == NULL)
    {
        printf("0\n");
        return;
    }
    while (temp != NULL)
    {
        if (temp != poly && temp->coeff > 0)
            printf(" + ");
        if (temp->coeff < 0)
            printf(" -");
        printf("%d", abs(temp->coeff));
        if (temp->exp > 0)
        {
            printf("x");
            if (temp->exp > 1)
                printf("^%d", temp->exp);
        }
        temp = temp->next;
    }
    printf("\n");
}
Node *addPolynomials(Node *p1, Node *p2)
{
    Node *result = createPolynomial();
    Node *temp = p1;
    while (temp != NULL)
    {
        result = insertTerm(result, temp->coeff, temp->exp);
        temp = temp->next;
    }
    temp = p2;
    while (temp != NULL)
    {
        result = insertTerm(result, temp->coeff, temp->exp);
        temp = temp->next;
    }
    return result;
}
double evaluatePolynomial(Node *poly, double x)
{
    Node *temp = poly;
    double result = 0;
    while (temp != NULL)
    {
        result += temp->coeff * pow(x, temp->exp);
        temp = temp->next;
    }
    return result;
}
void freePolynomial(Node *poly)
{
    Node *temp;
    while (poly != NULL)
    {
        temp = poly;
        poly = poly->next;
        free(temp);
    }
}
Node *readPolynomial()
{
    Node *poly = createPolynomial();
    int n, coeff, exp;
    printf("Enter number of terms: ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        printf("Enter coefficient and exponent: ");
        scanf("%d %d", &coeff, &exp);
        poly = insertTerm(poly, coeff, exp);
    }
    return poly;
}
int main()
{
    Node *p1 = createPolynomial();
    Node *p2 = createPolynomial();
    Node *result = NULL;
    int choice, coeff, exp;
    double x;
    do
    {
        printf("\n========== POLYNOMIAL MENU ==========\n");
        printf("1. Create Polynomial 1\n");
        printf("2. Create Polynomial 2\n");
        printf("3. Insert term into Polynomial 1\n");
        printf("4. Insert term into Polynomial 2\n");
        printf("5. Display Polynomial 1\n");
        printf("6. Display Polynomial 2\n");
        printf("7. Add Polynomial 1 and Polynomial 2\n");
        printf("8. Evaluate Polynomial 1\n");
        printf("9. Evaluate Polynomial 2\n");
        printf("10. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
                freePolynomial(p1);
                p1 = readPolynomial();
                printf("Polynomial 1 created successfully.\n");
                break;
            case 2:
                freePolynomial(p2);
                p2 = readPolynomial();
                printf("Polynomial 2 created successfully.\n");
                break;
            case 3:
                printf("Enter coefficient: ");
                scanf("%d", &coeff);
                printf("Enter exponent: ");
                scanf("%d", &exp);
                p1 = insertTerm(p1, coeff, exp);
                printf("Term inserted into Polynomial 1.\n");
                break;
            case 4:
                printf("Enter coefficient: ");
                scanf("%d", &coeff);
                printf("Enter exponent: ");
                scanf("%d", &exp);
                p2 = insertTerm(p2, coeff, exp);
                printf("Term inserted into Polynomial 2.\n");
                break;
            case 5:
                printf("Polynomial 1: ");
                displayPolynomial(p1);
                break;
            case 6:
                printf("Polynomial 2: ");
                displayPolynomial(p2);
                break;
            case 7:
                freePolynomial(result);
                result = addPolynomials(p1, p2);
                printf("Result: ");
                displayPolynomial(result);
                break;
            case 8:
                printf("Enter value of x: ");
                scanf("%lf", &x);
                printf("Polynomial 1: ");
                displayPolynomial(p1);
                printf("Value at x = %.2lf is %.2lf\n", x, evaluatePolynomial(p1, x));
                break;
            case 9:
                printf("Enter value of x: ");
                scanf("%lf", &x);
                printf("Polynomial 2: ");
                displayPolynomial(p2);
                printf("Value at x = %.2lf is %.2lf\n", x, evaluatePolynomial(p2, x));
                break;
            case 10:
                printf("Exiting program...\n");
                break;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 10);
    freePolynomial(p1);
    freePolynomial(p2);
    freePolynomial(result);
    return 0;
}
```

## 6. Stack using a linked list and postfix evaluation.

### Stack operations and postfix expression evaluation

*Source: DSA28F.pdf, pp. 19-20*

```c
// Q6. Implement Stack using a linked list. Use this stack to perform evaluation of a postfix expression.
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
typedef struct Node
{
    int data;
    struct Node *next;
} Node;
void push(Node **top, int value)
{
    Node *newNode = (Node *)malloc(sizeof(Node));
    if (newNode == NULL)
    {
        printf("Stack Overflow!\n");
        return;
    }
    newNode->data = value;
    newNode->next = *top;
    *top = newNode;
}
int pop(Node **top)
{
    if (*top == NULL)
    {
        printf("Stack Underflow!\n");
        return -1;
    }
    Node *temp = *top;
    int value = temp->data;
    *top = temp->next;
    free(temp);
    return value;
}
void display(Node *top)
{
    if (top == NULL)
    {
        printf("Stack is empty.\n");
        return;
    }
    printf("stack: ");
    while (top != NULL)
    {
        printf("%d ", top->data);
        top = top->next;
    }
    printf("\n");
}
int operation(int a, int b, char op)
{
    switch (op)
    {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/':
            if (b == 0)
            {
                printf("Error: Division by zero!\n");
                exit(1);
            }
            return a / b;
        default:
            printf("Invalid operator!\n");
            exit(1);
    }
}
int evaluatePostfix(char postfix[])
{
    Node *top = NULL;
    for (int i = 0; postfix[i] != '\0'; i++)
    {
        if (isspace(postfix[i]))
            continue;
        if (isdigit(postfix[i]))
        {
            int num = 0;
            while (isdigit(postfix[i]))
            {
                num = num * 10 + (postfix[i] - '0');
                i++;
            }
            i--;
            push(&top, num);
        }
        else
        {
            if (top == NULL || top->next == NULL)
            {
                printf("Invalid postfix expression!\n");
                exit(1);
            }
            int b = pop(&top);
            int a = pop(&top);
            int result = operation(a, b, postfix[i]);
            push(&top, result);
        }
    }
    if (top == NULL)
    {
        printf("Invalid postfix expression!\n");
        exit(1);
    }
    int result = pop(&top);
    if (top != NULL)
    {
        printf("Invalid postfix expression!\n");
        exit(1);
    }
    return result;
}
int main()
{
    Node *top = NULL;
    int choice, value;
    char postfix[100];
    while (1)
    {
        printf("\n========== STACK MENU ==========\n");
        printf("1. Push\n");
        printf("2. Pop\n");
        printf("3. Display Stack\n");
        printf("4. Evaluate Postfix Expression\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
                printf("Enter value to push: ");
                scanf("%d", &value);
                push(&top, value);
                printf("%d pushed into stack.\n", value);
                break;
            case 2:
                value = pop(&top);
                if (value != -1)
                    printf("Popped element: %d\n", value);
                break;
            case 3:
                display(top);
                break;
            case 4:
                getchar();
                printf("Enter postfix expression: ");
                fgets(postfix, sizeof(postfix), stdin);
                value = evaluatePostfix(postfix);
                printf("Result = %d\n", value);
                break;
            case 5:
                printf("Exiting program...\n");
                return 0;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    }
    return 0;
}
```

## 7. Evaluate infix expressions without converting to postfix.

### Handle spaces, parentheses, and operator precedence

*Source: DSA28F.pdf, pp. 22-23*

```c
// Q7. Write a function which evaluates an infix expression without converting it to postfix. The input string can have spaces, parentheses, and operator precedence.
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#define MAX 100
int values[MAX];
int valueTop = -1;
char operators[MAX];
int operatorTop = -1;
int precedence(char op)
{
    if (op == '+' || op == '-') return 1;
    if (op == '*' || op == '/') return 2;
    return 0;
}
int applyOperation(int a, int b, char op)
{
    switch (op)
    {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/':
            if (b == 0)
            {
                printf("Error: Division by zero!\n");
                exit(1);
            }
            return a / b;
        default:
            printf("Invalid operator!\n");
            exit(1);
    }
}
void pushValue(int value)
{
    values[++valueTop] = value;
}
int popValue()
{
    return values[valueTop--];
}
void pushOperator(char op)
{
    operators[++operatorTop] = op;
}
char popOperator()
{
    return operators[operatorTop--];
}
int evaluateInfix(char expression[])
{
    valueTop = -1;
    operatorTop = -1;
    for (int i = 0; expression[i] != '\0'; i++)
    {
        if (isspace(expression[i]))
            continue;
        if (isdigit(expression[i]))
        {
            int num = 0;
            while (isdigit(expression[i]))
            {
                num = num * 10 + (expression[i] - '0');
                i++;
            }
            pushValue(num);
            i--;
        }
        else if (expression[i] == '(')
            pushOperator(expression[i]);
        else if (expression[i] == ')')
        {
            while (operatorTop != -1 && operators[operatorTop] != '(')
            {
                int b = popValue();
                int a = popValue();
                char op = popOperator();
                pushValue(applyOperation(a, b, op));
            }
            if (operatorTop != -1 && operators[operatorTop] == '(')
                popOperator();
        }
        else
        {
            while (operatorTop != -1 && operators[operatorTop] != '(' &&
                   precedence(operators[operatorTop]) >= precedence(expression[i]))
            {
                int b = popValue();
                int a = popValue();
                char op = popOperator();
                pushValue(applyOperation(a, b, op));
            }
            pushOperator(expression[i]);
        }
    }
    while (operatorTop != -1)
    {
        int b = popValue();
        int a = popValue();
        char op = popOperator();
        pushValue(applyOperation(a, b, op));
    }
    return popValue();
}
int main()
{
    char expression[MAX];
    printf("Enter an infix expression: ");
    fgets(expression, MAX, stdin);
    int result = evaluateInfix(expression);
    printf("Result = %d\n", result);
    return 0;
}
```

## 8. Implement Tower of Hanoi using recursion.

### Tower of Hanoi

*Source: DSA28F.pdf, p. 24*

```c
// Q8. Implement Tower of Hanoi using recursion.
#include <stdio.h>
#include <conio.h>
void towers_of_hanoi(int n, char *a, char *b, char *c);
int cnt = 0;
int main(void)
{
    int n;
    printf("Enter number of discs: ");
    scanf("%d", &n);
    if (n <= 0)
    {
        printf("Number of discs must be positive.\n");
        return 1;
    }
    towers_of_hanoi(n, "Tower 1", "Tower 2", "Tower 3");
    getch();
    return 0;
}
void towers_of_hanoi(int n, char *a, char *b, char *c)
{
    if (n == 1)
    {
        ++cnt;
        printf("\n%5d: Move disk 1 from %s to %s", cnt, a, c);
        return;
    }
    else
    {
        towers_of_hanoi(n - 1, a, c, b);
        ++cnt;
        printf("\n%5d: Move disk %d from %s to %s", cnt, n, a, c);
        towers_of_hanoi(n - 1, b, a, c);
        return;
    }
}
```

## 9. Simulate a deque with insertion and deletion at either end.

### Deque

*Source: DSA28F.pdf, pp. 25-26*

```c
// Q9. Write a program to simulate deque with functions to add and delete elements from either end of the deque.
#include <stdio.h>
#include <stdlib.h>
#define MAX 5
int deque[MAX];
int front = -1, rear = -1;
int isFull()
{
    return ((front == 0 && rear == MAX - 1) || (front == rear + 1));
}
int isEmpty()
{
    return (front == -1);
}
void insertFront(int item)
{
    if (isFull())
    {
        printf("Deque is Overflow\n");
        return;
    }
    if (isEmpty())
        front = rear = 0;
    else if (front == 0)
        front = MAX - 1;
    else
        front--;
    deque[front] = item;
}
void insertRear(int item)
{
    if (isFull())
    {
        printf("Deque is Overflow\n");
        return;
    }
    if (isEmpty())
        front = rear = 0;
    else if (rear == MAX - 1)
        rear = 0;
    else
        rear++;
    deque[rear] = item;
}
int deleteFront()
{
    if (isEmpty())
    {
        printf("Deque is Underflow\n");
        return -1;
    }
    int item = deque[front];
    if (front == rear)
        front = rear = -1;
    else if (front == MAX - 1)
        front = 0;
    else
        front++;
    return item;
}
int deleteRear()
{
    if (isEmpty())
    {
        printf("Deque is Underflow\n");
        return -1;
    }
    int item = deque[rear];
    if (front == rear)
        front = rear = -1;
    else if (rear == 0)
        rear = MAX - 1;
    else
        rear--;
    return item;
}
void display()
{
    if (isEmpty())
    {
        printf("Deque is empty\n");
        return;
    }
    int i = front;
    while (1)
    {
        printf("%d ", deque[i]);
        if (i == rear)
            break;
        i = (i + 1) % MAX;
    }
    printf("\n");
}
int main()
{
    int choice, item;
    do
    {
        printf("\n========== DEQUE MENU ==========\n");
        printf("1. Insert Front\n");
        printf("2. Insert Rear\n");
        printf("3. Delete Front\n");
        printf("4. Delete Rear\n");
        printf("5. Display\n");
        printf("6. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
                printf("Enter item: ");
                scanf("%d", &item);
                insertFront(item);
                break;
            case 2:
                printf("Enter item: ");
                scanf("%d", &item);
                insertRear(item);
                break;
            case 3:
                item = deleteFront();
                if (item != -1)
                    printf("Deleted: %d\n", item);
                break;
            case 4:
                item = deleteRear();
                if (item != -1)
                    printf("Deleted: %d\n", item);
                break;
            case 5:
                display();
                break;
            case 6:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 6);
    return 0;
}
```

## 10. Binary search tree operations.

### Insert, longest path, minimum, mirror, search, and traversals

*Source: dsa1012.pdf, pp. 1-3*

```c
#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *L, *R;
};

struct node *root = NULL;
int count = 0;

struct node *insert(struct node *root, struct node *temp)
{
    if (root == NULL)
        return temp;
    if (temp->data > root->data)
        root->R = insert(root->R, temp);
    else
        root->L = insert(root->L, temp);
    return root;
}

void create()
{
    char ans;
    do
    {
        struct node *temp = (struct node *)malloc(sizeof(struct node));
        if (temp == NULL)
        {
            printf("Memory allocation failed.\n");
            return;
        }
        printf("Enter the data: ");
        scanf("%d", &temp->data);
        temp->L = NULL;
        temp->R = NULL;
        root = insert(root, temp);
        count++;
        printf("Do you want to insert more values (y/n): ");
        scanf(" %c", &ans);
    } while (ans == 'y' || ans == 'Y');
    printf("Total number of nodes: %d\n", count);
}

void disin(struct node *root)
{
    if (root != NULL)
    {
        disin(root->L);
        printf("%d\t", root->data);
        disin(root->R);
    }
}

void dispre(struct node *root)
{
    if (root != NULL)
    {
        printf("%d\t", root->data);
        dispre(root->L);
        dispre(root->R);
    }
}

void dispost(struct node *root)
{
    if (root != NULL)
    {
        dispost(root->L);
        dispost(root->R);
        printf("%d\t", root->data);
    }
}

void search(struct node *root)
{
    int key;
    printf("Enter your key: ");
    scanf("%d", &key);
    while (root != NULL)
    {
        if (key == root->data)
        {
            printf("KEY FOUND\n");
            return;
        }
        else if (key > root->data)
            root = root->R;
        else
            root = root->L;
    }
    printf("KEY NOT FOUND\n");
}

int height(struct node *root)
{
    if (root == NULL)
        return 0;
    int hl = height(root->L);
    int hr = height(root->R);
    return 1 + (hl > hr ? hl : hr);
}

void min(struct node *root)
{
    if (root == NULL)
    {
        printf("Tree is empty.\n");
        return;
    }
    while (root->L != NULL)
        root = root->L;
    printf("Minimum element: %d\n", root->data);
}

void mirror(struct node *root)
{
    if (root != NULL)
    {
        struct node *temp;
        mirror(root->L);
        mirror(root->R);
        temp = root->L;
        root->L = root->R;
        root->R = temp;
    }
}

int main()
{
    int ch;
    char ans;
    do
    {
        printf("\n1) Insert new node");
        printf("\n2) Number of nodes in longest path");
        printf("\n3) Minimum element");
        printf("\n4) Mirror the tree");
        printf("\n5) Search");
        printf("\n6) Inorder");
        printf("\n7) Preorder");
        printf("\n8) Postorder");
        printf("\nEnter your choice: ");
        scanf("%d", &ch);
        switch (ch)
        {
            case 1:
                create();
                break;
            case 2:
                printf("Number of nodes in longest path: %d\n", height(root));
                break;
            case 3:
                min(root);
                break;
            case 4:
                mirror(root);
                printf("Mirror of tree (inorder): ");
                disin(root);
                printf("\n");
                break;
            case 5:
                search(root);
                break;
            case 6:
                printf("INORDER: ");
                disin(root);
                printf("\n");
                break;
            case 7:
                printf("PREORDER: ");
                dispre(root);
                printf("\n");
                break;
            case 8:
                printf("POSTORDER: ");
                dispost(root);
                printf("\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
        printf("Do you want to continue (y/n): ");
        scanf(" %c", &ans);
    } while (ans == 'y' || ans == 'Y');
    return 0;
}
```

## Content Beyond Syllabus

### 11. Build a max heap

*Source: dsa1012.pdf, pp. 5-6*

```c
#include <stdio.h>
#include <stdlib.h>

void heapify(int a[], int n, int i)
{
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;
    int temp;

    if (left < n && a[left] > a[largest])
        largest = left;
    if (right < n && a[right] > a[largest])
        largest = right;
    if (largest != i)
    {
        temp = a[i];
        a[i] = a[largest];
        a[largest] = temp;
        heapify(a, n, largest);
    }
}

void buildMaxHeap(int a[], int n)
{
    int i;
    for (i = n / 2 - 1; i >= 0; i--)
        heapify(a, n, i);
}

void display(int a[], int n)
{
    int i;
    printf("Max Heap: ");
    for (i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
}

int main()
{
    int a[100], n, i;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    if (n < 1 || n > 100)
    {
        printf("Invalid number of elements.\n");
        return 1;
    }
    printf("Enter the elements: ");
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);
    buildMaxHeap(a, n);
    display(a, n);
    return 0;
}
```

### 12. Implement a hash table

*Source: dsa1012.pdf, pp. 7-9*

```c
#include <stdio.h>
#include <stdlib.h>
#define SIZE 10
#define EMPTY -1
#define DELETED -2

int hashTable[SIZE];

int hashFunction(int key)
{
    return key % SIZE;
}

void insert(int key)
{
    if (key == EMPTY || key == DELETED)
    {
        printf("Key is reserved by the hash table.\n");
        return;
    }
    int index = hashFunction(key), start = index;
    do
    {
        if (hashTable[index] == EMPTY || hashTable[index] == DELETED)
        {
            hashTable[index] = key;
            printf("%d inserted successfully.\n", key);
            return;
        }
        if (hashTable[index] == key)
        {
            printf("Element already exists.\n");
            return;
        }
        index = (index + 1) % SIZE;
    } while (index != start);
    printf("Hash table is full!\n");
}

void search(int key)
{
    int index = hashFunction(key), start = index;
    do
    {
        if (hashTable[index] == EMPTY)
            break;
        if (hashTable[index] == key)
        {
            printf("Element found at index %d.\n", index);
            return;
        }
        index = (index + 1) % SIZE;
    } while (index != start);
    printf("Element not found.\n");
}

void deleteKey(int key)
{
    int index = hashFunction(key), start = index;
    do
    {
        if (hashTable[index] == EMPTY)
            break;
        if (hashTable[index] == key)
        {
            hashTable[index] = DELETED;
            printf("%d deleted successfully.\n", key);
            return;
        }
        index = (index + 1) % SIZE;
    } while (index != start);
    printf("Element not found.\n");
}

void display()
{
    int i;
    printf("\nHash Table:\n");
    for (i = 0; i < SIZE; i++)
    {
        if (hashTable[i] == EMPTY)
            printf("[%d] : EMPTY\n", i);
        else if (hashTable[i] == DELETED)
            printf("[%d] : DELETED\n", i);
        else
            printf("[%d] : %d\n", i, hashTable[i]);
    }
}

int main()
{
    int choice, key, i;
    for (i = 0; i < SIZE; i++)
        hashTable[i] = EMPTY;
    do
    {
        printf("\nHash Table Menu\n");
        printf("1. Insert\n");
        printf("2. Search\n");
        printf("3. Delete\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
                printf("Enter key: ");
                scanf("%d", &key);
                insert(key);
                break;
            case 2:
                printf("Enter key to search: ");
                scanf("%d", &key);
                search(key);
                break;
            case 3:
                printf("Enter key to delete: ");
                scanf("%d", &key);
                deleteKey(key);
                break;
            case 4:
                display();
                break;
            case 5:
                printf("Exiting program.\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 5);
    return 0;
}
```

## Important corrections made

- Fixed insertion sort to shift larger values and insert the saved item once, after the shift loop.
- Fixed linked-list insertion at position 1 so it uses the entered value instead of prompting for a second value; invalid positions and allocation failures are handled.
- Added positive-size checks before variable-length arrays in the search and sorting programs.
- Reworked the sparse-matrix listing to provide the syllabus operations directly: initialize, insert/update, row-column sort, transpose, and display.
- Added operand-count and empty-expression checks to postfix evaluation.
- Added a positive disc-count check and a return value to the Tower of Hanoi program.
- Prevented the hash table from accepting its reserved EMPTY and DELETED marker values.
- Updated the infix program description to match the syllabus: it evaluates directly with operator and value stacks without converting the input to postfix.

## Notes on transcription and corrections

The original code screenshots had clipped instruction comments in a few places; the assignment headings above use the legible wording from the syllabus image. The source code is kept as separate programs. The sparse-matrix code is expanded to match the listed operations; the other corrections are noted above.