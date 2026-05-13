# C++ Comprehensive Cheatsheet

> **Complete C++ cheatsheet covering basics to modern C++20: data types, control flow, OOP, STL containers & algorithms, pointers, smart pointers, lambdas, file I/O, exception handling, and advanced features. Perfect quick reference for beginners and pros. Includes compilation commands and practical examples.**

## Table of Contents
1. [Basic Structure](#1-basic-structure)
2. [Data Types & Variables](#2-data-types--variables)
3. [Operators](#3-operators)
4. [Control Flow](#4-control-flow)
5. [Functions](#5-functions)
6. [Arrays & Strings](#6-arrays--strings)
7. [Pointers & References](#7-pointers--references)
8. [Dynamic Memory](#8-dynamic-memory)
9. [Object-Oriented Programming](#9-object-oriented-programming)
10. [Inheritance & Polymorphism](#10-inheritance--polymorphism)
11. [Exception Handling](#11-exception-handling)
12. [STL Containers](#12-stl-containers)
13. [STL Algorithms](#13-stl-algorithms)
14. [File I/O](#14-file-io)
15. [Modern C++ (C++11/14/17/20)](#15-modern-c-c11141720)
16. [Preprocessor Directives](#16-preprocessor-directives)

---

## 1. Basic Structure

```cpp
#include <iostream>  // Header inclusion

// Namespace declaration
using namespace std;  // Not recommended for large projects

// Entry point
int main() {
    cout << "Hello, World!" << endl;
    return 0;  // 0 indicates success
}
```

**Compile & Run:**
```bash
g++ -std=c++17 -o output source.cpp
./output
```

---

## 2. Data Types & Variables

### Primitive Types
```cpp
// Integers
int a = 10;              // 4 bytes
short b = 5;             // 2 bytes
long c = 100L;           // 8 bytes
long long d = 100LL;     // 8 bytes

// Unsigned
unsigned int e = 20;

// Floating point
float f = 3.14f;         // 4 bytes
double g = 3.14159;      // 8 bytes

// Character
char h = 'A';            // 1 byte
wchar_t i = L'B';        // 2-4 bytes

// Boolean
bool j = true;           // 1 byte

// Void (no value)
void myFunction() {}
```

### Type Modifiers
```cpp
signed int x = -10;
unsigned int y = 10;
const int z = 100;       // Cannot modify
volatile int w = 200;    // May change unexpectedly
```

### Type Deduction
```cpp
auto x = 10;             // int
auto y = 3.14;           // double
auto z = "Hello";        // const char*
decltype(x) w = 20;      // int
```

---

## 3. Operators

### Arithmetic
```cpp
+  -  *  /  %    // Basic
++  --           // Increment/Decrement
```

### Relational
```cpp
==  !=  <  >  <=  >=
```

### Logical
```cpp
&&  ||  !
```

### Bitwise
```cpp
&  |  ^  ~  <<  >>
```

### Assignment
```cpp
=  +=  -=  *=  /=  %=  &=  |=  ^=  <<=  >>=
```

### Ternary
```cpp
condition ? expr1 : expr2;
// Example: int max = (a > b) ? a : b;
```

### sizeof
```cpp
size_t size = sizeof(int);  // Returns bytes
```

---

## 4. Control Flow

### If-Else
```cpp
if (condition) {
    // code
} else if (condition2) {
    // code
} else {
    // code
}
```

### Switch
```cpp
switch (expression) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code
}
```

### Loops
```cpp
// For loop
for (int i = 0; i < 10; i++) {
    // code
}

// Range-based for (C++11)
for (auto& elem : container) {
    // code
}

// While loop
while (condition) {
    // code
}

// Do-while loop
do {
    // code
} while (condition);

// Break & Continue
break;   // Exit loop
continue; // Skip to next iteration
```

---

## 5. Functions

### Basic Function
```cpp
// Declaration (prototype)
int add(int a, int b);

// Definition
int add(int a, int b) {
    return a + b;
}
```

### Parameters
```cpp
// Pass by value
void func1(int x) { x = 10; }  // Original unchanged

// Pass by reference
void func2(int& x) { x = 10; }  // Original modified

// Pass by pointer
void func3(int* x) { *x = 10; } // Original modified

// Default arguments
void func4(int x, int y = 10) {}

// Function overloading
void print(int x) {}
void print(double x) {}
void print(string s) {}

// Inline functions
inline int square(int x) { return x * x; }
```

### Lambda Expressions (C++11)
```cpp
[capture](parameters) -> return_type { body };

// Examples:
auto sum = [](int a, int b) { return a + b; };
auto add2 = [](int x) { return x + 2; };

// Capture:
[&]  // Capture all by reference
[=]  // Capture all by value
[x]  // Capture x by value
[&x] // Capture x by reference
```

---

## 6. Arrays & Strings

### C-Style Arrays
```cpp
// Declaration
int arr[5];                    // Uninitialized
int arr2[5] = {1, 2, 3, 4, 5}; // Initialized
int arr3[] = {1, 2, 3};        // Size inferred

// Multi-dimensional
int matrix[3][4] = {{1,2,3,4}, {5,6,7,8}};

// Access
arr[0] = 10;                   // First element
```

### C++ Strings (`<string>`)
```cpp
#include <string>
using namespace std;

string s1 = "Hello";
string s2("World");
string s3 = s1 + " " + s2;     // Concatenation

// Methods
s1.length();                   // Size
s1.size();                     // Also size
s1.empty();                    // Check empty
s1.substr(0, 5);              // Substring
s1.find("ell");                // Find substring (returns index)
s1.replace(0, 2, "Heaven");   // Replace
s1.push_back('!');             // Add char
s1.pop_back();                 // Remove last char
s1.c_str();                    // Convert to C-string

// Iterators
for (char c : s1) { cout << c; }
```

---

## 7. Pointers & References

### Pointers
```cpp
int x = 10;
int* ptr = &x;      // Pointer to int
int* ptr2 = nullptr; // Null pointer

// Dereferencing
*ptr = 20;          // x becomes 20

// Pointer arithmetic
int arr[5] = {1,2,3,4,5};
int* p = arr;       // Points to arr[0]
p++;                // Points to arr[1]

// Pointer to pointer
int** pptr = &ptr;
```

### References
```cpp
int x = 10;
int& ref = x;       // Reference (alias)
ref = 20;           // x becomes 20

// Const reference (prevents modification)
const int& cref = x;
// cref = 30;       // Error!
```

### Function Pointers
```cpp
int (*funcPtr)(int, int) = &add;
int result = funcPtr(5, 3);
```

---

## 8. Dynamic Memory

### C-Style (Not recommended)
```cpp
#include <cstdlib>
int* p = (int*)malloc(10 * sizeof(int));
free(p);
```

### C++ Operators
```cpp
// Single object
int* p = new int;       // Allocate
*p = 10;
delete p;               // Deallocate

int* p2 = new int(20);  // Allocate with initialization
delete p2;

// Array
int* arr = new int[10]; // Allocate array
delete[] arr;           // Deallocate array

// Multi-dimensional
int** matrix = new int*[rows];
for (int i = 0; i < rows; i++)
    matrix[i] = new int[cols];

// Deletion
for (int i = 0; i < rows; i++)
    delete[] matrix[i];
delete[] matrix;
```

### Smart Pointers (C++11) - `<memory>`
```cpp
#include <memory>

// unique_ptr (exclusive ownership)
unique_ptr<int> uptr = make_unique<int>(10);
// unique_ptr<int> uptr2 = uptr; // Error! No copy

// shared_ptr (shared ownership)
shared_ptr<int> sptr1 = make_shared<int>(20);
shared_ptr<int> sptr2 = sptr1;   // Reference count = 2

// weak_ptr (non-owning)
weak_ptr<int> wptr = sptr1;
if (auto sp = wptr.lock()) {
    // Use sp safely
}
```

---

## 9. Object-Oriented Programming

### Class Basics
```cpp
class Person {
private:        // Access specifier
    string name;
    int age;
    
protected:      // Accessible to derived classes
    int id;
    
public:         // Accessible to everyone
    // Constructor
    Person() : name("Unknown"), age(0) {}  // Initializer list
    Person(string n, int a) : name(n), age(a) {}
    
    // Destructor
    ~Person() { cout << "Destroyed" << endl; }
    
    // Copy constructor
    Person(const Person& other) : name(other.name), age(other.age) {}
    
    // Assignment operator
    Person& operator=(const Person& other) {
        if (this != &other) {
            name = other.name;
            age = other.age;
        }
        return *this;
    }
    
    // Methods
    void setName(string n) { name = n; }
    string getName() const { return name; }  // Const method
    virtual void display() const {  // Virtual for polymorphism
        cout << name << ", " << age << endl;
    }
    
    // Static member
    static int count;
};

// Static member definition
int Person::count = 0;
```

### Struct (C-style, public by default)
```cpp
struct Point {
    int x, y;
    // Methods allowed
    void print() { cout << x << ", " << y; }
};
```

### Enum
```cpp
enum Color { RED, GREEN, BLUE };
enum class Status { OK, ERROR, PENDING };  // Scoped enum (C++11)

Color c = RED;
Status s = Status::OK;
```

---

## 10. Inheritance & Polymorphism

### Inheritance
```cpp
class Student : public Person {  // Public inheritance
private:
    int studentId;
    
public:
    Student(string n, int a, int id) : Person(n, a), studentId(id) {}
    
    // Override virtual function
    void display() const override {  // 'override' keyword (C++11)
        Person::display();
        cout << "ID: " << studentId << endl;
    }
};

// Multiple inheritance
class TeachingAssistant : public Student, public Teacher {
    // ...
};
```

### Polymorphism
```cpp
// Base class pointer to derived object
Person* ptr = new Student("Alice", 20, 12345);
ptr->display();  // Calls Student::display() (virtual)
delete ptr;

// Abstract class (has pure virtual function)
class Shape {
public:
    virtual double area() const = 0;  // Pure virtual
    virtual ~Shape() {}               // Virtual destructor
};
```

### Virtual Functions
```cpp
class Base {
public:
    virtual void func() { cout << "Base"; }
    virtual ~Base() {}  // Always virtual in base classes
};

class Derived : public Base {
public:
    void func() override { cout << "Derived"; }
};
```

---

## 11. Exception Handling

```cpp
#include <stdexcept>

try {
    // Code that may throw
    if (error)
        throw runtime_error("Error message");
        
} catch (const runtime_error& e) {
    cout << "Runtime error: " << e.what() << endl;
    
} catch (const logic_error& e) {
    // Handle logic errors
    
} catch (const exception& e) {
    // Catch any standard exception
    
} catch (...) {
    // Catch any exception
    cout << "Unknown exception" << endl;
}

// Throw from function
void func() throw(exception) {  // Deprecated in C++11
    throw runtime_error("Error");
}

// Noexcept specifier (C++11)
void safeFunc() noexcept {
    // Guarantees no throw
}
```

### Standard Exceptions
- `std::exception` - base class
- `std::runtime_error` - runtime errors
- `std::logic_error` - logic errors
- `std::out_of_range` - array index out of bounds
- `std::invalid_argument` - invalid argument

---

## 12. STL Containers

### Sequence Containers
```cpp
#include <vector>
vector<int> v = {1, 2, 3, 4};
v.push_back(5);          // Add to end
v.pop_back();            // Remove from end
v.size();                // Size
v[0];                    // Access (no bounds check)
v.at(0);                 // Access (with bounds check)
v.insert(v.begin(), 0);  // Insert at beginning
v.erase(v.begin());      // Erase first element

#include <deque>
deque<int> dq = {1, 2, 3};
dq.push_front(0);        // Add to front
dq.push_back(4);         // Add to back
dq.pop_front();          // Remove from front

#include <list>
list<int> lst = {1, 2, 3};
lst.push_back(4);
lst.push_front(0);
lst.remove(2);           // Remove all elements with value 2

#include <array>          // C++11
array<int, 5> arr = {1, 2, 3, 4, 5};
arr.size();              // Always 5
```

### Associative Containers
```cpp
#include <set>
set<int> s = {3, 1, 4, 1, 5};  // Sorted, unique
s.insert(2);
s.count(3);              // Returns 1 if exists
s.find(4);               // Returns iterator or end()

#include <map>
map<string, int> m;
m["apple"] = 5;
m["banana"] = 3;
m.insert({"cherry", 7});
for (auto& [key, value] : m) {  // C++17 structured binding
    cout << key << ": " << value;
}

#include <unordered_set>
#include <unordered_map>
// Same interface as set/map but unsorted (hash table)
```

### Container Adapters
```cpp
#include <stack>
stack<int> st;
st.push(1);
st.top();                // Access top
st.pop();

#include <queue>
queue<int> q;
q.push(1);
q.front();               // Access front
q.back();                // Access back
q.pop();

#include <priority_queue>
priority_queue<int> pq;  // Max heap
pq.push(5);
pq.top();                // Largest element
```

---

## 13. STL Algorithms

Include `<algorithm>` and `<numeric>`:

```cpp
#include <algorithm>
#include <numeric>

// Sorting
sort(v.begin(), v.end());                 // Ascending
sort(v.begin(), v.end(), greater<int>()); // Descending
sort(v.begin(), v.end(), [](int a, int b) { return a > b; });

// Searching
auto it = find(v.begin(), v.end(), 3);    // Linear search
bool exists = binary_search(v.begin(), v.end(), 3); // Binary search

// Modifying
fill(v.begin(), v.end(), 0);              // Fill with 0
reverse(v.begin(), v.end());              // Reverse order
rotate(v.begin(), v.begin()+2, v.end());  // Rotate
replace(v.begin(), v.end(), 3, 99);       // Replace values

// Copying
copy(v.begin(), v.end(), back_inserter(v2));

// Min/Max
int mx = *max_element(v.begin(), v.end());
int mn = *min_element(v.begin(), v.end());

// Accumulate (numeric)
int sum = accumulate(v.begin(), v.end(), 0);

// Remove duplicates
auto last = unique(v.begin(), v.end());
v.erase(last, v.end());

// Permutations
next_permutation(v.begin(), v.end());
prev_permutation(v.begin(), v.end());

// For each
for_each(v.begin(), v.end(), [](int& x) { x *= 2; });
```

---

## 14. File I/O

Include `<fstream>`:

```cpp
#include <fstream>

// Writing
ofstream outfile("file.txt");
if (outfile.is_open()) {
    outfile << "Hello, file!" << endl;
    outfile.close();
}

// Reading
ifstream infile("file.txt");
string line;
if (infile.is_open()) {
    while (getline(infile, line)) {
        cout << line << endl;
    }
    infile.close();
}

// Binary file
ofstream out("data.bin", ios::binary);
int num = 42;
out.write(reinterpret_cast<char*>(&num), sizeof(num));
out.close();

ifstream in("data.bin", ios::binary);
int readNum;
in.read(reinterpret_cast<char*>(&readNum), sizeof(readNum));

// File modes
ios::in      // Open for reading
ios::out     // Open for writing
ios::app     // Append to end
ios::binary  // Binary mode
ios::trunc   // Truncate file

// Checking state
ifstream f("test.txt");
f.is_open();   // Check if open
f.good();      // Check if no errors
f.bad();       // Check if serious error
f.eof();       // End of file
```

---

## 15. Modern C++ (C++11/14/17/20)

### C++11 Features
```cpp
// Auto type deduction
auto i = 10;
auto f = 3.14;
auto s = "string";

// Range-based for
for (auto& elem : container) {}

// Initializer lists
vector<int> v = {1, 2, 3, 4};

// nullptr
int* p = nullptr;  // Instead of NULL

// Strongly typed enums
enum class Color { Red, Green, Blue };

// Static assertions
static_assert(sizeof(int) == 4, "int is not 4 bytes");

// Delegating constructors
class Foo {
    Foo() : Foo(0) {}
    Foo(int x) : value(x) {}
    int value;
};

// Move semantics
vector<BigObject> v;
v.push_back(std::move(obj));  // Move instead of copy

// constexpr
constexpr int square(int x) { return x * x; }
int arr[square(5)];  // Compile-time evaluation

// Threading
#include <thread>
thread t([]() { cout << "Hello from thread"; });
t.join();
```

### C++14 Features
```cpp
// Generic lambdas
auto lambda = [](auto x, auto y) { return x + y; };

// Return type deduction
auto func() { return 42; }

// make_unique (C++14)
auto ptr = make_unique<int>(10);

// Binary literals
int x = 0b1010;  // 10
```

### C++17 Features
```cpp
// Structured bindings
auto [a, b] = pair<int, int>(1, 2);
auto& [key, value] = *map.begin();

// if with initializer
if (auto it = map.find(key); it != map.end()) {
    cout << it->second;
}

// Fold expressions (variadic templates)
template<typename... Args>
auto sum(Args... args) {
    return (args + ...);
}

// inline variables
struct S { inline static int x = 0; };

// std::filesystem
#include <filesystem>
namespace fs = std::filesystem;
fs::path p = "test.txt";
```

### C++20 Features
```cpp
// Concepts
template<typename T>
concept Addable = requires(T a, T b) { a + b; };

auto add(Addable auto a, Addable auto b) { return a + b; }

// Ranges
#include <ranges>
auto squares = views::iota(0) | views::transform([](int x) { return x*x; }) | views::take(10);

// Coroutines (advanced)
// Spaceship operator <=>
auto result = a <=> b;  // Three-way comparison

// std::format (Python-like formatting)
std::cout << std::format("Hello {}!", "world");
```

---

## 16. Preprocessor Directives

```cpp
// Include
#include <iostream>     // System header
#include "myheader.h"   // User header

// Macros
#define PI 3.14159
#define SQUARE(x) ((x)*(x))  // Always use parentheses

// Undefine
#undef PI

// Conditional compilation
#ifdef DEBUG
    cout << "Debug info" << endl;
#endif

#ifndef HEADER_H
#define HEADER_H
// Header guard
#endif

#if defined(__cplusplus) && __cplusplus >= 201703L
    // C++17 or later
#endif

// Predefined macros
__cplusplus   // C++ language version
__LINE__      // Current line number
__FILE__      // Current file name
__DATE__      // Compilation date
__TIME__      // Compilation time
__func__      // Current function name (C++11)

// Pragma
#pragma once  // Alternative header guard
#pragma warning(disable: 4996)  // Disable warning
```

---

## Quick Reference: Common Patterns

### Console I/O
```cpp
#include <iostream>
using namespace std;

cout << "Output" << endl;
int x; cin >> x;
cerr << "Error message" << endl;
clog << "Log message" << endl;
```

### String to Number
```cpp
#include <string>
int i = stoi("123");
float f = stof("3.14");
double d = stod("2.718");
long l = stol("123456");

string s = to_string(123);  // "123"
```

### Random Numbers (C++11)
```cpp
#include <random>
random_device rd;
mt19937 gen(rd());
uniform_int_distribution<> dis(1, 100);
int random = dis(gen);
```

### Chrono (Timing)
```cpp
#include <chrono>
using namespace std::chrono;

auto start = high_resolution_clock::now();
// ... code ...
auto end = high_resolution_clock::now();
auto duration = duration_cast<milliseconds>(end - start);
cout << "Time: " << duration.count() << "ms";
```

---
