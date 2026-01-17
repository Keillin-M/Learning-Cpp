# 🧩 **Abstract Classes**

An **abstract class** is a class that **cannot be instantiated** and is designed to be **inherited from**.
It defines a common interface while leaving implementation details to derived classes.

In C++, a class becomes abstract when it contains **at least one pure virtual function**.

---

## 🧩 **Why Use Abstract Classes?**

* ✅ Enforce a common interface
* ✅ Enable polymorphism
* ✅ Prevent invalid object creation
* ✅ Improve code design and consistency

---

## 🏗️ **Basic Syntax (C++)**

```cpp
class Animal {
public:
    virtual void speak() const = 0;
};
```

Here:

* `= 0` makes the function **pure virtual**
* `Animal` becomes an **abstract class**
* Objects of `Animal` **cannot be created**

---

## ❌ **Invalid Usage**

```cpp
Animal a; // ❌ Compilation error
```

---

## ✅ **Derived Class Implementation**

```cpp
class Dog : public Animal {
public:
    void speak() const override {
        std::cout << "Woof!" << std::endl;
    }
};
```

```cpp
Animal* a = new Dog();
a->speak(); // Calls Dog::speak()
```

---

## 🔑 **Key Characteristics**

| Feature               | Description       |
| --------------------- | ----------------- |
| Instantiation         | ❌ Not allowed     |
| Inheritance           | ✅ Required        |
| Polymorphism          | ✅ Fully supported |
| Interface enforcement | ✅ Guaranteed      |

---

## 🧪 **Abstract Class with Concrete Methods**

Abstract classes can still contain **implemented functions**.

```cpp
class Animal {
public:
    virtual void speak() const = 0;

    void breathe() const {
        std::cout << "Breathing..." << std::endl;
    }
};
```

Derived classes must implement `speak()` but automatically inherit `breathe()`.

---

## 🧠 **Abstract Classes vs Interfaces**

| Concept          | C++ Abstract Class       |
| ---------------- | ------------------------ |
| Pure virtual     | Required for abstraction |
| Data members     | Allowed                  |
| Method bodies    | Allowed                  |
| Multiple inherit | Allowed                  |

> In C++, **interfaces are implemented using abstract classes**.

---

## ⚠️ **Common Pitfalls**

* Forgetting to implement all pure virtual functions
* Missing `virtual` destructor
* Signature mismatch (`const`, references)
* Instantiating through value instead of pointer/reference

---

## 🛑 **Abstract Destructors**

Even destructors can be abstract — but must be implemented.

```cpp
class Animal {
public:
    virtual ~Animal() = 0;
};

Animal::~Animal() {}
```

---

## 📋 **Summary Table**

| Term           | Meaning                                |
| -------------- | -------------------------------------- |
| Abstract class | Class with pure virtual functions      |
| Pure virtual   | Function with `= 0`                    |
| Interface      | Abstract class with only pure virtuals |
| Polymorphism   | Enabled via base pointers              |

---

# 🧠 **Abstract Class Analogy: Blueprint**

* **Abstract class:** A building blueprint
* You cannot live in a blueprint
* You must build a real house from it

### **In Programming Terms:**

* Abstract classes define *what* must exist
* Derived classes define *how* it works

---

## 🧾 **Key Takeaways**

* Abstract classes cannot be instantiated
* Used to define interfaces
* Require inheritance
* Essential for polymorphism
* Fundamental in modern C++ design

