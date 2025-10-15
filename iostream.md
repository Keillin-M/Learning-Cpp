# 🔧 Understanding **iostream** in C++

In C++, **`iostream`** is a standard library header (`#include <iostream>`) that provides input and output (I/O) functionality using streams. It is the foundation for reading from input devices (like the keyboard) and writing to output devices (like the screen).

## 🔑 **Key Components**

- **`cin`**: Standard input stream. Used for reading input (usually from the keyboard).
- **`cout`**: Standard output stream. Used for writing output (usually to the console/screen).

---

### **cin**  
- Pronounced "see-in".
- Used to get input from the user.
- Example usage:
    ```cpp
    int age;
    std::cin >> age;
    ```
    This reads a value from the user and stores it in the variable `age`.

### **cout**  
- Pronounced "see-out".
- Used to display output to the user.
- Example usage:
    ```cpp
    std::cout << "Hello, World!" << std::endl;
    ```
    This prints "Hello, World!" to the screen.

---

## ⚙️ **How It Works**

- **Streams**: Think of `cin` and `cout` as flows of data.  
    - `cin` flows data **into** your program from the user.
    - `cout` flows data **out** of your program to the user.

- **Operators**:
    - `<<` is the **insertion operator** for `cout` (sends data to output).
    - `>>` is the **extraction operator** for `cin` (gets data from input).

---

## 🧪 **Example Program**

```cpp
#include <iostream>

int main() {
    int number;
    std::cout << "Enter a number: ";  // Output to user
    std::cin >> number;               // Input from user
    std::cout << "You entered: " << number << std::endl;
    return 0;
}
```

---

### 🎯 **Summary**

- **`iostream`** is used for input and output in C++.
- **`cin`** reads data from the user.
- **`cout`** writes data to the user.
- Operators `>>` and `<<` are used to handle data transfer.
