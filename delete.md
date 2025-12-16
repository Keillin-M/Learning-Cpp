# 🔧 Understanding `delete` in C++

The keyword **`delete`** is used to **destroy objects created with `new`**.

---

# 🧠 What does `delete` do?

When you call `delete` on a pointer, C++ performs **two actions**:

1️⃣ Calls the object’s **destructor**
2️⃣ Frees the memory from the **heap**

If you never call `delete`, the destructor **never runs**, and memory is leaked.

---

# ⚠️ Important rules for `delete`

* Only use `delete` on memory created with `new`
* Never delete the same pointer twice
* Never delete stack memory

---

## 🧠 Mental model

> `new` = birth
> `delete` = death

If death never happens, the object stays alive forever.

---

# 🔧 `new[]` vs `delete[]`

When creating **arrays** on the heap, C++ uses a different form.

---

## 📍 `new[]`

* Allocates memory for **multiple objects**
* Calls the constructor for **each element**

---

## 🧹 `delete[]`

* Calls the destructor for **each element**
* Frees the entire block of memory

---

## ⚠️ Critical rule

> **`new[]` must be matched with `delete[]`**
> **`new` must be matched with `delete`**

Mixing them causes **undefined behavior**.

---

# 🔧 Why Smart Pointers Replace `new`

Raw `new` and `delete` are **error-prone**.

Smart pointers are C++ objects that:

* Own heap memory
* Automatically delete it
* Follow RAII

---

# 🧠 Common Smart Pointers

## 🔹 `std::unique_ptr`

* Sole owner of an object
* Cannot be copied
* Automatically deletes when it goes out of scope

**Use when:** one clear owner exists.

---

## 🔹 `std::shared_ptr`

* Multiple owners
* Object destroyed when last owner goes away

**Use when:** shared ownership is needed.

---

## 🔹 `std::weak_ptr`

* Non-owning reference
* Prevents circular references

**Use when:** observing without owning.

---

# ❤️ Why modern C++ prefers smart pointers

* No manual `delete`
* No memory leaks
* Exception-safe
* Clear ownership semantics

---

# 🧠 How this connects to Stack vs Heap (again)

| Allocation           | Cleanup                             |
| -------------------- | ----------------------------------- |
| Stack                | Automatic (destructor at scope end) |
| Heap + `new`         | Manual (`delete`)                   |
| Heap + smart pointer | Automatic (RAII)                    |

Smart pointers give heap memory **stack-like safety**.

---

# 🎯 Final Summary

* `new` creates objects on the heap
* `delete` destroys them
* `new[]` / `delete[]` manage arrays
* Forgetting `delete` = memory leak
* Smart pointers eliminate manual cleanup

---

## 🧠 One-line takeaway

> **If you must use the heap, use smart pointers.
> If you can avoid the heap, avoid `new`.**
