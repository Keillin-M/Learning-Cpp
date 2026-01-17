# 🔌 **Interfaces (C++)**

An **interface** defines a **contract**: a set of functions that a class **must implement**, without providing any implementation details.

C++ does not have a dedicated `interface` keyword.
Instead, interfaces are implemented using **pure abstract classes**.

---

## 🧩 **Why Use Interfaces?**

* ✅ Enforce a strict API
* ✅ Decouple implementation from usage
* ✅ Enable polymorphism
* ✅ Improve scalability and testability

---

## 🏗️ **How Interfaces Are Implemented in C++**

An interface in C++ is:

* A class with **only pure virtual functions**
* No data members
* A **virtual destructor**

---

## 🏗️ **Basic Interface Example**

```cpp
class IAnimal {
public:
    virtual ~IAnimal() {}
    virtual void speak() const = 0;
};
```

Here:

* `IAnimal` is an **interface**
* All methods are **pure virtual**
* Naming convention: `I` prefix (common, optional)

---

## ❌ **Invalid Usage**

```cpp
IAnimal a; // ❌ Cannot instantiate an interface
```

---

## ✅ **Implementing an Interface**

```cpp
class Dog : public IAnimal {
public:
    void speak() const override {
        std::cout << "Woof!" << std::endl;
    }
};
```

```cpp
IAnimal* a = new Dog();
a->speak(); // Calls Dog::speak()
```

---

## 🔑 **Interface Characteristics**

| Feature               | Interface (C++)   |
| --------------------- | ----------------- |
| Instantiation         | ❌ Not allowed     |
| Method implementation | ❌ Not allowed     |
| Data members          | ❌ Not allowed     |
| Multiple inheritance  | ✅ Allowed         |
| Polymorphism          | ✅ Fully supported |

---

## 🧬 **Multiple Interfaces**

A class can implement **multiple interfaces**.

```cpp
class IFlyable {
public:
    virtual ~IFlyable() {}
    virtual void fly() const = 0;
};

class ISwimmable {
public:
    virtual ~ISwimmable() {}
    virtual void swim() const = 0;
};

class Duck : public IFlyable, public ISwimmable {
public:
    void fly() const override;
    void swim() const override;
};
```

---

## ⚠️ **Interfaces vs Abstract Classes**

| Aspect            | Interface         | Abstract Class          |
| ----------------- | ----------------- | ----------------------- |
| Purpose           | Define a contract | Share interface + logic |
| Pure virtual only | ✅ Yes             | ❌ Not required          |
| Data members      | ❌ No              | ✅ Allowed               |
| Default behavior  | ❌ No              | ✅ Allowed               |

---

## 🚫 **Common Interface Pitfalls**

* Forgetting a virtual destructor
* Adding data members
* Partial implementation in derived class
* Signature mismatches (`const`, references)
* Not using pointers/references

---

## 📋 **Summary Table**

| Term         | Meaning                            |
| ------------ | ---------------------------------- |
| Interface    | Pure abstract class                |
| Contract     | Functions that must be implemented |
| `= 0`        | Pure virtual function              |
| Polymorphism | Behavior via base pointer          |

---

# 🧠 **Interface Analogy: Power Socket**

* **Interface:** A power socket
* **Devices:** TV, Laptop, Phone charger
* Same socket → different internal behavior

### **In Programming Terms:**

* Interface defines *what must exist*
* Implementation defines *how it works*
* User code depends only on the interface

---

## 🧾 **Key Takeaways**

* C++ interfaces are implemented using abstract classes
* Interfaces define **what**, not **how**
* Support multiple inheritance cleanly
* Essential for decoupled design
* Heavily used in CPP04

