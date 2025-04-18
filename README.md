# Notes C++ Programming Language

## Welcome to the C++ Programming Language Basics Guide

This guide is designed to help beginners understand the fundamental concepts of C++ programming. It covers essential topics such as functions, loops, arrays, pointers, classes, and structures with easy-to-understand code examples and explanations.


---

## Functions in C++

### Explanation

A function is a block of reusable code that performs a specific task. Functions help break down programs into smaller, more manageable pieces. This makes the program easier to debug, maintain, and understand. Functions can return values and accept inputs in the form of parameters.

### Code Example

```cpp
#include <iostream>
using namespace std;

// Function declaration
int add(int a, int b);

int main() {
    int result = add(5, 10);  // Calling the function and passing two integers
    cout << "Sum: " << result << endl;  // Printing the result
    return 0;
}

// Function definition
int add(int a, int b) {
    return a + b;  // Returns the sum of a and b
}
```

### Explanation of Code

- **Function Declaration:** `int add(int a, int b);` - This tells the compiler about the function’s return type (`int`) and the types of parameters it accepts (two `int` values).
- **Main Function:** In `main()`, the function `add(5, 10)` is called with arguments 5 and 10. It returns the sum, which is then printed.
- **Function Definition:** `int add(int a, int b)` defines the function, which calculates the sum of `a` and `b` and returns the result.

---
## Some Question With Their Example And Explaination Of This Topic
---

## Is it possible to call the function in a function ?

#### Yes, it is absolutely possible to call a function from within another function in C++. This is a common practice in programming and is often used to break down complex problems into smaller, more manageable pieces.
### C++ Code Example: Calculating the Square of a Number

```cpp
#include <iostream>
using namespace std;
// Function to calculate the square of a number
int square(int number) {
    return number * number; // Return the square of the number
}

// Function to display the square of a number
void displaySquare(int number) {
    int result = square(number); // Call the square function
    cout << "The square of " << number << " is " <<result<<endl; // Print the result
}

int main() {
    int num = 5; // Define a number
    displaySquare(num); // Call the function to display the square of the number
    return 0; // Indicate that the program ended successfully
}
```

### Explanation:
1. **Function `square(int number)`**:
   - This function takes an integer `number` as input and returns its square (the number multiplied by itself).

2. **Function `displaySquare(int number)`**:
   - This function takes an integer `number`, calls the `square` function to calculate its square, and then prints the result.

3. **`main()` Function**:
   - In the `main` function, we define a number (`num = 5`) and call the `displaySquare` function to show the square of that number.

### Output:
When you run this program, it will display:
```
The square of 5 is 25
```

### Summary:
This example demonstrates how to define and call functions in C++. The `square` function calculates the square of a number, while the `displaySquare` function handles the output. The `main` function serves as the entry point of the program, where the execution begins. This structure helps in organizing code and making it more readable.



## Loops in C++

### Explanation

Loops are used to repeatedly execute a block of code as long as a condition is met. Loops are important for automating repetitive tasks.

### Code Examples

#### For Loop

```cpp
for(int i = 1; i <= 5; i++) {
    cout << i << " ";
}
```

- **Initialization:** `int i = 1;` - Starts with `i` equal to 1.
- **Condition:** `i <= 5;` - The loop continues as long as `i` is less than or equal to 5.
- **Increment:** `i++` - Increments `i` by 1 in each iteration.
- The loop will print: `1 2 3 4 5`.

#### While Loop

```cpp
int i = 1;
while(i <= 5) {
    cout << i << " ";
    i++;  // Increment
}
```

- The loop runs as long as `i <= 5`.
- It prints the numbers `1 2 3 4 5` and increments `i` each time.

#### Do-While Loop

```cpp
int i = 1;
do {
    cout << i << " ";
    i++;  // Increment
} while(i <= 5);
```

- The do-while loop guarantees that the code block runs at least once, even if the condition (`i <= 5`) is false on the first check.

---

## Arrays in C++

### Explanation

An array is a collection of elements of the same data type, stored in contiguous memory locations. Arrays make it easy to manage and process a large number of similar items.

