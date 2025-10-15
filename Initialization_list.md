# 📝 **Initialization List in C++ Constructors**

An **initialization list** in C++ allows you to initialize member variables directly before the constructor body runs. It’s placed after the constructor’s parameter list and a colon (`:`), followed by a comma-separated list of member initializations.

---

## 🔍 **Why Use Initialization List?**

- **Efficiency:** Member variables are initialized directly, rather than default-constructed and then assigned inside the constructor body.
- **Required for certain members:** Some types (like `const` or reference members) **must** be initialized this way.
- **Supports base class initialization:** You can also initialize base class constructors.

---

## 🧪 **Example**

```cpp
class Car {
public:
    const int wheels;
    std::string color;

    Car(int numWheels, std::string col)
        : wheels(numWheels), color(col) // initialization list
    {
        // Constructor body (runs after member variables are initialized)
        std::cout << "Car created!" << std::endl;
    }
};
```
- Here, `wheels` and `color` are initialized *before* the constructor body runs.
- You **must use** an initialization list for `const int wheels` because `const` members cannot be assigned after construction.

---

## ⚡ **When Is It Required?**

- For `const` members  
- For reference members (`int& x;`)
- When calling base class constructors with arguments

---

## 🧭 **Base Class Initialization Example**

```cpp
class Vehicle {
public:
    Vehicle(int id) { /* ... */ }
};

class Car : public Vehicle {
public:
    Car(int id) : Vehicle(id) { /* ... */ } // calls Vehicle's constructor
};
```

---

## 📋 **Summary**

- An **initialization list** sets member variables before entering the constructor body.
- It is **efficient, sometimes necessary**, and supports base class initialization.
