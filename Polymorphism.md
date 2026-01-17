# 🎭 **Polymorphism**

**Polymorphism** allows objects of different derived types to be treated as objects of a common base type, while still invoking **their own specific behavior**.

In C++, polymorphism is achieved through **inheritance + virtual functions**.

---

## 🧩 **Why Use Polymorphism?**

* ✅ Write flexible and extensible code
* ✅ Decouple code from concrete implementations
* ✅ Enable runtime behavior selection
* ✅ Follow the *Open/Closed Principle*

---

## 🏗️ **Basic Idea (C++)**

```cpp
class Animal {
public:
    virtual void speak() const {
        std::cout << "Animal sound" << std::endl;
    }
};
```

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

Here:

* The function is **chosen at runtime**
* The base pointer calls the **derived implementation**

---

## 🔑 **Key Requirements for Polymorphism**

| Requirement            | Explanation             |
| ---------------------- | ----------------------- |
| Inheritance            | Shared base class       |
| `virtual` functions    | Enable dynamic dispatch |
| Base pointer/reference | Access derived objects  |

---

## ❌ **Without Polymorphism (Static Binding)**

```cpp
class Animal {
public:
    void speak() const {
        std::cout << "Animal sound" << std::endl;
    }
};

Animal* a = new Dog();
a->speak(); // ❌ Animal sound
```

Why?

* No `virtual`
* Function call resolved at **compile time**

---

## 🧪 **Example: Polymorphic Array**

```cpp
Animal* animals[2];
animals[0] = new Dog();
animals[1] = new Cat();

for (int i = 0; i < 2; i++)
    animals[i]->speak();
```

Each object responds **according to its real type**.

---

## 🧬 **Virtual Destructors**

Polymorphic base classes **must** have virtual destructors.

---

### ❌ **Wrong Example**

```cpp
Animal* a = new Dog();
delete a; // ❌ Dog destructor not called
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

## 🧠 **Polymorphism vs Method Overriding**

| Concept      | Meaning                                 |
| ------------ | --------------------------------------- |
| Overriding   | Redefining a virtual base method        |
| Polymorphism | Calling correct method via base pointer |

---

## 🧪 **Using `override` (Best Practice)**

```cpp
class Dog : public Animal {
public:
    void speak() const override;
};
```

Benefits:

* Compiler checks correctness
* Prevents signature mismatches
* Improves readability

---

## ⚠️ **Common Polymorphism Pitfalls**

* Forgetting `virtual` in base class
* Missing virtual destructor
* Object slicing
* Calling virtual functions in constructors
* Signature mismatch (`const`, references, etc.)

---

## 📋 **Summary Table**

| Term             | Description                   |
| ---------------- | ----------------------------- |
| Polymorphism     | One interface, many behaviors |
| Virtual function | Enables runtime dispatch      |
| Dynamic binding  | Function chosen at runtime    |
| Base pointer     | Access derived behavior       |

---

# 🧠 **Polymorphism Analogy: Remote Control**

* **Base class:** Universal remote
* **Derived classes:** TV, Radio, Console
* Same button → different behavior

Without polymorphism:
👉 Every device reacts the same
With polymorphism:
👉 Each device reacts correctly

---

## 🧾 **Key Takeaways**

* Polymorphism enables runtime behavior selection
* Requires inheritance and virtual functions
* Always use virtual destructors
* Prefer `override` keyword
* Core concept of object-oriented C++

