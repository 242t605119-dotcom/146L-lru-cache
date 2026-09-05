# LeetCode 146 – LRU Cache

## Problem

Design a data structure that follows the **Least Recently Used (LRU)** cache policy.

Implement the following operations:

* `LRUCache(capacity)` – initialize the cache with a given capacity.
* `get(key)` – return the value associated with the key, or `-1` if the key does not exist.
* `put(key, value)` – insert or update a key-value pair.

When the cache reaches its capacity, the **least recently used** item must be removed before adding a new item.

Both `get` and `put` should work in **O(1)** average time.

## Example

**Input:**

```text
LRUCache cache = new LRUCache(2)

cache.put(1, 1)
cache.put(2, 2)
cache.get(1)
cache.put(3, 3)
cache.get(2)
cache.put(4, 4)
cache.get(1)
cache.get(3)
cache.get(4)
```

**Output:**

```text
1
-1
-1
3
4
```

## Explanation

The cache capacity is `2`.

After:

```text
put(1,1)
put(2,2)
```

the cache contains:

```text
1 → 2
```

Accessing key `1` makes it recently used.

When:

```text
put(3,3)
```

is performed, key `2` is the least recently used item, so it is removed.

Later, inserting key `4` removes the least recently used key at that time.

## Approach

An efficient solution uses two data structures together:

1. **Hash Map**
2. **Doubly Linked List**

The hash map provides fast access to a node using its key.

The doubly linked list maintains the order of usage.

A common arrangement is:

```text
Least Recently Used ←→ Most Recently Used
```

Whenever an item is accessed or inserted, it is moved toward the most recently used side.

When the cache becomes full, the node at the least recently used side is removed.

## Algorithm

### `get(key)`

1. Check whether the key exists in the hash map.
2. If it does not exist, return `-1`.
3. Remove the corresponding node from its current position.
4. Move it to the most recently used position.
5. Return its value.

### `put(key, value)`

1. Check whether the key already exists.
2. If it exists, update its value.
3. Move the node to the most recently used position.
4. If the key is new, create a new node.
5. Add the node to the most recently used position.
6. If the cache exceeds its capacity, remove the least recently used node.
7. Update the hash map.

## Why Hash Map + Doubly Linked List?

A hash map alone can provide fast lookup, but it does not efficiently maintain the order of recently used items.

A doubly linked list allows nodes to be inserted and removed quickly.

Together, they allow both `get` and `put` to operate in **O(1)** average time.

## Complexity

* **Time Complexity:** `O(1)` average for both `get` and `put`
* **Space Complexity:** `O(capacity)`

The cache stores at most `capacity` nodes.

## LeetCode Details

* **Problem Number:** 146
* **Problem Name:** LRU Cache
* **Difficulty:** Medium
* **Language:** Python 3
* **File:** `solution.py`

## Topics

* Hash Table
* Linked List
* Design
* Doubly Linked List

## Key Learning

This problem is an important example of combining multiple data structures to achieve efficient performance.

The combination of a **hash map and doubly linked list** is a standard technique for implementing an LRU cache with constant-time operations.

## Repository Structure

```text
leetcode-146-lru-cache/
│
├── solution.py
└── README.md
```

## Author

T.Nandhini
