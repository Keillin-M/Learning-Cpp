# 🔧 Understanding Orthodox Canonical Form in C++

In C++, the **Orthodox Canonical Form (OCF)** is a set of **four special member functions** that a class should define to manage **copying, assignment, and destruction** correctly. It ensures that your objects behave predictably when copied, assigned, or destroyed.

These functions are:

1. **Default constructor**
2. **Copy constructor**
3. **Copy assignment operator**
4. **Destructor**

Some people also include the **move constructor** and **move assignment operator** in modern C++, but OCF traditionally focuses on the four above.

---

# 📍 1. Default Constructor

A **default constructor** creates an object **without requiring initial values**.

## 🧪 Example:

```cpp
class MyClass {
public:
    int x;
    MyClass() : x(0) {} // default constructor
};
```

* Creates a new `MyClass` object
* Initializes `x` to `0`
* Called automatically when you declare `MyClass obj;`

---

# 📍 2. Copy Constructor

A **copy constructor** creates a **new object as a copy of an existing object**.

## 🧪 Example:

```cpp
class MyClass {
public:
    int x;
    MyClass(int val) : x(val) {}             // param constructor
    MyClass(const MyClass &other) : x(other.x) {} // copy constructor
};

MyClass a(10);
MyClass b(a); // copy constructor called
```

* `b` is a new object with the same value as `a`
* Important for **classes with dynamic memory** to avoid shallow copies

---

# 📍 3. Copy Assignment Operator

The **copy assignment operator** lets you **assign one existing object to another** after both are created.

## 🧪 Example:

```cpp
class MyClass {
public:
    int x;
    MyClass() : x(0) {}
    MyClass& operator=(const MyClass &other) {
        if (this != &other) { // avoid self-assignment
            x = other.x;
        }
        return *this;
    }
};

MyClass a, b;
a = b; // copy assignment called
```

* `a` now has the same value as `b`
* Always **check for self-assignment** in complex classes

---

# 📍 4. Destructor

A **destructor** cleans up resources when an object is **destroyed**.

## 🧪 Example:

```cpp
class MyClass {
public:
    ~MyClass() {
        // clean up if needed
    }
};
```

* Called automatically when an object goes **out of scope**
* Essential for classes managing **dynamic memory** or **file handles**

---

# 🧠 Analogy: Object Lifecycle

* **Default constructor 🛠** = Building a new house
* **Copy constructor 🔁** = Cloning an existing house
* **Copy assignment 📝** = Renovating an existing house to match another
* **Destructor 💥** = Demolishing the house when done

---

# 🧠 Quick OCF Table

| Member Function          | Purpose                                |
| ------------------------ | -------------------------------------- |
| Default constructor      | Create new object with default values  |
| Copy constructor         | Create new object as a copy of another |
| Copy assignment operator | Assign one existing object to another  |
| Destructor               | Clean up before object is destroyed    |

---

# 📌 Key Points

* Always define these if your class **manages resources manually** (dynamic memory, file handles, sockets)
* If you don’t, C++ will **generate default versions**, which might cause **shallow copies** and **resource leaks**
* Modern C++ (C++11+) also recommends **move constructor** and **move assignment operator** for efficiency

---

# 🧪 Example in Code (OCF Complete)

```cpp
class MyClass {
private:
    int* data;
public:
    MyClass() : data(new int(0)) {}                 // default
    MyClass(const MyClass &other) : data(new int(*other.data)) {} // copy constructor
    MyClass& operator=(const MyClass &other) {     // copy assignment
        if (this != &other) {
            *data = *other.data;
        }
        return *this;
    }
    ~MyClass() { delete data; }                    // destructor
};
```

* Properly manages dynamic memory
* Avoids shallow copies
* Prevents memory leaks

---

# 🎯 Final Takeaways

* **OCF** = A set of four functions that make a class **safe to copy, assign, and destroy**
* Essential for classes with **manual resource management**
* Modern C++ adds **move semantics**, but OCF is still foundational

---

## 🧠 One-line summary

> **Orthodox Canonical Form ensures your class behaves correctly when copied, assigned, or destroyed.**

