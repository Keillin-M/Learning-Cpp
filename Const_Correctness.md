
# 🔒 **Const Correctness**

**Const correctness** ensures that objects and variables are **not modified unintentionally**.
It is a core principle of safe and clean C++ design.

---

## 🧩 **Why Use Const Correctness?**

* ✅ Prevent accidental changes
* ✅ Improve code clarity
* ✅ Allow usage with const objects
* ✅ Required for operator overloading

---

## 🏗️ **Basic Syntax (C++)**

```cpp
class Sample {
private:
    int value;

public:
    int getValue() const {
        return value;
    }
};
```

Here:

* `const` means this function **cannot modify** the object
* Calling it on a `const` object is allowed

---

## 🧪 **Const Objects Example**

```cpp
const Sample s;
s.getValue();   // OK
// s.setValue(5); // ❌ Not allowed
```

---

## 🔧 **Const in Function Parameters**

```cpp
void print(const Sample& s);
```

* Prevents copying
* Guarantees `s` won’t be modified

---

## 🔁 **Const with Operator Overloading**

```cpp
bool operator<(const Fixed& other) const;
```

Meaning:

* `other` will not be modified
* The current object will not be modified

---

## 📋 **Summary Table**

| Usage             | Purpose                          |
| ----------------- | -------------------------------- |
| `const variable`  | Prevent modification             |
| `const function`  | Protect object state             |
| `const reference` | Avoid copies + safety            |
| `const return`    | Prevent misuse of returned value |

---

# 🧠 **Const Correctness Analogy: Read-Only Mode**

* **Const object:** A document opened in *read-only mode*
* You can **read** it
* You cannot **edit** it

### **In Programming Terms:**

* `const` enforces rules at compile time
* Prevents unintended side effects
* Makes APIs safer and clearer

---

## 🧪 **Code Example (Analogy)**

```cpp
void readOnly(const Sample& doc) {
    std::cout << doc.getValue() << std::endl;
}
```

---

## 🧾 **Summary**

* Const correctness prevents bugs
* Enforced at compile time
* Essential for clean APIs
* Mandatory for idiomatic C++