### Code Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};  // Array initialization

    // Accessing elements using a loop
    for(int i = 0; i < 5; i++) {
        cout << arr[i] << " ";  // Prints each element in the array
    }

    return 0;
}
```

### Explanation of Code

- **Array Initialization:** `int arr[5] = {10, 20, 30, 40, 50};` defines an array of 5 integers.
- **Accessing Array Elements:** The `for` loop accesses and prints each element of the array by using the index `i`.

---

### Is it possible to search the value in Arry through Function or without Function ?

##### Yes, it is possible to search for a value in an array in C++ both with and without using a function. Below are examples of both methods along with explanations.

### Method 1: Searching Without a Function

In this method, we will directly search for a value in the array using a simple loop.

```cpp
#include <iostream>
using namespace std;
int main() {
    int arr[] = {10, 20, 30, 40, 50}; // Array of integers
    int size = sizeof(arr) / sizeof(arr[0]); // Calculate the size of the array
    int valueToFind = 30; // Value to search for
    bool found = false; // Flag to indicate if the value is found

    // Loop through the array
    for (int i = 0; i < size; i++) {
        if (arr[i] == valueToFind) { // Check if the current element matches the value
            found = true; // Set the flag to true
             cout << "Value " << valueToFind << " found at index " << i <<  endl;
            break; // Exit the loop since we found the value
        }
    }

    if (!found) {
         cout << "Value " << valueToFind << " not found in the array." <<  endl;
    }

    return 0;
}
```

#### Explanation:

1. We define an array `arr` with some integer values.
2. We calculate the size of the array using `sizeof(arr) / sizeof(arr[0])`.
3. We set the value we want to find (`valueToFind`) and a boolean flag (`found`) to track if the value is found.
4. We use a `for` loop to iterate through each element of the array.
5. Inside the loop, we check if the current element matches `valueToFind`. If it does, we print the index and set `found` to `true`, then break out of the loop.
6. After the loop, we check if `found` is still `false` and print a message if the value was not found.

### Method 2: Searching With a Function

In this method, we will create a function to encapsulate the search logic.

```cpp
#include <iostream>

// Function to search for a value in an array
int searchInArray(int arr[], int size, int valueToFind) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == valueToFind) {
            return i; // Return the index if found
        }
    }
    return -1; // Return -1 if not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50}; // Array of integers
    int size = sizeof(arr) / sizeof(arr[0]); // Calculate the size of the array
    int valueToFind = 30; // Value to search for

    // Call the search function
    int index = searchInArray(arr, size, valueToFind);

    if (index != -1) {
        cout << "Value " << valueToFind << " found at index " << index <<endl;
    } else {
        cout << "Value " << valueToFind << " not found in the array." <<endl;
    }

    return 0;
}
```

#### Explanation:
1. We define a function `searchInArray` that takes an array, its size, and the value to find as parameters.
2. Inside the function, we use a `for` loop to iterate through the array, similar to the previous example.
3. If the value is found, we return the index; if not, we return `-1`.
4. In the `main` function, we call `searchInArray` and store the returned index.
5. We check if the index is not `-1` to determine if the value was found and print the appropriate message.

Both methods effectively search for a value in an array, but using a function can make your code cleaner and more modular, especially if you need to perform the search operation multiple times.

### Summary
- **Without a function**: We write the search logic directly in the main part of the program.
- **With a function**: We create a reusable tool (function) that can search for numbers in any list, making our code cleaner and easier to manage.

### How to check the in an Arry the output value is user define value or garbage value?

In C++, when you declare an array, the values it contains are not automatically initialized. If you don't explicitly set the values, they may contain "garbage values," which are essentially random data left in memory. To determine whether a value in an array is a garbage value or a user-defined value, you can follow these steps:

1. **Initialize the Array**: Always initialize your array when you declare it. This way, you can avoid garbage values.

2. **Use a Sentinel Value**: If you want to check for user-defined values, you can use a special value (sentinel) that you know will not be used as a valid value in your array.

3. **Check for Initialization**: If you want to check if a value is garbage, you can compare it against known valid values or use a flag to indicate whether a value has been set.

### Example Code

Here’s an example that demonstrates how to initialize an array and check for garbage values:

```cpp
#include <iostream>
using namespace std;

