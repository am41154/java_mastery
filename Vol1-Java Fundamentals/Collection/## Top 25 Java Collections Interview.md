# Top 25 Java Collections Interview Questions

> **Rapid Revision for Senior Java Interviews**

---

## 1. What is the difference between Collection and Collections?

**Answer**

- `Collection` is the root interface of the Java Collections Framework.
- `Collections` is a utility class containing static helper methods such as sorting, searching, synchronization, and creating immutable collections.

---

## 2. What is the difference between List, Set, and Map?

| Collection | Stores | Duplicate Keys/Elements | Ordering |
|------------|--------|-------------------------|----------|
| List | Elements | ✓ Allowed | Usually insertion order |
| Set | Elements | ✗ Not allowed | Depends on implementation |
| Map | Key-Value Pairs | Keys ✗, Values ✓ | Depends on implementation |

---

## 3. Why is ArrayList faster than LinkedList for random access?

Because `ArrayList` stores elements in a contiguous array, allowing direct index-based access in O(1). `LinkedList` must traverse nodes sequentially, resulting in O(n) access.

---

## 4. When would you choose LinkedList?

- Frequent insertions/removals at the beginning or end.
- Queue or deque implementations.
- Rare random access.

---

## 5. How does HashMap work internally?

`HashMap` computes the key's `hashCode()`, determines the target bucket, and then uses `equals()` to locate the exact key within that bucket. Java 8+ treeifies heavily populated buckets to improve worst-case lookup performance.

---

## 6. Why must `equals()` and `hashCode()` be overridden together?

Equal objects must produce equal hash codes. Otherwise, logically identical objects may be stored in different buckets, causing lookups in hash-based collections to fail.

---

## 7. What is a hash collision?

A collision occurs when two different keys produce the same hash code and are placed in the same bucket. `HashMap` resolves collisions using bucket structures and, in Java 8+, treeifies heavily populated buckets.

---

## 8. What is the default capacity and load factor of HashMap?

- Default Capacity: **16**
- Default Load Factor: **0.75**

When the threshold is exceeded, the map resizes and rehashes its entries.

---

## 9. What is rehashing?

Rehashing is the process of allocating a larger bucket array and redistributing all existing entries after a resize because bucket positions depend on the table size.

---

## 10. Can HashMap have `null` keys?

Yes.

- One `null` key is allowed.
- Multiple `null` values are allowed.

`ConcurrentHashMap` allows neither.

---

## 11. Why are immutable objects good HashMap keys?

Because their `equals()` and `hashCode()` values remain stable after insertion, ensuring reliable lookups.

---

## 12. How is HashSet implemented?

`HashSet` is internally backed by a `HashMap`. Elements are stored as keys, while a shared dummy object is used as the value.

---

## 13. What is the difference between HashMap and TreeMap?

| Feature | HashMap | TreeMap |
|---------|---------|---------|
| Ordering | None | Sorted by key |
| Internal Structure | Hash Table | Red-Black Tree |
| Average Lookup | O(1) | O(log n) |

---

## 14. What is the difference between HashSet and TreeSet?

`HashSet` provides fast uniqueness checks without ordering.

`TreeSet` maintains unique elements in sorted order using a Red-Black Tree.

---

## 15. What is the difference between Queue and Deque?

- **Queue** follows FIFO (First In, First Out).
- **Deque** supports insertion and removal at both ends, enabling both FIFO and LIFO behavior.

---

## 16. Why is ArrayDeque preferred over Stack?

`Stack` is a legacy synchronized class extending `Vector`.

`ArrayDeque` is faster, more memory-efficient, and supports both stack and queue operations.

---

## 17. What is a PriorityQueue?

A heap-based queue that removes elements according to priority rather than insertion order. By default, it behaves as a min-heap.

---

## 18. What is ConcurrentHashMap?

A thread-safe implementation of `Map` designed for high concurrency using fine-grained synchronization and lock-free techniques where possible.

---

## 19. Why doesn't ConcurrentHashMap allow `null`?

Because a `null` return value would be ambiguous—it would be impossible to distinguish between a missing key and a key explicitly mapped to `null`.

---

## 20. What is CopyOnWriteArrayList?

A thread-safe list that creates a new internal array whenever it is modified. It is best suited for read-heavy workloads.

---

## 21. What is ConcurrentModificationException?

A runtime exception thrown by fail-fast iterators when a collection is structurally modified outside the iterator during iteration.

---

## 22. What is the difference between fail-fast and fail-safe iterators?

| Fail-Fast | Fail-Safe / Weakly Consistent |
|-----------|-------------------------------|
| Detects structural modification | Continues iteration |
| Throws `ConcurrentModificationException` | Does not throw it |
| Iterates over live collection | Uses a snapshot or weakly consistent view |

---

## 23. How do you safely remove elements while iterating?

Use:

```java
Iterator.remove();
```

or, where appropriate,

```java
collection.removeIf(...);
```

Avoid modifying the collection directly inside a for-each loop.

---

## 24. Which collection would you use for a cache?

- Single-threaded: `HashMap`
- Multi-threaded: `ConcurrentHashMap`
- Large-scale production: Consider an external cache such as Redis when data must be shared across application instances.

---

## 25. Which collection should I choose?

A senior engineer answers this by evaluating:

- Read vs write frequency
- Ordering requirements
- Duplicate handling
- Thread safety
- Memory usage
- Data size

The collection should be chosen based on the application's access patterns—not personal preference.

---

# Final Interview Tips

Before any Java interview, make sure you can confidently explain:

✓ Why `equals()` and `hashCode()` work together.

✓ How `HashMap` stores and retrieves data.

✓ Why collisions occur and how they are handled.

✓ The trade-offs between `ArrayList` and `LinkedList`.

✓ When to choose `HashMap` over `TreeMap`.

✓ Why `ConcurrentHashMap` scales better than a synchronized `HashMap`.

✓ The difference between fail-fast and fail-safe iteration.

✓ How to select the most appropriate collection for a real-world problem.

If you can explain these concepts with production examples—not just definitions—you'll be well prepared for most senior Java backend interviews.