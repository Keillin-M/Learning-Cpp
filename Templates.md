# ➕ **Templates**

**Templates** allow you to write **generic and reusable code** in C++. They enable functions or classes to operate with **any data type** without rewriting code for each type.

---

## 🧩 **Why Use Templates?**

* ✅ Avoid code duplication
* ✅ Increase code flexibility and reusability
* ✅ Write type-independent algorithms
* ✅ Work with multiple data types while maintaining type safety

---

## 🏗️ **Basic Syntax (Function Template)**

```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    int x = add(5, 3);      // Works with int
    double y = add(2.5, 1.5); // Works with double
}
```

Here:

* `template <typename T>` tells the compiler to create a generic function
* `T` is a **placeholder type**
* The compiler generates the correct version based on the argument type

---

## 🏗️ **Basic Syntax (Class Template)**

```cpp
template <typename T>
class Box {
private:
    T content;

public:
    Box(T c) : content(c) {}
    T getContent() const { return content; }
};

int main() {
    Box<int> intBox(123);
    Box<std::string> strBox("Hello");
}
```

Here:

* `Box<T>` can store **any type**
* `T` is specified when instantiating the class

---

## 🧪 **Example: Generic Swap Function**

```cpp
template <typename T>
void swapValues(T& a, T& b) {
    T temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 5, y = 10;
    swapValues(x, y); // Works with int

    double a = 1.2, b = 3.4;
    swapValues(a, b); // Works with double
}
```

---

## 🔧 **Common Template Types**

| Type               | Description                             |
| ------------------ | --------------------------------------- |
| Function Template  | Generic functions                       |
| Class Template     | Generic classes                         |
| Template Parameter | `typename` or `class` as placeholders   |
| Non-type Template  | Allows constants as template parameters |

---

## ⚠️ **Rules & Best Practices**

* Templates are **compile-time constructs**
* Prefer **typename** over class for clarity (though both work)
* Keep **template code in headers** (C++ linker rules)
* Avoid overly complex templates unless necessary

---

## 📋 **Summary Table**

| Term               | Meaning                                 |
| ------------------ | --------------------------------------- |
| Template           | Generic blueprint for function or class |
| `typename T`       | Placeholder type                        |
| Function Template  | Generic function definition             |
| Class Template     | Generic class definition                |
| Non-type Parameter | Constant value as template argument     |

---

# 🧠 **Templates Analogy: Cookie Cutter**

* **Normal function/class:** Makes one cookie type
* **Template:** A cookie cutter that works for **any dough**

### **In Programming Terms:**

* Templates generate code automatically for any type
* Functions and classes become **type-independent**
* Reusable and maintainable

---

## 🧪 **Code Example (Analogy)**

```cpp
template <typename T>
T multiply(T a, T b) {
    return a * b;
}

int main() {
    int resultInt = multiply(2, 3);       // 6
    double resultDouble = multiply(2.5, 4.0); // 10.0
}
```

---

## 🧾 **Summary**

* Templates allow writing **generic, reusable code**
* Functions and classes can work with **any type**
* Compiler generates type-specific implementations automatically
* Essential for **type-safe and flexible C++ code**
