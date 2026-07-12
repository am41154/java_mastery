## Appendix A – Top 15 String Interview Questions

This appendix is designed as a **last-minute revision sheet**.

If you have 10 minutes before an interview, reviewing these questions should quickly refresh the most important String concepts.

---

### 1. Why is `String` immutable?

**Answer:**

Immutability enables:

- String Pooling
- Thread safety
- Stable hash codes
- Better security
- Safe object sharing

---

### 2. What is the String Pool?

**Answer:**

The String Pool is a JVM-managed cache of unique string literals. Identical literals reuse the same object to reduce memory consumption.

---

### 3. What is the difference between a String literal and `new String()`?

```java
String s1 = "Java";

String s2 = new String("Java");
```

- Literal → Reuses the pooled object.
- `new String()` → Creates a new object on the heap.

---

### 4. Why shouldn't we compare Strings using `==`?

**Answer:**

`==` compares object references.

`equals()` compares character content.

Use `equals()` for business logic.

---

### 5. Why does `==` sometimes return `true`?

**Answer:**

Because both references may point to the same pooled String object.

It is a consequence of String Pooling—not content comparison.

---

### 6. What does `intern()` do?

**Answer:**

Returns the pooled version of a String.

If the value isn't already in the pool, it is added.

---

### 7. When should you use `StringBuilder`?

**Answer:**

Whenever Strings are built incrementally, especially inside loops.

---

### 8. Difference between `StringBuilder` and `StringBuffer`?

| `StringBuilder` | `StringBuffer` |
|-----------------|----------------|
| Faster | Slower |
| Not synchronized | Synchronized |
| Single-threaded | Multi-threaded |

---

### 9. Why is String a good `HashMap` key?

**Answer:**

Because it is immutable.

Its hash code never changes after creation.

---

### 10. Does every String operation modify the original object?

**Answer:**

No.

Almost every operation returns a **new String**.

---

### 11. Why is `split()` sometimes slower than expected?

**Answer:**

Because it uses **regular expressions**.

Regex processing introduces additional overhead compared to simple parsing.

---

### 12. Is String thread-safe?

**Answer:**

Yes.

Since Strings are immutable, they can be safely shared across multiple threads.

---

### 13. Why avoid `new String("Java")`?

**Answer:**

It creates an unnecessary object, increasing memory usage without any practical benefit in most applications.

---

### 14. Why shouldn't we concatenate Strings inside loops?

**Answer:**

Each concatenation creates a new String object, increasing object allocation and garbage collection pressure.

Use `StringBuilder` instead.

---

### 15. What String-related mistakes do you commonly see in production?

Typical examples include:

- Using `==` instead of `equals()`
- Repeated String concatenation in loops
- Manual log message construction
- Unnecessary `new String()`
- Incorrect use of `split()` with regular expressions

---

## One-Minute Revision

✓ Strings are immutable.

✓ Literals are pooled.

✓ `==` compares references.

✓ `equals()` compares content.

✓ `StringBuilder` is preferred for mutable text.

✓ `StringBuffer` adds synchronization.

✓ `split()` uses regular expressions.

✓ Avoid unnecessary String creation.

✓ Use parameterized logging.

✓ Immutable Strings make excellent `HashMap` keys.

---

> **Congratulations!**

You have completed **Chapter 03 – Strings**.

The next chapter explores one of the most frequently discussed topics in Java interviews:

**Chapter 04 – Collections Framework**

We'll move beyond memorizing APIs and focus on:

- Internal data structures
- Time complexities
- Performance characteristics
- Fail-fast iterators
- HashMap internals
- Concurrent collections
- Real-world usage patterns