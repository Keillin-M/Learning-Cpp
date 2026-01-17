# ➕ **Operator Overloading**

**Operator overloading** allows C++ classes to define how standard operators (`+`, `-`, `==`, `<<`, etc.) behave when used with objects.
It makes **user-defined types feel like built-in types**.

---

## 🧩 **Why Use Operator Overloading?**

* ✅ Improve code readability
* ✅ Write expressive and intuitive code
* ✅ Encapsulate behavior inside the class
* ✅ Enable mathematical and logical operations on objects

---

## 🏗️ **Basic Syntax (C++)**

```cpp
class Number {
private:
    int value;

public:
    Number(int v) : value(v) {}

    Number operator+(const Number& other) const {
        return Number(value + other.value);
    }
};
```

```cpp
Number a(5);
Number b(3);
Number c = a + b; // Calls operator+
```

Here:

* `operator+` defines how `+` works for `Number`
* `const` ensures objects are not modified
* A new object is returned

---

## 🧪 **Example: Fixed-Point Addition**

```cpp
class Fixed {
private:
    int _rawBits;

public:
    Fixed operator+(const Fixed& other) const {
        Fixed result;
        result._rawBits = this->_rawBits + other._rawBits;
        return result;
    }
};
```

---

## 🔧 **Commonly Overloaded Operators**

| Category   | Operators              |
| ---------- | ---------------------- |
| Arithmetic | `+  -  *  /`           |
| Comparison | `==  !=  <  >  <=  >=` |
| Increment  | `++  --` (pre & post)  |
| Assignment | `=`                    |
| Stream     | `<<  >>`               |

---

## ⚠️ **Rules & Best Practices**

* Operators should **preserve their original meaning**
* Prefer **const correctness**
* Return by **value** unless modification is required
* `operator<<` should usually be a **non-member function**

---

## 📋 **Summary Table**

| Term              | Meaning                            |
| ----------------- | ---------------------------------- |
| Operator Overload | Custom behavior for an operator    |
| `operator+`       | Defines how `+` works on objects   |
| Member overload   | Operator defined inside the class  |
| Non-member        | Needed for stream operators (`<<`) |

---

# 🧠 **Operator Overloading Analogy: Calculator**

* **Built-in types:** Like a calculator that only works with numbers
* **Operator overloading:** Upgrading the calculator to understand your own types

### **In Programming Terms:**

* Operators become **function calls**
* Objects decide how operations behave
* Code becomes easier to read and maintain

---

## 🧪 **Code Example (Analogy)**

```cpp
Fixed a(2.5f);
Fixed b(1.5f);
Fixed c = a + b; // Reads naturally
```

---

## 🧾 **Summary**

* Operator overloading makes objects behave like built-in types
* Operators are implemented as functions
* Const correctness is essential
* Widely used in idiomatic C++
