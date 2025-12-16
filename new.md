# 🔧 Understanding `new` in C++

In C++, the keyword **`new`** is used to **create objects dynamically** — meaning the object is allocated on the **heap**, not on the stack.

---

# 🧠 What does `new` actually do?

When you use `new`, C++ performs **two things at once**:

1️⃣ **Allocates memory** on the heap
2️⃣ **Calls the constructor** to initialize the object

This is the key difference from C’s `malloc`.

---

# 📍 Stack vs Heap Reminder

## Stack allocation

* Automatic
* Object is destroyed when scope ends
* Destructor is called automatically

## Heap allocation (`new`)

* Manual
* Object lives until you destroy it
* Destructor is **not** called automatically

---

# 🧪 Conceptual Example

> Creating an object with `new` is like **renting storage space**:

* You get a usable object
* It stays alive after the function ends
* You must return it when you’re done

---

# 🔥 Why `new` can be dangerous

If you use `new`:

* The object will **not be destroyed automatically**
* If you forget to clean it up:

  * Destructor never runs
  * Memory leaks occur

This is exactly why C++ beginners are warned about `new`.

---

# 🧠 `new` vs `malloc` (C mindset)

| C (`malloc`)         | C++ (`new`)                      |
| -------------------- | -------------------------------- |
| Allocates raw memory | Allocates + constructs object    |
| No constructor       | Constructor is called            |
| Must use `free`      | Must use `delete`                |
| No destructor        | Destructor is called by `delete` |

---

# 🔁 The missing half: `delete`

> **Every `new` must have a matching `delete`.**

* `new` → constructor runs
* `delete` → destructor runs + memory is freed

If `delete` is never called:

* Object stays alive forever
* Resources are leaked

---

# ❤️ Why modern C++ avoids raw `new`

Modern C++ prefers:

* Stack objects
* References
* Smart pointers (`std::unique_ptr`, `std::shared_ptr`)

Because they:

* Automatically manage destruction
* Prevent memory leaks
* Follow RAII principles

---

# 🧠 Rule of thumb (very important)

> **If you don’t need dynamic lifetime, don’t use `new`.**

Use `new` only when:

* Object must outlive its scope
* Lifetime cannot be clearly scoped
* Ownership must be transferred

---

# 🎯 Summary

* `new` allocates memory on the **heap**
* Calls the **constructor**
* Returns a pointer to the object
* Requires `delete` to clean up
* Misuse causes memory leaks

---

## 🧠 One-line takeaway

> **`new` creates an object that you must destroy yourself.**
