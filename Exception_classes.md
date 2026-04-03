# 🚨 **Exception Classes**

**Exception classes** in C++ allow you to **handle errors in an organized and type-safe way**. They let you define **custom error types** beyond the built-in exceptions.

---

## 🧩 **Why Use Exception Classes?**

* ✅ Separate error-handling logic from normal code
* ✅ Provide meaningful error messages
* ✅ Enable custom recovery strategies
* ✅ Make debugging easier

---

## 🏗️ **Basic Syntax (Throwing and Catching Exceptions)**

```cpp
#include <iostream>
#include <stdexcept>

int divide(int a, int b) {
    if (b == 0) {
        throw std::runtime_error("Division by zero!");
    }
    return a / b;
}

int main() {
    try {
        int result = divide(10, 0);
        std::cout << result << std::endl;
    } catch (const std::runtime_error& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }
}
```

Here:

* `throw` signals that an error occurred
* `try` block contains code that **might throw** an exception
* `catch` block handles the exception safely
* `std::runtime_error` is a **built-in exception class**

---

## 🏗️ **Defining a Custom Exception Class**

```cpp
#include <iostream>
#include <exception>

class MyException : public std::exception {
public:
    const char* what() const noexcept override {
        return "My custom exception occurred!";
    }
};

int main() {
    try {
        throw MyException();
    } catch (const MyException& e) {
        std::cerr << "Caught exception: " << e.what() << std::endl;
    }
}
```

Here:

* `MyException` inherits from `std::exception`
* Override `what()` to provide a **custom error message**
* `noexcept` ensures `what()` won’t throw another exception

---

## 🔧 **Common Exception Categories**

| Category            | Description                                      |
| ------------------- | ------------------------------------------------ |
| Standard Exceptions | `std::exception`, `std::runtime_error`           |
| Logic Errors        | `std::logic_error`, `std::invalid_argument`      |
| Runtime Errors      | `std::runtime_error`, `std::overflow_error`      |
| Custom Exceptions   | User-defined classes inheriting `std::exception` |

---

## ⚠️ **Rules & Best Practices**

* Always catch exceptions **by reference** (`const &`)
* Prefer **specific exception types** over `catch(...)`
* Provide **clear and informative messages**
* Use custom exceptions for **domain-specific errors**

---

## 📋 **Summary Table**

| Term                   | Meaning                                             |
| ---------------------- | --------------------------------------------------- |
| Exception              | Runtime error signaling abnormal behavior           |
| `throw`                | Signal an exception                                 |
| `try`                  | Code that may throw an exception                    |
| `catch`                | Handles the exception safely                        |
| Custom Exception Class | User-defined error type inheriting `std::exception` |

---

# 🧠 **Exception Classes Analogy: Fire Alarm**

* **Normal code:** Runs without interruptions
* **Throwing an exception:** Triggers a fire alarm when something goes wrong
* **Catching:** Firefighters come to handle the problem safely

### **In Programming Terms:**

* Exceptions separate **error handling** from **main logic**
* Exception classes allow **specific and descriptive errors**
* Helps prevent crashes and undefined behavior

---

## 🧪 **Code Example (Analogy)**

```cpp
class BatteryLow : public std::exception {
public:
    const char* what() const noexcept override {
        return "Battery is too low!";
    }
};

void startRobot() {
    throw BatteryLow();
}

int main() {
    try {
        startRobot();
    } catch (const BatteryLow& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }
}
```

Here:

* Robot “throws” an exception when the battery is low
* The `catch` block handles the situation safely

---

## 🧾 **Summary**

* Exception classes provide **structured error handling**
* Use **built-in or custom classes** for meaningful errors
* Catch exceptions by **reference** for efficiency
* Separates normal logic from error management
