# 🧬 **Inheritance**

**Inheritance** is an object-oriented programming concept that allows one class to **reuse**, **extend**, or **modify** the properties and behaviors of another class.
It helps avoid code duplication and represents **real-world relationships**.

* The class being inherited **from** is called the **Base (Parent) class**
* The class that inherits is called the **Derived (Child) class**

---

## 🧩 **Why Use Inheritance?**

* ✅ Reuse existing code
* ✅ Improve readability and maintainability
* ✅ Represent real-world *“is-a”* relationships
* ✅ Support extensibility

---

## 🏗️ **Basic Syntax (C++)**

```cpp
class Parent {
public:
    void show() {
        std::cout << "I am the parent class" << std::endl;
    }
};

class Child : public Parent {
public:
    void display() {
        std::cout << "I am the child class" << std::endl;
    }
};
```

Here:

* `Child` **inherits** from `Parent`
* `Child` can access public members of `Parent`

---

## 🧪 **Example: Vehicle and Car**

```cpp
class Vehicle {
public:
    int speed;

    void move() {
        std::cout << "Vehicle is moving" << std::endl;
    }
};

class Car : public Vehicle {
public:
    void honk() {
        std::cout << "Car is honking" << std::endl;
    }
};
```

```cpp
Car myCar;
myCar.speed = 100;   // Inherited variable
myCar.move();        // Inherited method
myCar.honk();        // Child's own method
```

Here:

* `Car` **inherits** `speed` and `move()` from `Vehicle`
* `Car` also has its own method `honk()`

---

## 👪 **Types of Inheritance (Common in C++)**

| Type         | Description                               |
| ------------ | ----------------------------------------- |
| Single       | One child inherits one parent             |
| Multilevel   | Child inherits from another derived class |
| Hierarchical | Multiple children inherit from one parent |
| Multiple     | One child inherits multiple parents       |

---

## 📋 **Summary Table**

| Term         | Meaning                           | Example         |
| ------------ | --------------------------------- | --------------- |
| Parent Class | Class being inherited from        | `Vehicle`       |
| Child Class  | Class that inherits               | `Car`           |
| Inheritance  | Reusing & extending another class | `Car : Vehicle` |

---

# 🧠 **Inheritance Analogy: Parent and Child**

* **Parent Class:**
  Think of a **parent** who has certain traits—like eye color, last name, or habits.

* **Child Class:**
  A **child** naturally inherits some traits from the parent but can also have **unique traits** of their own.

### **In Programming Terms:**

* The **child class** automatically gets access to the parent’s public features
* The child can **add new features** or **override existing ones**

---

## 📍 **Example Mapping**

| Analogy          | Programming                 |
| ---------------- | --------------------------- |
| Parent           | Base Class                  |
| Child            | Derived Class               |
| Inherited traits | Inherited methods/variables |

---

## 🧪 **Code Example (Relating to Analogy):**

```cpp
class Parent {
public:
    std::string lastName = "Smith";

    void profession() {
        std::cout << "Parent is a doctor" << std::endl;
    }
};

class Child : public Parent {
public:
    void hobby() {
        std::cout << "Child likes painting" << std::endl;
    }
};

Child child;
child.profession();   // Inherited
child.hobby();        // Own behavior
std::cout << child.lastName; // Inherited property
```

---

## 🧾 **Summary**

* **Inheritance** allows one class to reuse another class’s code
* The **child class** gets properties and methods from the **parent class**
* It models real-world **“is-a”** relationships
* Improves code reusability and organization
