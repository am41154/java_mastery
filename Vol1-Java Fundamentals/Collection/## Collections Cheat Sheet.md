# Collections Cheat Sheet (Quick Revision)

> **5-Minute Revision Before an Interview**

---

# Collection Selection Matrix

| Requirement | Recommended Collection |
|-------------|------------------------|
| Ordered List | ArrayList |
| Frequent Insert/Delete at Beginning | LinkedList |
| Fast Random Access | ArrayList |
| Unique Elements | HashSet |
| Sorted Unique Elements | TreeSet |
| Fast Key-Value Lookup | HashMap |
| Sorted Key-Value Pairs | TreeMap |
| Thread-Safe Map | ConcurrentHashMap |
| Read-Heavy List | CopyOnWriteArrayList |
| FIFO Processing | Queue / LinkedBlockingQueue |
| Double-Ended Queue | ArrayDeque |
| Priority Processing | PriorityQueue |

---

# Time Complexity

| Collection | Add | Search | Remove |
|------------|-----|--------|--------|
| ArrayList | O(1)* | O(n) | O(n) |
| LinkedList | O(1) | O(n) | O(n) |
| HashSet | O(1) | O(1) | O(1) |
| TreeSet | O(log n) | O(log n) | O(log n) |
| HashMap | O(1) | O(1) | O(1) |
| TreeMap | O(log n) | O(log n) | O(log n) |

> *Appending to an `ArrayList` is amortized O(1); inserting at arbitrary positions is O(n).*

---

# Ordering

| Collection | Maintains Order? |
|------------|------------------|
| ArrayList | ✓ Insertion Order |
| LinkedList | ✓ Insertion Order |
| HashSet | ✗ No |
| LinkedHashSet | ✓ Insertion Order |
| TreeSet | ✓ Sorted |
| HashMap | ✗ No |
| LinkedHashMap | ✓ Insertion Order |
| TreeMap | ✓ Sorted by Key |

---

# Duplicates

| Collection | Duplicates |
|------------|------------|
| List | ✓ Allowed |
| Set | ✗ Not Allowed |
| Map Keys | ✗ Not Allowed |
| Map Values | ✓ Allowed |

---

# Null Support

| Collection | Null Allowed |
|------------|--------------|
| ArrayList | ✓ |
| LinkedList | ✓ |
| HashSet | ✓ One `null` |
| HashMap | ✓ One `null` key, many `null` values |
| TreeMap | ✗ `null` keys (natural ordering) |
| ConcurrentHashMap | ✗ No `null` keys or values |

---

# Internal Data Structures

| Collection | Internal Structure |
|------------|--------------------|
| ArrayList | Dynamic Array |
| LinkedList | Doubly Linked List |
| HashMap | Hash Table |
| HashSet | HashMap |
| TreeMap | Red-Black Tree |
| TreeSet | Red-Black Tree |
| PriorityQueue | Binary Heap |
| ArrayDeque | Circular Resizable Array |
| ConcurrentHashMap | Concurrent Hash Table |

---

# When to Use What?

### ArrayList

- Frequent reads
- Index-based access
- Small to medium insertions

---

### LinkedList

- Frequent insertions/removals at ends
- Queue-like operations
- Rare random access

---

### HashMap

- Fast key-value lookup
- Caching
- Configuration storage
- Lookup tables

---

### HashSet

- Duplicate elimination
- Membership testing
- Fast existence checks

---

### TreeMap

- Sorted reports
- Leaderboards
- Range queries

---

### PriorityQueue

- Scheduling
- Job prioritization
- Dijkstra's Algorithm

---

### ConcurrentHashMap

- Shared caches
- Multi-threaded applications
- High-concurrency systems

---

# Golden Rules

✓ Prefer interfaces over implementations.

```java
List<User> users = new ArrayList<>();
```

Not

```java
ArrayList<User> users = new ArrayList<>();
```

---

✓ Override both `equals()` and `hashCode()`.

---

✓ Prefer immutable keys in `HashMap`.

---

✓ Choose collections based on access patterns.

---

✓ Use concurrent collections instead of manual synchronization where appropriate.

---

# Interview One-Liners

**HashMap**

> Fast key-value lookup using hashing.

---

**HashSet**

> Internally backed by a HashMap.

---

**TreeMap**

> Sorted map implemented using a Red-Black Tree.

---

**ArrayList**

> Dynamic array with excellent random access.

---

**LinkedList**

> Doubly linked list optimized for insertions/removals at the ends.

---

**ConcurrentHashMap**

> Thread-safe map with high concurrency and fine-grained synchronization.

---

**PriorityQueue**

> Heap-based queue that removes elements by priority rather than insertion order.

---

**CopyOnWriteArrayList**

> Creates a new internal array on each write; ideal for read-heavy workloads.

---

# Senior Engineering Advice

Don't choose a collection because you remember its complexity.

Choose it because it best matches:

- Data access patterns
- Ordering requirements
- Concurrency needs
- Memory considerations
- Maintainability

The right collection often makes the simplest solution the most efficient one.