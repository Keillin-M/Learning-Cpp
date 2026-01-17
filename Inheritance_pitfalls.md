# ⚠️ **Inheritance Pitfalls**

Inheritance is a powerful object-oriented feature, but **misusing it can lead to bugs, confusing code, and undefined behavior**.
Understanding common pitfalls helps write **safe, maintainable, and idiomatic C++**.

---

## 🧩 **Why Learn Inheritance Pitfalls?**

* ✅ Avoid subtle runtime bugs
* ✅ Prevent memory leaks
* ✅ Write correct polymorphic code
* ✅ Understand how C++ differs from other OOP languages

---

## 🚫 **Pitfall #1: Missing Virtual Destructor**

Deleting a derived object through a base class pointer **without a virtual destructor** causes undefined behavior.

---

### ❌ **Wrong Example**

```cpp
class Animal {
public:
    ~Animal() {}
};

class Dog : public Animal {
public:
    ~Dog() {
        std::cout << "Dog destroyed" << std::endl;
    }
};

Animal* a = new Dog();
delete a; // ❌ Dog destructor NOT called
```

---

### ✅ **Correct Example**

```cpp
class Animal {
public:
    virtual ~Animal() {}
};
```

---

### 🔍 **Why This Happens**

* Destructors are not virtual by default
* Base pointer deletion only calls base destructor
* Leads to resource leaks

---

## 🚫 **Pitfall #2: Forgetting `virtual` in Base Methods**

Without `virtual`, method calls are resolved at **compile time**, not runtime.

---

### ❌ **Wrong Example**

```cpp
class Animal {
public:
    void speak() const {
        std::cout << "Animal sound" << std::endl;
    }
};

class Dog : public Animal {
public:
    void speak() const {
        std::cout << "Woof!" << std::endl;
    }
};

Animal* a = new Dog();
a->speak(); // ❌ Outputs: Animal sound
```

---

### ✅ **Correct Example**

```cpp
class Animal {
public:
    virtual void speak() const {
        std::cout << "Animal sound" << std::endl;
    }
};
```

---

## 🚫 **Pitfall #3: Object Slicing**

Assigning a derived object to a base object **slices off** the derived part.

---

### ❌ **Wrong Example**

```cpp
Dog d;
Animal a = d; // ❌ Dog-specific data lost
```

---

### ✅ **Correct Usage**

```cpp
Animal* a = new Dog();   // Polymorphism preserved
Animal& r = d;
```

---

### 🔍 **Why It Happens**

* Objects are copied by value
* Base object only stores base part
* Polymorphism requires pointers or references

---

## 🚫 **Pitfall #4: Public Inheritance for “Has-A” Relationships**

Inheritance should model **“is-a”**, not **“has-a”**.

---

### ❌ **Wrong Example**

```cpp
class Engine {};

class Car : public Engine {}; // ❌ Car is NOT an Engine
```

---

### ✅ **Correct Design (Composition)**

```cpp
class Car {
private:
    Engine engine;
};
```

---

## 🚫 **Pitfall #5: Overriding Without `const` or Exact Signature**

A small mismatch prevents overriding.

---

### ❌ **Wrong Example**

```cpp
class Animal {
public:
    virtual void speak() const;
};

class Dog : public Animal {
public:
    void speak(); // ❌ Does NOT override
};
```

---

### ✅ **Correct Example**

```cpp
class Dog : public Animal {
public:
    void speak() const override;
};
```

---

### 💡 **Why Use `override`?**

* Compiler checks correctness
* Prevents silent bugs
* Improves readability

---

## 🚫 **Pitfall #6: Calling Virtual Functions in Constructors**

Virtual dispatch **does not work** during construction/destruction.

---

### ❌ **Wrong Example**

```cpp
class Animal {
public:
    Animal() {
        speak(); // ❌ Calls Animal::speak()
    }

    virtual void speak() const;
};
```

---

### 🔍 **Why This Is Dangerous**

* Derived part not constructed yet
* Leads to unexpected behavior
* Common beginner mistake

---

## 📋 **Summary Table**

| Pitfall                      | Consequence             |
| ---------------------------- | ----------------------- |
| Non-virtual destructor       | Memory leaks            |
| Missing `virtual`            | No polymorphism         |
| Object slicing               | Lost derived behavior   |
| Wrong relationship           | Bad design              |
| Signature mismatch           | Function not overridden |
| Virtual calls in constructor | Unexpected behavior     |

---

# 🧠 **Inheritance Analogy: Remote Control**

* **Base class pointer:** A universal remote
* **Derived object:** A specific device
* If functions aren’t virtual → remote always acts generic
* Virtual functions enable **correct device behavior**

---

## 🧾 **Key Takeaways**

* Always use **virtual destructors** for polymorphic bases
* Use `virtual` and `override` consistently
* Avoid object slicing
* Prefer **composition over inheritance**
* Inheritance is powerful — but dangerous if misused

