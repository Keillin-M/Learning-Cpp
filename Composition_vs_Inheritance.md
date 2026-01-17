# 🧱 **Composition vs Inheritance**

**Composition** and **inheritance** are two ways to build relationships between classes.
Choosing the right one is critical for **clean design, flexibility, and maintainability**.

> Rule of thumb:
> **Favor composition over inheritance**

---

## 🧩 **Key Difference**

| Concept     | Meaning                  |
| ----------- | ------------------------ |
| Inheritance | **“Is-a”** relationship  |
| Composition | **“Has-a”** relationship |

---

## 🧬 **Inheritance**

Inheritance allows a class to **reuse and extend** another class.

---

### 🏗️ **Inheritance Example**

```cpp
class Animal {
public:
    void breathe() const {
        std::cout << "Breathing..." << std::endl;
    }
};

class Dog : public Animal {
};
```

```cpp
Dog d;
d.breathe(); // Inherited behavior
```

---

### ✅ **When Inheritance Is Appropriate**

* Clear **is-a** relationship
* Base class is designed for inheritance
* Polymorphism is required
* Behavior should be overridden

---

### ⚠️ **Inheritance Drawbacks**

* Tight coupling
* Fragile base class problem
* Harder to change or refactor
* Can introduce hidden dependencies

---

## 🧩 **Composition**

Composition means a class **contains** another class as a member and **delegates behavior** to it.

---

### 🏗️ **Composition Example**

```cpp
class Engine {
public:
    void start() const {
        std::cout << "Engine started" << std::endl;
    }
};

class Car {
private:
    Engine engine;

public:
    void drive() const {
        engine.start();
        std::cout << "Car is driving" << std::endl;
    }
};
```

---

### ✅ **When Composition Is Better**

* **Has-a** relationship
* Behavior can change dynamically
* Avoid inheritance hierarchy complexity
* Favor flexibility over reuse

---

## 🔁 **Replacing Inheritance with Composition**

### ❌ **Wrong Design**

```cpp
class Engine {};

class Car : public Engine {}; // ❌ Car is NOT an Engine
```

---

### ✅ **Correct Design**

```cpp
class Car {
private:
    Engine engine;
};
```

---

## 🧠 **Polymorphism with Composition**

Composition still supports polymorphism via **interfaces**.

```cpp
class IWeapon {
public:
    virtual ~IWeapon() {}
    virtual void use() const = 0;
};

class Sword : public IWeapon {
public:
    void use() const override;
};

class Character {
private:
    IWeapon* weapon;

public:
    void attack() const {
        if (weapon)
            weapon->use();
    }
};
```

---

## ⚖️ **Comparison Table**

| Aspect         | Inheritance | Composition |
| -------------- | ----------- | ----------- |
| Relationship   | Is-a        | Has-a       |
| Coupling       | Tight       | Loose       |
| Flexibility    | Low         | High        |
| Runtime change | ❌ No        | ✅ Yes       |
| Code reuse     | Implicit    | Explicit    |

---

# 🧠 **Analogy: Robot**

* **Inheritance:** Robot *is a* Machine
* **Composition:** Robot *has a* Battery, Sensors, CPU

Robots can change parts — they don’t change what they *are*.

---

## 🧾 **Key Takeaways**

* Use inheritance only for true **is-a** relationships
* Prefer composition for flexibility
* Composition avoids fragile hierarchies
* Interfaces + composition is a powerful pattern
* Core principle of good C++ design