int main() {
    const int SIZE = 5;
    int arr[SIZE]; // Declare an array of size 5

    // Initialize the array with a known value (e.g., -1) to indicate "not set"
    for (int i = 0; i < SIZE; i++) {
        arr[i] = -1; // Using -1 as a sentinel value
    }

    // Simulate user-defined values
    arr[2] = 25;
    arr[4] = 50;

    // Check the values in the array
    for (int i = 0; i < SIZE; i++) {
        if (arr[i] == -1) {
            cout << "Index " << i << " has a garbage value (not set)." <<endl;
        } else {
            cout << "Index " << i << " has a user-defined value: " << arr[i] <<endl;
        }
    }

    return 0;
}
```

### Explanation:
1. **Array Declaration**: We declare an array `arr` of size 5.
2. **Initialization**: We initialize all elements of the array to `-1`, which we use as a sentinel value to indicate that the value has not been set by the user.
3. **Setting User-Defined Values**: We assign user-defined values to specific indices in the array.
4. **Checking Values**: We loop through the array and check each value:
   - If the value is `-1`, we print that it has a garbage value (or is not set).
   - If it has a different value, we print that it has a user-defined value.

### Important Note:
- **Garbage Values**: If you do not initialize the array, the values will be whatever was previously in that memory location, which is unpredictable (garbage).
---


## Pointers in C++

### Explanation

A pointer is a variable that stores the memory address of another variable. Pointers are crucial for dynamic memory management and working with complex data structures such as linked lists.

### Code Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 10;
    int* ptr = &num;  // Pointer stores the address of num

    cout << "Value of num: " << num << endl;  // Prints the value of num
    cout << "Address of num: " << &num << endl;  // Prints the address of num
    cout << "Pointer points to: " << ptr << endl;  // Prints the address stored in ptr
    cout << "Value at pointer: " << *ptr << endl;  // Dereferencing pointer to get value

    return 0;
}
```

### Explanation of Code

- **Pointer Declaration:** `int* ptr = &num;` - `ptr` is a pointer to an integer, and it stores the memory address of the variable `num`.
- **Dereferencing:** `*ptr` accesses the value stored at the memory address pointed to by `ptr`.

---

## Classes in C++

### Explanation

A class is a user-defined data type that bundles data and methods (functions) together. It is the foundation of Object-Oriented Programming (OOP) in C++.

### Code Example

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    int speed;

    void display() {
        cout << "Brand: " << brand << ", Speed: " << speed << " km/h" << endl;
    }
};

int main() {
    Car car1;  // Creating an object of class Car
    car1.brand = "Toyota";  // Assigning values to the object
    car1.speed = 120;
    car1.display();  // Calling method to display car details

    return 0;
}
```

### Explanation of Code

- **Class Declaration:** `class Car` defines a class with two attributes: `brand` and `speed`, and a method `display()` that prints the car's details.
- **Object Creation:** `Car car1;` creates an object `car1` of the class `Car`.
- **Accessing Members:** `car1.brand` and `car1.speed` set the attributes of the object, and `car1.display()` calls the method to display the car's details.

---

## Structures in C++

### Explanation

A structure (or struct) is similar to a class but does not support access modifiers (like private or public) by default. It is used to group different types of data together.

### Code Example

```cpp
#include <iostream>
using namespace std;

struct Student {
    string name;
    int age;
    float marks;
};

int main() {
    Student s1 = {"Alice", 20, 85.5};  // Creating and initializing a struct object

    cout << "Name: " << s1.name << endl;  // Accessing struct members
    cout << "Age: " << s1.age << endl;
    cout << "Marks: " << s1.marks << endl;

    return 0;
}
```

### Explanation of Code

- **Struct Declaration:** `struct Student` defines a structure to hold student information, such as name, age, and marks.
- **Object Initialization:** `Student s1 = {"Alice", 20, 85.5};` creates a `Student` object `s1` and initializes its members.
- **Accessing Members:** `s1.name`, `s1.age`, and `s1.marks` access the individual fields of the structure.

---
