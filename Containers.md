# 📦 **STL Containers**

**STL containers** in C++ are **data structures that store collections of objects**. They provide **flexible, efficient, and ready-to-use storage** for different types of data.

---

## 🧩 **Why Use STL Containers?**

* ✅ Avoid implementing common data structures from scratch
* ✅ Use optimized, tested, and reliable structures
* ✅ Work with generic algorithms using iterators
* ✅ Improve code readability and maintainability

---

## 🏗️ **Main Categories of STL Containers**

| Container Type         | Description                                                                      |
| ---------------------- | -------------------------------------------------------------------------------- |
| Sequence Containers    | Store elements in a linear order (vector, deque, list, array, forward_list)      |
| Associative Containers | Store elements in a sorted way for fast retrieval (set, map, multiset, multimap) |
| Unordered Containers   | Store elements in a hash table (unordered_set, unordered_map, etc.)              |
| Container Adapters     | Simplified interfaces over existing containers (stack, queue, priority_queue)    |

---

## 🏗️ **Sequence Containers Example**

```cpp id="stl1"
#include <iostream>
#include <vector>
#include <list>

int main() {
    std::vector<int> vec = {1, 2, 3};
    std::list<int> lst = {4, 5, 6};

    vec.push_back(4);
    lst.push_back(7);

    for (int n : vec) std::cout << n << " ";
    std::cout << std::endl;
    for (int n : lst) std::cout << n << " ";
}
```

* `vector` → dynamic array
* `list` → doubly-linked list
* Both support **iterators and range-based loops**

---

## 🏗️ **Associative Containers Example**

```cpp id="stl2"
#include <iostream>
#include <map>
#include <set>

int main() {
    std::map<std::string, int> ages;
    ages["Alice"] = 25;
    ages["Bob"] = 30;

    std::set<int> numbers = {5, 3, 8, 3};

    for (auto& pair : ages) std::cout << pair.first << ": " << pair.second << std::endl;
    for (int n : numbers) std::cout << n << " ";
}
```

* `map` → key-value pairs, sorted by key
* `set` → unique elements, sorted by value

---

## 🏗️ **Unordered Containers Example**

```cpp id="stl3"
#include <iostream>
#include <unordered_map>
#include <unordered_set>

int main() {
    std::unordered_map<std::string, int> ages = {{"Alice", 25}, {"Bob", 30}};
    std::unordered_set<int> numbers = {5, 3, 8, 3};

    for (auto& pair : ages) std::cout << pair.first << ": " << pair.second << std::endl;
    for (int n : numbers) std::cout << n << " ";
}
```

* Uses **hash tables** for faster access
* Order is **not guaranteed**

---

## 🏗️ **Container Adapters Example**

```cpp id="stl4"
#include <iostream>
#include <stack>
#include <queue>

int main() {
    std::stack<int> s;
    s.push(1);
    s.push(2);
    std::cout << s.top() << std::endl; // 2

    std::queue<int> q;
    q.push(1);
    q.push(2);
    std::cout << q.front() << std::endl; // 1
}
```

* `stack` → LIFO (last in, first out)
* `queue` → FIFO (first in, first out)
* `priority_queue` → always returns the largest element

---

## 🔧 **Rules & Best Practices**

* Choose containers based on **access and insertion patterns**
* Use **iterators** or **range-based for loops** for traversal
* Prefer **`unordered_` containers** for fast access when order doesn’t matter
* Use **adapters** when you only need simplified interfaces

---

## 📋 **Summary Table**

| Container Type | Examples                                 | Notes                                      |
| -------------- | ---------------------------------------- | ------------------------------------------ |
| Sequence       | vector, list, deque, array, forward_list | Linear order                               |
| Associative    | set, map, multiset, multimap             | Sorted, unique keys                        |
| Unordered      | unordered_set, unordered_map             | Hash-based, faster access                  |
| Adapter        | stack, queue, priority_queue             | Simplified interface over other containers |

---

# 🧠 **STL Containers Analogy: Storage Boxes**

* 📦 **Sequence containers:** Like trays where items are lined up
* 📦 **Associative containers:** Like filing cabinets sorted by key
* 📦 **Unordered containers:** Like bins where items can be accessed quickly, order doesn’t matter
* 📦 **Adapters:** Like a stack of trays or a conveyor belt for specialized access

---

## 🧪 **Code Example (Analogy)**

```cpp id="stl5"
#include <vector>
#include <set>
#include <iostream>

std::vector<int> vec = {1,2,3}; // Tray
std::set<int> uniqueNumbers = {3,2,1,2}; // Filing cabinet, sorted

for (int n : vec) std::cout << n << " ";  
for (int n : uniqueNumbers) std::cout << n << " ";
```

* Shows different **ways to store and access data**
* STL containers abstract the underlying details

---

## 🧾 **Summary**

* STL containers provide **ready-to-use data structures**
* Work uniformly with **iterators and algorithms**
* Choose containers based on **performance, order, and usage needs**
* Adapters provide **specialized, simplified interfaces**
