# 🛡️ **Understanding `const` in C++**

In C++, the **`const`** keyword is used to indicate that something cannot be changed (it is "constant").  
It helps you write safer code by preventing accidental modifications to variables, function parameters, objects, and member functions.

---

## 🔍 **Where Can You Use `const`?**

1. **Constant Variables**
    ```cpp
    const int maxSpeed = 100;
    ```
    *This variable cannot be changed after its initialization.*

2. **Constant Function Parameters**
    ```cpp
    void printValue(const int value) {
        std::cout << value << std::endl;
    }
    ```
    *The function cannot modify `value`.*

3. **Constant Member Functions**
    ```cpp
    class Car {
    public:
        int getSpeed() const {    // note the const after ()
            return speed;
        }
    private:
        int speed;
    };
    ```
    *This function promises not to modify the object’s data members.*

4. **Constant Pointers**
    ```cpp
    int value = 5;
    const int* p = &value;  // pointer to const int (cannot change the value pointed to)
    int* const q = &value;  // const pointer to int (cannot change the pointer itself)
    ```
    *You can make either the pointer or the value it points to constant.*

5. **Constant Objects**
    ```cpp
    const Car myCar;
    ```
    *You cannot call non-const member functions or modify `myCar`.*

---

## 🧪 **Example**

```cpp
class Box {
public:
    int getVolume() const {           // const member function
        return length * width * height;
    }
    void setLength(int l) {
        length = l;
    }
private:
    int length, width, height;
};

void showBox(const Box& box) {        // const reference parameter
    std::cout << box.getVolume() << std::endl;
}
```
- `getVolume()` cannot modify any member variables.
- `showBox` cannot modify the box passed in.

---

## 📌 **Summary**

- **`const`** helps keep things unchanged and protects data from accidental modification.
- You can use `const` with variables, parameters, pointers, member functions, and objects.
- It improves code safety and clarity.
