# ➡️ **Iterators**

**Iterators** in C++ provide a **uniform way to traverse containers** (like arrays, vectors, lists) without exposing their underlying representation. They act like **pointers that can move through a sequence**.

---

## 🧩 **Why Use Iterators?**

* ✅ Access elements of a container sequentially
* ✅ Work with different container types uniformly
* ✅ Support algorithms from the STL
* ✅ Improve code readability and safety

---

## 🏗️ **Iterator Basics**

```cpp id="iter1"
#include <iostream>
#include <vector>

int main() {
    std::vector<int> numbers = {1, 2, 3, 4, 5};

    for (std::vector<int>::iterator it = numbers.begin(); it != numbers.end(); ++it) {
        std::cout << *it << " ";
    }
}
```

Here:

* `begin()` returns an iterator to the first element
* `end()` returns an iterator past the last element
* `*it` dereferences the iterator to access the element
* `++it` moves the iterator forward

---

## 🏗️ **Common Iterator Types**

| Iterator Type          | Description                                    |
| ---------------------- | ---------------------------------------------- |
| Input Iterator         | Read elements sequentially                     |
| Output Iterator        | Write elements sequentially                    |
| Forward Iterator       | Read/write, moves forward                      |
| Bidirectional Iterator | Forward and backward traversal                 |
| Random Access Iterator | Supports arithmetic operations (like `+`, `-`) |

---

## 🏗️ **Using STL Algorithms with Iterators**

```cpp id="iter2"
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> numbers = {5, 2, 8, 1, 4};

    std::sort(numbers.begin(), numbers.end()); // sort using iterators

    for (auto it = numbers.begin(); it != numbers.end(); ++it) {
        std::cout << *it << " ";
    }
}
```

* Iterators allow **generic algorithms** to work with any container type

---

## 🔧 **Rules & Best Practices**

* Use **`auto`** for iterator type deduction to simplify code
* Avoid invalidating iterators (e.g., after container modifications)
* Prefer **range-based for loops** when simple iteration is enough
* Use iterators with **STL algorithms** for cleaner code

---

## 📋 **Summary Table**

| Term            | Meaning                                    |
| --------------- | ------------------------------------------ |
| Iterator        | Object to traverse container elements      |
| `begin()`       | Iterator to the first element              |
| `end()`         | Iterator past the last element             |
| `*it`           | Access element pointed by iterator         |
| `++it` / `--it` | Move forward / backward                    |
| STL Algorithms  | Work with iterators for generic operations |

---

# 🧠 **Iterators Analogy: Bookmark in a Book**

* 📖 **Container:** The book
* 🔖 **Iterator:** A bookmark pointing to a page
* You can move the bookmark forward, backward, or read the current page
* Algorithms are like “reading instructions” applied using the bookmark

### **In Programming Terms:**

* Iterators **abstract access to elements**
* Enable **generic programming** across containers
* Work seamlessly with **STL algorithms**

---

## 🧪 **Code Example (Analogy)**

```cpp id="iter3"
#include <vector>
#include <iostream>

std::vector<std::string> words = {"hello", "world", "iterator"};

for (auto it = words.begin(); it != words.end(); ++it) {
    std::cout << *it << " ";
}
```

* Moves through the container sequentially
* Accesses elements without knowing the underlying structure

---

## 🧾 **Summary**

* Iterators provide **uniform access to container elements**
* Work with **all STL containers** and **algorithms**
* Enable **generic, reusable, and readable code**
