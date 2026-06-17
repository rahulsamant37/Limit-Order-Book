## 1. High-Performance Limit Order Book (LOB) & Matching Engine in C++

* **Project Size:** Compact (~500 - 1,500 lines of code)
* **Estimated Difficulty:** Advanced

---

### Why it is valuable for a Quant Developer
Proprietary trading firms and market makers live and die by execution speed. Understanding the internal mechanics of a limit order book (**price-time priority matching**) is a fundamental requirement for anyone working on execution desks or market connectivity.

### What skills it demonstrates
* **Low-Latency C++ Patterns:** Object pooling to avoid heap allocation overhead (`malloc`/`free` during rapid trades), memory alignment, and cache locality.
* **Optimal Data Structures:** Combining **doubly-linked lists** (to represent orders at a specific price level for $O(1)$ insertions/deletions) with a **hash map** (for $O(1)$ order lookups by ID) to achieve overall **$O(1)$ time complexity** for additions, cancellations, and execution.
* **Modern C++:** Practical application of C++17/C++20 features, smart pointers, templates, and strict profiling.

### Why it stands out on a Resume
Unlike standard CRUD applications, this project allows you to put concrete performance numbers on your resume. 

> **Resume Impact Example:** > *"Designed a C++ matching engine that processes over 5 million orders per second with sub-microsecond latency, profiled and optimized using Valgrind and gprof."*

---

### High-Level Implementation Roadmap

1.  **Define Structures:** Create the core data layers—an `Order` struct, a `Limit` price-level struct (holding a doubly-linked list of orders), and the main `Book` struct.
2.  **Implement LOB Logic:** Build out robust functions for `add_order`, `cancel_order`, and `execute_order`. Ensure bids and asks are strictly sorted using a binary search tree or a flat array map for price levels.
3.  **Engine Matching:** Write the execution matching rules. When a buy market order arrives, match it against the lowest ask price levels sequentially until it is either completely filled or the book runs out of liquidity.
4.  **Benchmark & Profile:** Write a rigorous test harness that generates millions of randomized orders. Profile the application for CPU cache misses, memory bottlenecks, and hot paths using tools like `perf` or `valgrind`.
